---
title: "CallerArgumentExpressionAttribute in Unity"
categories:
  - Unity Tips
tags:
  - unity
  - unity-tip
  - c#
---

C# 10 introduced the `CallerArgumentExpressionAttribute` which can be useful for custom logging and utility methods like assertions and guard checks. Without this we have to supply the expression manually, e.g. `Ensure.NotNull(myInstance, nameof(myInstance))`. Unity only supports up to C# 9, so we don't get this attribute by default. However, starting in Unity 2022 (because of the compiler used) we can "unlock" this feature by manually adding the attribute class. Here is the attribute and a couple examples:

```csharp
namespace System.Runtime.CompilerServices
{
    [AttributeUsage(AttributeTargets.Parameter, AllowMultiple = false, Inherited = false)]
    internal sealed class CallerArgumentExpressionAttribute : Attribute
    {
        public CallerArgumentExpressionAttribute(string parameterName)
        {
            ParameterName = parameterName;
        }

        public string ParameterName { get; }
    }
}
```

```csharp
public class Demo : MonoBehaviour
{
    private void Start()
    {
        var a = 2;
        var b = 3;
        Assert(a + b == 4);
    }

    private void Assert(bool condition, [CallerArgumentExpression] string expression = "")
    {
        if (!condition)
        {
            throw new Exception($"'{expression}' is false");
        }
    }
}
```

![caller-argument-expression-attribute1](/assets/images/caller-argument-expression-attribute1.png)

![caller-argument-expression-attribute2](/assets/images/caller-argument-expression-attribute2.png)

[Attribute docs](https://learn.microsoft.com/en-us/dotnet/api/system.runtime.compilerservices.callerargumentexpressionattribute?view=net-7.0)