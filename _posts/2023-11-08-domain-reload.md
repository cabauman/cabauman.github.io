---
title: "Enter Play Mode Faster"
categories:
  - Unity Tips
tags:
  - unity
  - unity-tip
---

Disable domain reloading for quicker iteration time during development (if you have to frequently enter and exit play mode). Open Project Settings -> Editor, scroll all the way down, and enable the "Enter Play Mode Options" checkbox while leaving the 2 child checkboxes unchecked. The only thing you have to be aware of is static fields and event handler that won't get reset. The docs have a helpful section to assist: [Domain Reloading](https://docs.unity3d.com/Manual/DomainReloading.html).

It won't be realistic for bigger projects, but still comes in really handy in certain cases, especially when prototyping and for small projects. SceneManager.sceneLoaded event can be enabled by enabling the "Reload Scene" checkbox.

![disable-domain-reload](/assets/images/disable-domain-reload.png)

Domain Reload On

<video width="480" controls="controls">
  <source src="/assets/videos/domain-reload-on.mp4" type="video/mp4">
</video>

<br />
Domain Reload Off

<video controls>
  <source src="/assets/videos/domain-reload-off.mp4" type="video/mp4">
</video>
