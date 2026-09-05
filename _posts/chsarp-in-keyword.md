---
title: "C# in Keyword Performance Trap"
date: 2026-09-05
tags:
  - c#
---

I recently came across some NativeArray sorting experiments online that utilize the Unity job system and burst compiler. As I was reviewing the code, I noticed a potential performance trap related to the `in` keyword in C#. The input array parameter `a` is passed by readonly reference because there's no intention to modify it within the method.

```csharp
/// <summary>
/// <param name="a">The array to be sorted.</param>
/// <param name="b">The result of sorting.</param>
/// </summary>
internal static void Merge<T1, U1>(in NativeArray<T1> a, NativeArray<T1> b, U1 cmp, int left, int mid, int end)
{
    ...
    for (; k < end && i < mid && j < end; ++k)
    {
        if (cmp.Compare(a[i], a[j]) <= 0)
        {
            b[k] = a[i++];
        }
        else
        {
            b[k] = a[j++];
        }
    }
    ...
}
```

```csharp
using System;
public struct A
{
    public float this[int index]
    {
        get => 1f;
    }
}
public class C
{
    public void M(in A a)
    {
        for (int i = 0; i < 1_000_000; ++i)
        {
            Console.WriteLine(a[0]);
        }
    }
}
```

```csharp
public T this[int index]
{
    [MethodImpl(MethodImplOptions.AggressiveInlining)]
    get
    {
        CheckElementReadAccess(index);
        return UnsafeUtility.ReadArrayElement<T>(m_Buffer, index);
    }
    ...
}

asdf

```csharp
using System;
public struct A
{
    public readonly float this[int index]
    {
        get => 1f;
    }
}
public class C
{
    public void M(in A a)
    {
        for (int i = 0; i < 1_000_000; ++i)
        {
            Console.WriteLine(a[0]);
        }
    }
}
```
