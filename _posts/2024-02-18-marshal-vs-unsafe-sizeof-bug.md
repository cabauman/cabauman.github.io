---
title: "Resolving a Bug Related to 'Marshal.SizeOf<T> vs Unsafe.SizeOf<T>'"
categories:
  - Code Journal
tags:
  - C#
  - unsafe code
  - unmanaged structs
  - sizeof
  - marshal
---

In this post I'm going to share how switching from `Marshal.SizeOf<T>` to `Unsafe.SizeOf<T>` helped me resolve a bug that I had a left a TODO comment for a month or two ago, along with a work-around. It's not that the former is broken, but rather I had made the wrong choice for my particular use case. Thanks to my improved understanding of the differences between these two SizeOf variations, I felt it was time to try to address that TODO comment.

In order to make this as understandable as possible, I'll be using simplified versions of the actual code, and excluding parts that would otherwise distract us from the main focus.
{: .notice--info}

This code is from a Unity project but it doesn't touch any Unity-specific API, so you'll probably see me using `Console.WriteLine` to demonstrate printing.
{: .notice--info}

So without further ado, here's the snippet of interest:

{% highlight csharp linenos %}
var data = new TValue[structCount];
// TODO: Find out why ReadArray is returning wrong values but reading one-by-one is fine.
//accessor.ReadArray(position: 0, array: data, offset: 0, count: data.Length);
var structSize = Marshal.SizeOf<T>();
for (var i = 0; i < structCount; i++)
{
    var byteOffset = i * structSize;
    accessor.Read<TValue>(byteOffset, out var value);
    data[i] = value;
}
{% endhighlight %}

Line 3 is the statement I had to comment out because it wasn't working as expected, while the for loop is the "unsatisfying workaround". Unsatisfying for a couple reasons:

1. reading one-by-one is not as performant
2. not knowing the "why"

`accessor` is of type [MemoryMappedViewAccessor](https://learn.microsoft.com/en-us/dotnet/api/system.io.memorymappedfiles.memorymappedviewaccessor?view=net-8.0). I'll cover this in a future post. For now, just know that it's acting as a binary file reader.
{: .notice--info}

The commented out code works fine when the struct type contains only ints, floats, doubles, etc. The issue only surfaced when it tried to read a struct type that contains boolean values. Let's walk through an example using the following struct definition.

```csharp
struct MyStruct
{
    public bool MyBool;
}
```

We'll start by writing 2 instances of this struct to a binary file.

```csharp
public static void WriteStructs<T>(T[] structs)
    where T : unmanaged
{
    var structSize = Marshal.SizeOf<T>();
    var bytes = new byte[structs.Length * structSize];
    // convert structs to bytes...
    File.WriteAllBytes(BinaryFilePath, bytes);
}

var myStructs = new MyStruct[]
{
   new() { MyBool = true },
   new() { MyBool = true }
};
WriteStructs(myStructs);
```

This results in a binary file with a size of 8 bytes.

What? 8 bytes for 2 bool values?

> Although the bool type in C# is only 1 byte in size (sizeof(bool) == 1), the CLR defaults to marshalling it as the unmanaged BOOL type. This is the size you get when you call Marshal.SizeOf. BOOL is a typedef in the Windows SDK headers for an int, which is 4 bytes in size. Why? Because these headers were written for the C language at a time that this language did not have a first-class Boolean type. It does now, but the decisions are fixed in stone for backwards-compatibility reasons. The CLR marshals bool types this way in order to be compatible with Windows API functions that use BOOL values. [source](https://stackoverflow.com/questions/39251727/c-sharp-structlayout-pack-for-use-with-bool-values/39251864#39251864)

Okay, good to know. Let's just roll with this for now.

Printing out the bytes gives the following: `1,0,0,0,1,0,0,0`

Now it's clear why the for loop in the first snippet works fine: it uses `Marshal.SizeOf<T>` just like the `WriteStructs` method. The 2 `bool` values we get are `True,True` when printing the result:

```csharp
var str = string.Join(",", myStructs.Select(x => x.MyBool));
Console.WriteLine(str);
```

But what if we try using commented out code?

```csharp
accessor.ReadArray(position: 0, array: data, offset: 0, count: data.Length);
```

The 2 `bool` values end up being `True,False` 🤔

If we take a look at the `ReadArray` source code, we can see a call to [`SafeBuffer.AlignedSizeOf<T>()`](https://github.com/dotnet/runtime/blob/37445d4964a50eeff87ca7ed8cbdf251b547b779/src/libraries/System.Private.CoreLib/src/System/IO/UnmanagedMemoryAccessor.cs#L333), which ultimately [calls sizeof(T)](https://github.com/dotnet/runtime/blob/ab888616590c1f9654694af735d1f429fd27e26b/src/libraries/System.Private.CoreLib/src/System/Runtime/InteropServices/SafeBuffer.cs#L409).

`sizeof(MyStruct)` returns 1. That means `ReadArray` was only reading the first 2 bytes instead of all 8. Being that the file bytes are `1,0,0,0,1,0,0,0`, it now makes sense why it returned `True,False`. We can try reading 8 structs from that same file to further prove this theory.

```csharp
accessor.ReadArray(0, data, 0, 8);
// returns: True,False,False,False,True,False,False,False
```

This brings us to the difference between the two.

> [sizeof(T)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/sizeof) returns the size of a type in managed memory, and `Marshal.SizeOf` returns the size of a type in _unmanaged_ memory.

`sizeof(T)` and `Unsafe.SizeOf<T>` are equivalent in the sense that they both return the _managed size_ of a type, and they even compile down to the same IL instruction. The only difference is that `sizeof` only works when `T` is [unmanaged](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/unmanaged-types), and requires the `unsafe` keyword when used with custom structs.
{: .notice--info}

## Conclusion

So the bug was caused by mixing two different interpretations of size: managed and unmanaged. The binary utility that this code is part of has nothing to do with interop - it only reads and writes C# types - so `Marshal.SizeOf` is the wrong tool for the job. After swapping out all the `Marshal.SizeOf<T>` calls for `Unsafe.SizeOf<T>` I was able to replace the workaround with `ReadArray`, offically resolving the TODO comment.

```csharp
var data = new TValue[structCount];
accessor.ReadArray(position: 0, array: data, offset: 0, count: data.Length);
```

Unravelling this bug would have been a daunting task if I used a struct with many different fields and a binary file with thousands of bytes. But as with any problem, breaking it down simplifies the debugging experience a great deal.
