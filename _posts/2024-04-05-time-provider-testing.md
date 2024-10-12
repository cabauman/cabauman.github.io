---
title: "Using .NET 8 TimeProvider + FakeTimeProvider in Unity"
categories:
  - Code Journal
tags:
  - C#
  - testing
  - Unity
---

As a fan of testing I was pleased about this addition.

- No more custom IClock abstractions
- Adding a "time" abstraction that wraps calls to DateTime.UtcNow and other similar APIs has been a common approach to testing for a long time.
- Task extensions
- Timer
- Time zone
- Mocking

```csharp
public abstract class TimeProvider
{
    public static TimeProvider System { get; }
    protected TimeProvider() 
    public virtual DateTimeOffset GetUtcNow()
    public DateTimeOffset GetLocalNow()
    public virtual TimeZoneInfo LocalTimeZone { get; }
    public virtual long TimestampFrequency { get; }
    public virtual long GetTimestamp()
    public TimeSpan GetElapsedTime(long startingTimestamp)
    public TimeSpan GetElapsedTime(long startingTimestamp, long endingTimestamp)
    public virtual ITimer CreateTimer(TimerCallback callback, object? state,TimeSpan dueTime, TimeSpan period)
}
```

```csharp
namespace System.Threading.Tasks
{
    public static class TimeProviderTaskExtensions
    {
        public static Task Delay(this TimeProvider timeProvider, TimeSpan delay, CancellationToken cancellationToken = default) 
        public static Task<TResult> WaitAsync<TResult>(this Task<TResult> task, TimeSpan timeout, TimeProvider timeProvider, CancellationToken cancellationToken = default)
        public static Tasks.Task WaitAsync(this Task task, TimeSpan timeout, TimeProvider timeProvider, CancellationToken cancellationToken = default)
        public static CancellationTokenSource CreateCancellationTokenSource(this TimeProvider timeProvider, TimeSpan delay)
    }
}
```

https://devblogs.microsoft.com/dotnet/announcing-dotnet-8-preview-4/#introducing-time-abstraction
https://www.nuget.org/packages/Microsoft.Bcl.TimeProvider
https://www.nuget.org/packages/Microsoft.Extensions.TimeProvider.Testing

---

[Official Source](https://github.com/dotnet/extensions/tree/main/src/Libraries/Microsoft.Extensions.TimeProvider.Testing

