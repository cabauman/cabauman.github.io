---
title: "Welcome to Jekyll!"
date: 2019-04-18T15:34:30-04:00
categories:
  - Blog
tags:
  - Jekyll
  - update
---

## Unity Collection Pools API

Unity 2021.1 introduced a convenient pooling API which includes the following classes

- CollectionPool<T0,T1>
- DictionaryPool<T0,T1>
- GenericPool<T0>
- HashSetPool<T0>
- LinkedPool<T0>
- ListPool<T0>
- ObjectPool<T0>
- UnsafeGenericPool<T0>

Just bringing it up because I used it recently. Here's an example of normal usage:

```csharp
private void OnEnable()
{
    _myClass = GenericPool<MyClass>.Get();
}

private int OnDisable()
{
    GenericPool<MyClass>.Release(_myClass);
}
```

But if you only need it with a single method, you can use the overload that returns the item back to the pool automatically after disposal.

```csharp
public int DoSomeWork()
{
    using var _ = ListPool<Vector2>.Get(out List<Vector3> vertices);
    // Do some work
    ...
    return result;
}
```
