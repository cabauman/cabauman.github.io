---
title: "Resolving IL2CPP Build Issues"
categories:
  - Code Journal
tags:
  - unity
  - il2cpp
toc: true
toc_sticky: true
---

It's usually a good idea to test built versions of your application regularly because code will often behave differently than in the editor. Doing this regularly helps to
- easily pinpoint when a bug was introduced
- avoid "surprises" when someone requests a build

This includes early in development; not just when getting close to a release. The importance is magnified when building for IL2CPP because of managed code stripping, especially when reflection is in use. I recently did one of these routine checks for a project I'm currently assigned to at work (early in development). It had been 1-2 weeks since my last check, and let's just say it resulted in enough content for this blog post 😅 There were three main issues that came up.

## Awake vs OnEnable Order

The first was related to editor vs build rather than IL2CPP specifically, because the same issue occurred for Mono. The undefined order of `Awake` vs `OnEnable` _in separate scripts_ resulted in a `NullReferenceException` in the built version of the application, but not in the editor. In this case, Awake was executing before OnEnable in the editor, and vice versa in the build.

```csharp
// GameObjectA
private void Awake()
{
    _a = new A();
}

public void DoSomething()
{
    _a.DoSomething(); // exception, _a is null!
}
```

```csharp
// GameObjectB
private void OnEnable()
{
    gameObjectA.DoSomething();
}
```

The quick fix in this case was wrapping `_a` in a property for lazy initialization instead of in `Awake`.

## Marshal.SizeOf

The next exception to deal with was

> ArgumentException: The t parameter is a generic type.

which was being thrown by a call to `Marshal.SizeOf` in the IL2CPP build, but not in the editor or Mono build. The specific line was in a binary reader class:

```csharp
Marshal.SizeOf<HeaderSegment<TKey>>()
```

Other calls like `Marshal.SizeOf<TKey>()` work fine; it's just not happy when `T` is generic.

I found it mentioned in a [2020 dotnet/runtime GitHub issue](https://github.com/dotnet/runtime/issues/46426) where someone commented it's by design, but of course it doesn't help explain the difference in behavior between Mono and IL2CPP. There was also a comment about using `Unsafe.SizeOf`, instead, so I gave that a try and it worked. Since I didn't feel like adding another DLL at the moment, I just used the `UnsafeUtility` included in the `Unity.Collections.LowLevel.Unsafe` namespace, which is just a wrapper for a lot of the `System.Runtime.CompilerServices.Unsafe` methods, anyway.

A day or two later I did some research on these two `SizeOf` variations, which lead to resolving another related issue. I'll cover that in the next post.
{: .notice--info}

## SQLite Stripping

The final issue only surfaced after I bumped up the [managed stripping level](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) to **Medium** (**Minimal** and **Low** were fine). The goal was to get up to the maximum level, **High**. I got a `NullReferenceException` [on the following line](https://github.com/praeclarum/sqlite-net/blob/e8a24a8b2ecb4fd700c5fe46062239a9b08472fd/src/SQLite.cs#L4233) when trying to do a read.

```csharp
var columnName = Table.FindColumnWithPropertyName (mem.Member.Name).Name;
```

`FindColumnWithPropertyName` was returning null, so accessing the `Name` property resulted in the NRE. So now, I'll walk you through the process I took to get to the root cause. Here's an abbreviated class that resembles the table being queried:

```csharp
public class LineInfo
{
    public string LineName { get; set; }
}
```

### Why is FindColumnWithPropertyName returning null?

```csharp
public Column FindColumnWithPropertyName (string propertyName)
{
    var exact = Columns.FirstOrDefault (c => c.PropertyName == propertyName);
    return exact;
}
```

Answer: [The Columns property](https://github.com/praeclarum/sqlite-net/blob/e8a24a8b2ecb4fd700c5fe46062239a9b08472fd/src/SQLite.cs#L2666) is empty here.

### Why is the Columns property empty?

`Columns` is initialized in the `TableMapping` constructor but I noticed [GetPublicMembers](https://github.com/praeclarum/sqlite-net/blob/e8a24a8b2ecb4fd700c5fe46062239a9b08472fd/src/SQLite.cs#L2566) was returning an empty list.

```csharp
var members = GetPublicMembers(type);
```

### Why is GetPublicMembers returning an empty list?

```csharp
private void GetPublicMembers()
{
    ...
    newMembers.AddRange(
        from p in ti.DeclaredProperties
        where !memberNames.Contains(p.Name) &&
            p.CanRead && p.CanWrite &&
            p.GetMethod != null && p.SetMethod != null &&
            p.GetMethod.IsPublic && p.SetMethod.IsPublic &&
            !p.GetMethod.IsStatic && !p.SetMethod.IsStatic
        select p);
    ...
}
```

Reflection...of course. [This query](https://github.com/praeclarum/sqlite-net/blob/e8a24a8b2ecb4fd700c5fe46062239a9b08472fd/src/SQLite.cs#L2614) gets all public instance properties that have both a getter and setter. But it turns out `p.CanWrite` was returning false and `p.SetMethod` was null, meaning there's no setter.

### Why is the setter missing?

This was a clear indication that it must being getting stripped, so I added a [PreserveAttribute](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) on the class, but it didn't work. So then I tried applying the attribute to each property instead, and that did the trick. I thought applying it to the class meant it preserves all members, but apparently I was wrong. I found a GitHub issue that mentioned this exact stripping side effect: ["IL2CPP Code stripping makes properties unwritable"](https://github.com/jacobdufault/fullserializer/issues/143).

```csharp
public class LineInfo
{
    [UnityEngine.Scripting.Preserve]
    public string LineName { get; set; }
}
```

## Conclusion

In the end, the goal of having a functional IL2CPP build of the application with managed stripping level set to `High` was achieved. Ensuring a successful build in CI is a good start, but actually running that build can save time down the road. This can even be _Play Mode_ tests configured to run on the target platform.