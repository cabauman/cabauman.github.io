---
title: "Projects at Capgemini Engineering"
excerpt: "2024-2025: Digital Twin & Industry Team"
project_type: Professional
#classes: wide
header:
  teaser: /assets/images/capgemini/capgemini_logo_teaser.png
sidebar:
  - image: /assets/images/capgemini/capgemini_logo.png
    text: "Aug 2024 - Apr 2025<br/>Experience Engineering team: build real-time 3D applications for Industry such as Automotive, Manufacturing, Retail, and Healthcare"
---

**NOTE:** The following client project has not been made public so I'm not able to include screenshots or videos.
{: .notice--info}

## ADAS HMI Project

**Period:** Aug 2024 - May 2025<br />
**Platform:** Windows<br />
**Role:** Lead Engineer<br />
**Engineers:** 2<br />
**Engine:** Unreal 5.3<br />
**Tags:** [Advanced Driver-Assistance System](https://en.wikipedia.org/wiki/Advanced_driver-assistance_system) | [Human-Machine Interface](https://en.wikipedia.org/wiki/User_interface)

**Background**

This project is the second phase of the one we worked on at Unity Technologies (before our team was sold to Capgemini). Phase 1 was developed with Unity but for phase 2 the client required a port to Unreal Engine. I was the only engineer at the time and hadn't used Unreal Engine since university. So, while contract agreement details were being worked out I focused on quickly getting reacquainted with Unreal and C++. My first task was basically to create a clone of the Unity project in Unreal. The target delivery of both phases is the editor project (not a build), so in addition to runtime features, custom editor tooling is also required. About four months later an another engineer joined me on the project.

**Summary**

The whole concept behind the runtime aspect of this project is to read ECU (electronic control unit) measurement values from a vehicle and turn that into a RT3D visual simulation. The editor tooling aspect makes it possible for the user to customize what assets appear when a given signal is received.

**Definitions**

CAN - Controller Area Network: a messaging-based protocol that enables electronic control units (ECUs) to communicate within a vehicle or other systems

[Vector CANoe](https://www.vector.com/int/en/products/products-a-z/software/canoe/#): analysis and simulation tool for bus systems used in the automotive industry

COM – Component Object Model: a standard defined by Microsoft for the communication between different software components. Different programming languages can be used to create such components. These components can be built by different software developers, independently from each other.

CANoe COM Server: allows users to write their own applications or components that interface/interoperate with CANoe ([API Guide](https://cdn.vector.com/cms/content/know-how/_application-notes/AN-AND-1-117_CANoe_CANalyzer_as_a_COM_Server.pdf))

**API Integration**

In phase 1 we used the C# COM dll provided by Vector CANoe, but for phase 2 we had to switch over to using the C/C++ COM API. So my first task was to integrate that into Unreal.

Starting up the CANoe application from C++ blocks the calling thread for about 15 seconds, so I utilized Unreal's [AsyncTask](https://dev.epicgames.com/documentation/en-us/unreal-engine/API/Runtime/Core/Async/AsyncTask) to execute it on a helper thread and notify the GameThread when finished. We display an animated loading indicator while this is going on.

```c++
AsyncTask(ENamedThreads::AnyThread, [this, OnCompleted]()
{
    OpenCANoe();

    AsyncTask(ENamedThreads::GameThread, [this, OnCompleted]()
    {
        InitializeCANoeOnMainThread();
        OnCompleted.ExecuteIfBound();
    });
});
```

**Notable Contributions**

Estimated C++ vs Blueprint usage: 80% - 20%

- developed custom editor windows using Slate and Editor Utility Widgets
- used Unreal's localization system to localize the custom editor windows (Korean and English)
- used a data table as the "single source of truth" for CAN signals
- built a "scenario editor" tool for reading and writing csv files for testing
  - 3 columns: signal name, timestamp, value
- created an Unreal Plugin for the C++ COM API integration
- abstracted the CANoe API behind an interface so we're able to use a mock implementation when we don't have access to the CANoe software
- used pooling for Widgets and Actors
