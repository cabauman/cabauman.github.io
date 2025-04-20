---
title: "Projects at Unity Technologies"
excerpt: "2022-2024: Digital Twin & Industry Team"
project_type: Professional
classes: wide
header:
  teaser: /assets/images/unity-employment/unity-logo-teaser.png
sidebar:
  - image: /assets/images/unity-employment/unity-logo.svg
    text: "<p><b>Aug 2022 - Apr 2024</b></p><p><b>Senior Software Engineer</b></p><p><b>Experience Engineering Team</b> - build real-time 3D applications for industries such as Automotive, Manufacturing, Retail, and Healthcare</p>"
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
---

**NOTE:** The following projects were for clients, so only the ones that were made public include screenshots/videos.
{: .notice--info}

## LG Meta Slap

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/unity-employment/lg-meta-slap6.avif" style="width: 40%" class="align-right"/>

**Period:** Aug 2022 - Feb 2023<br />
**Platform:** Windows & Mac<br />
**Role:** Unity Engineer<br />
**Engineers:** 4<br />
**Description:** a virtual office "metaverse" application developed during the COVID-19 pandemic

[Unity Blog: LG U+ fosters real connections for virtual offices](https://unity.com/blog/industry/lg-u-plus-fosters-connections-for-virtual-offices)

{% include gallery %}

**Notable Contributions:**
- implemented an in-app messenger using [SendBird](https://sendbird.com/docs/chat/sdk/v4/unity/getting-started/send-first-message) (basically a clone of KakaoTalk)
  - incremental message history loading based on scroll
  - file/image uploads with expirations
  - 1:1 and group chats
  - user profiles, favorites, mentions with autocomplete
- implemented video and voice chat with [Agora](https://www.agora.io/en/blog/agora-video-sdk-for-unity-quick-start-programming-guide/) library
- implemented native plugins for both Windows and Mac
  - file selection and save dialogs
  - window resizing and "always on top"
- replaced AWS API calls with custom backend API
- integrated Unity analytics

## App Optimization - Project Makeover

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/unity-employment/project-makeover.webp" style="width: 40%" class="align-right"/>


**Period:** Feb 2023 - Apr 2023<br />
**Platform:** Android<br />
**Role:** Unity Engineer<br />
**Engineers:** 3<br />
**Description:** The goal of this project was to profile the whole application to make as many optimizations as possible.

[Project Makeover on Google Play](https://play.google.com/store/apps/details?id=com.bgg.jump&hl=en)

**Notable Contributions:**
- reduced GC (closures, boxing, temporary allocations, etc.)
- reduced audio and texture storage space
- improved loading times via config values and caching

## Multiplayer Game

**Period:** Apr 2023 - Jul 2023<br />
**Platform:** Windows<br />
**Role:** .NET Backend Engineer<br />

**Notable Contributions:**
- implemented basic player matching
- developed a mock .NET backend service that can be swapped in and out with the real external dependency; this was important for deterministic testing; this mock service includes the use of RPC and Redis
- improved stability by catching potential regressions and edge cases via improved code coverage and CI

## NUHS Holomedicine

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/unity-employment/nuhs-holomedicine.png" style="width: 40%" class="align-right"/>

**Period:** Jul 2023 - Sep 2023<br />
**Platform:** Microsoft HoloLens 2<br />
**Role:** Unity Engineer<br />
**Engineers:** 4<br />
**Description:** Project for the [National University Health System](https://www.nuhs.edu.sg/) in Singapore which utilizes [Mixed Reality Toolkit (MRTK)](https://learn.microsoft.com/en-us/windows/mixed-reality/mrtk-unity/mrtk3-overview/).

**Notable Contributions:**
- implemented high performance filtering using Burst and the Unity Job System
- implemented ultrasound user flow
  - instruct user to translate/rotate/scale a cuboid and use the medical handheld device to scan within
  - convert world-space values to cuboid-space
  - send scanned data to backend via gRPC
  - display loading indicator while asynchronously awaiting the result of 3D mesh reconstruction
- implemented play-mode tests that simulate XR interactions in the editor (e.g. pressing buttons and interacting with the cuboid)

<iframe src="https://www.linkedin.com/embed/feed/update/urn:li:ugcPost:7114952710122049536?compact=1" height="399" width="504" frameborder="0" allowfullscreen="" title="Embedded post"></iframe>

## Satellite Monitoring Prototype

**Period:** Oct 2023 - Nov 2023<br />
**Platform:** Windows<br />
**Role:** Unity Engineer<br />
**Engineers:** 1 (and 1 TA)

**Notable Contributions:**
- implemented camera controls (rotate around the Earth model and zoom in/out)
- implemented deterministic orbits using the equation for an eclipse, and expose properties that TA can configure
  - we initially used the Splines package but it was inefficient
- trigger alert when a satellite gets too close to debris or another satellite; then enter simulation mode for collision predication
- wrote a compute shader that renders thousands of quads that always face the camera and rotate around the Earth in random orbits

## Smart City Project

**Period:** Nov 2023 - Feb 2024<br />
**Platform:** Windows & Mac<br />
**Role:** Unity Engineer<br />
**Engineers:** 2<br />
**Description:** Visualize city data such as building visitors, sales, weather, populations, etc. Visualizations include day/night system, rain, clouds, heat map, world-space UI, point cloud, and others.

**Notable Contributions:**
- developed a custom editor window using UI Toolkit
  - designed importer to parse, filter, and transform CSV data to binary for efficient storage and fast reading at runtime
  - utilize Unity's [Background Tasks Window](https://docs.unity3d.com/6000.2/Documentation/Manual/BackgroundTasksWindow.html) for asynchronous imports via the [Progress API](https://docs.unity3d.com/6000.2/Documentation/ScriptReference/Progress.html); tested with CSV files up to 10gb in size
- implemented simulation playback: select a date range via calendar pickers and then use the play/pause button and slider to simulate
  - also implemented split screen mode to simulate and compare two date ranges side-by-side
- utilized low-level code and the [MemoryMappedFile API](https://learn.microsoft.com/en-us/dotnet/standard/io/memory-mapped-files) to reference a specific range of data without needing to load the whole binary file
- applied custom and minimalistic dependency injection resulting in zero singletons in the project
- caught data import bugs and runtime data presentation bugs thanks to unit and integration tests

## ADAS HMI Project

**Period:** Feb 2024 - Apr 2024<br />
**Platform:** Windows<br />
**Role:** Unity Engineer<br />
**Engineers:** 3<br />
**Tags:** [Advanced Driver-Assistance System](https://en.wikipedia.org/wiki/Advanced_driver-assistance_system) | [Human-Machine Interface](https://en.wikipedia.org/wiki/User_interface)<br />
**Description:** I joined this project at the halfway point to assist with editor tooling. You can find a lot more detailed information about phase 2 of this project [here](../2024-2025-capgemini-projects), where I was the lead engineer.

**Notable Contributions:**
- developed custom editor windows using both IMGUI and UI Toolkit
  - add/remove/edit data items and save in ScriptableObjects
  - handle communication between multiple editor windows; basically a master-detail UI with a tree view of data items
