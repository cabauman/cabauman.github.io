---
title: "Init Keyword in Unity"
categories:
  - Unity Tips
tags:
  - unity
  - unity-tip
  - c#
---

C# 9 introduced the init keyword which can be applied to properties and indexers. This means the value can only be set during object initialization (unlike set). Unity supports C# 9 since 2021.2, but you'll notice the init keyword doesn't work right out of the box.

![Image Click Area](/assets/images/unitytip-init.png)

The compiler complains about missing something called IsExternalInit. If you search online, you'll find a small snippet of code that you can add to your project to fill in the missing piece.

![Image Click Area](/assets/images/unitytip-init2.png)

Of course, MonoBehaviours can't benefit from this feature, but still a lot of use cases. Immutable properties ftw!

[init keyword docs](https://lnkd.in/gep2ARvk){:target="_blank"}

[IsExternalInit snippet](https://stackoverflow.com/questions/62648189/testing-c-sharp-9-0-in-vs2019-cs0518-isexternalinit-is-not-defined-or-imported/62656145#62656145){:target="_blank"}

![Image Click Area](/assets/images/unitytip-init3.png)