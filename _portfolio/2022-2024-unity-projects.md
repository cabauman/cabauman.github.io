---
title: "Unity Technologies Projects"
excerpt: "2018-2022: Educational Technology company"
header:
  teaser: /assets/images/unity-employment/lg-meta-slap6.avif
gallery:
  - url: /assets/images/unity-employment/lg-meta-slap1.gif
    image_path: assets/images/unity-employment/lg-meta-slap1.gif
  - url: /assets/images/unity-employment/lg-meta-slap2.gif
    image_path: assets/images/unity-employment/lg-meta-slap2.gif
  - url: /assets/images/unity-employment/lg-meta-slap3.gif
    image_path: assets/images/unity-employment/lg-meta-slap3.gif
  - url: /assets/images/unity-employment/lg-meta-slap4.gif
    image_path: assets/images/unity-employment/lg-meta-slap4.gif
  - url: /assets/images/unity-employment/lg-meta-slap5.gif
    image_path: assets/images/unity-employment/lg-meta-slap5.gif
classes: wide
---

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/unity-employment/unity-logo.svg" style="height: 80px" />

## LG Meta Slap

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/unity-employment/lg-meta-slap6.avif" style="width: 40%" class="align-right"/>

**Period:** Aug 2022 - Feb 2023<br />
**Platform:** Windows & Mac<br />
**Role:** Unity Engineer<br />
**Engineers:** 4<br />
**Description:** TODO

- SendBird
- [Agora](https://www.agora.io/en/blog/agora-video-sdk-for-unity-quick-start-programming-guide/)
- Photon

[Unity Blog: LG U+ fosters real connections for virtual offices](https://unity.com/blog/industry/lg-u-plus-fosters-connections-for-virtual-offices)

{% include gallery %}

**Contributions:**<br />
- 

## Google Optimization - Project 

{% include video id="R0X5k8IJ4Tk" provider="youtube" class="align-right" style="width: 40%" %}

**Period:** Feb 2023 - Apr 2023<br />
**Platform:** Android<br />
**Role:** Unity Engineer<br />
**Engineers:** 3<br />
**Description:** TODO

[Project Makeover on Google Play](https://play.google.com/store/apps/details?id=com.bgg.jump&hl=en)

**Contributions:**<br />
- reduced C# GC allocations
- reduced audio and texture storage space
- improved loading times via config values and caching

## Multiplayer Game

**Period:** Apr 2023 - Jul 2023<br />
**Platform:** Windows<br />
**Role:** .NET Backend Engineer<br />

**Confidential:** details and screenshots excluded
{: .notice--info}

**Contributions:**<br />
- developed a mock .NET backend service that can be swapped in and out with the real external dependency; this was important for deterministic testing; this mock service includes the use of RPC and Redis
- improved stability by catching potential regressions and edge cases via improved code coverage and CI

## NUHS Holomedicine

<iframe style="aspect-ratio: 1280 / 720;" width="504" height="0" src="{{ site.url }}{{ site.baseurl }}/assets/images/unity-employment/nuhs-video.mp4" frameborder="0" class="align-right"> </iframe>

**Period:** Jul 2023 - Sep 2023<br />
**Platform:** Microsoft HoloLens 2<br />
**Role:** Unity Engineer<br />
**Engineers:** 4<br />
**Description:** Project for the [National University Health System](https://www.nuhs.edu.sg/) in Singapore

- Mixed Reality Toolkit (MRTK)
- gRPC
- OpenCV
- Python
- NumPy

**Contributions:**<br />
- implemented file selection and file save dialogs
- implemented "scan region" translate/rotate/scale cuboid
- implemented scan progress feature
- optimized 3D mesh reconstruction
- implemented play-mode tests that simulate XR interactions in the editor (e.g. pressing buttons and interacting with the cuboid)

## Satellite Monitoring Prototype

**Period:** Oct 2023 - Nov 2023<br />
**Platform:** Windows<br />
**Role:** Unity Engineer<br />
**Engineers:** 1 (and 1 TA)<br />
**Description:** This project is 

**Confidential:** details and screenshots excluded
{: .notice--info}

**Contributions:**<br />
- implement camera controls (rotate around the Earth model and zoom in/out)
- implement deterministic orbits using the eclipse equation, and expose properties that TA can configure
  - we initially used the Splines package but it was inefficient
- trigger alert when a satellite gets to close to debris or another satellite; then enter simulation mode for collision predication
- wrote a compute shader that renders thousands of quads that always face the camera and rotate around the Earth in random orbits

## Smart City Project

**Period:** Nov 2024 - Feb 2024<br />
**Platform:** Windows & Mac<br />
**Role:** Unity Engineer<br />
**Engineers:** 2<br />
**Description:** Visualize city data such as building visitors, sales, weather, populations, etc. Visualizations include day/night system, rain, clouds, heat map, world-space UI, point cloud, and others.

- https://assetstore.unity.com/packages/tools/utilities/plateau-sdk-for-unity-245703?srsltid=AfmBOooPu4Uj4RKCepnyPMa5ePaELak7AdFPJjEb6aQJqc5Zc0CsBx6z#reviews

**Confidential:** details and screenshots excluded
{: .notice--info}

**Contributions:**<br />
- developed a custom editor window using UI Toolkit
  - convert CSV data to binary for efficient storage and fast reading at runtime
  - implemented an extensible importer system; each CSV type has it's own importer class, because of specific data processing requirements, but share the same interface
  - utilize Unity's [Background Tasks Window](https://docs.unity3d.com/6000.2/Documentation/Manual/BackgroundTasksWindow.html) for asynchronous imports via the [Progress API](https://docs.unity3d.com/6000.2/Documentation/ScriptReference/Progress.html); tested with CSV files up to 10gb in size
- implemented simulation playback: select a date range via calendar pickers and then use the play/pause button and slider to simulate
  - also implemented split screen mode to simulate and compare two date ranges side-by-side
- utilized low-level code and the [MemoryMappedFile API](https://learn.microsoft.com/en-us/dotnet/standard/io/memory-mapped-files) to reference a specific range of data without needing to load the whole binary file
- applied custom and minimalistic dependency injection resulting in zero singletons in the project
- caught data import bugs and runtime data presentation bugs thanks to unit and intergration tests

## ADAS HMI Project

**Period:** Feb 2024 - Apr 2024<br />
**Platform:** Windows<br />
**Role:** Unity Engineer<br />
**Engineers:** 3<br />
**Description:** TODO

**Confidential:** details and screenshots excluded
{: .notice--info}

**Contributions:**<br />
- developed custom editor windows using both IMGUI and UI Toolkit
