---
title: "GPU Instancing & Compute Shader Demo"
excerpt: "2023: GPU instancing & compute shader demo"
project_type: Personal
header:
  teaser: /assets/images/gpu-instancing/gpu-instancing-orbit.png
sidebar:
  - title: "Details"
    image: /assets/images/gpu-instancing/gpu-instancing-orbit.png
    text: "- Team Size: 1\n- Platform: Windows\n- Tech: Unity, URP"
  #- nav: portfolio
---

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/gpu-instancing/gpu-instancing-inspector.png" style="width: 40%" class="align-right"/>

Features
- can render over a million quads
- uses the [Graphics.RenderMeshPrimitives](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/Graphics.RenderMeshPrimitives.html) API
- enable/disable billboarding (mesh will always face the camera)
- position and rotation are updated in a compute shader
- applies frustum culling by passing in the bounds of the render area
- generates random points within a sphere and random rotation axes
- list of speeds and sizes to be chosen at random

{% include video id="l0RC5X2zB3Y" provider="youtube" %}