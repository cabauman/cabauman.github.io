---
title: "Visual Studio Tracepoints"
categories:
  - Unity Tips
tags:
  - unity
  - unity-tip
  - visual-studio
---

You know those fleeting logs you scatter around when trying to debug an issue? A couple downsides are
- compilation time every time you need to add or modify a log
- have to remember to remove them when finished (unless they're useful enough to keep around)

![script-template1](/assets/images/vs-tracepoints.png)

Well, instead of putting those logs in the code, try moving them to a [special kind of breakpoint known as a Tracepoint](https://devblogs.microsoft.com/visualstudio/tracepoints/){:target="_blank"}. Its primary use case is printing text to the Visual Studio console, but it also allows us to execute methods by putting the invocation inside a pair of curly braces. We can utilize this by calling Unity's Debug.Log:

```csharp
{Debug.Log("value: " + transform.name)}
```

![script-template1](/assets/images/vs-tracepoints2.png)