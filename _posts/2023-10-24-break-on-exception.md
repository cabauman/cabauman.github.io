---
title: "'Break on Exception' for Custom Exception Types"
categories:
  - Unity Tips
tags:
  - unity
  - unity-tip
---

When the debugger is attached, to enable "break on exception" for custom exception types go to Debug -> Windows -> Exception Settings and add a new entry with the full type name, like `UnityEngine.MissingReferenceException` and `UnityEngine.UnassignedReferenceException`.

![break-on-exception1](/assets/images/break-on-exception1.png)

![break-on-exception2](/assets/images/break-on-exception2.png)

![break-on-exception3](/assets/images/break-on-exception3.png)
