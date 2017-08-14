
### Release notes 0.4

<br>

The Programming Guide will present an overview of the features and API usages of the SDK. We recommend even experienced VR developers to read through this guide to familiarize themselves with Hypereal VR SDK.

#### Introduction

Hypereal VR Runtime is a set of DLLs, EXEs and some data files required for running Apps with Hypereal VR hardware.

Hypereal VR Development Kit includes:

  - SDK, includes header / lib flies and documents.
  - Sample applications are coming soon.
  - Unreal Plugins for the following versions of Unreal Engine:
    - Unreal 4.12
    - Unreal 4.13
    - Unreal 4.14
    - Includes documents and sample project.
  - Unity Plugins for latest Unity:
    - Unity 5.3
    - Unity 5.4
    - Unity 5.5
    - Includes plugins package with demo scene, and documents.

We're continuously updating our development kit for new features, stability, compatibility.

#### Features

- C/S mode, could switch smoothly between client apps when playing, and can be upgraded separately between Client Apps and Runtime (server side of C/S).
- DX11 and DX11.1 are supported in Runtime and Client App side, DX12 support is coming soon for Client App only.
- Direct Mode of NVIDIA and AMD are supported.
- Dynamic pixel density supported, 1.4 is by default.
- Asynchronous Time Warping.
- Asynchronous Space Warping.
- Position prediction in tracking system.
- Non-tracking system mode supported, can switch gameplay to non-tracking (play with Xbox Gamepad only etc.) in Plugins.
- Built-in profile tool provided, can switch to display rendering time, vsync on HMD screen.
- A crash reporter provided, can send reporter by mail automatically with one click or just close it to save crash dump into "local app data" folder.
- Built-in log system involved, can retrieve running status if a problem occurs.

#### Supported Platforms all subsequent operations will get

Windows 7 sp1, 8.1, 10.

(x64 only for all of them)

#### Supported Dev Tools

Visual Studio 2013

Visual Studio 2015

#### Recommended Spec of PC

NVIDIA GTX 970 / AMD 290 equivalent or greater

Intel i5-4590 equivalent or greater

8GB+ RAM

Compatible HDMI 1.3 video output

2x USB 3.0 ports

#### Version History

Version 0.1

SDK for prototype hardware with lighthouse tracking, join our Announcement of product in China Joy 2016.

Unreal plugin for Unreal Engine 4.10 is provided for internal game project "Zombies Never Die", and also third party content developers for China Joy.

Version 0.2

SDK was improved with C/S mode, so "Development" and "Play" would be separated. All the Apps provided by third party content developers are "Clients", when playing they are all running on "Server" installed in players local PC in different folders.

Unity plugin is ready for internal test.

Version 0.3

Performance enhancement for C/S mode

Separation of Runtime & Development Kit

Polish of Runtime and Development Kit

Unity plugins for Unity 5.2, 5.3 and 5.4.

Unreal plugins for Unreal Engine 4.11, 4.12 and 4.13 (Unreal Engine installed by Epic Launcher and Epic's GitHub.

Version 0.4

Camera tracking system.

Asynchronous Space Warping is involved, please refer "Asynchronous Space Warping" to get details.

#### Known Issues

1. Unreal Project can't be in path with Unicode characters, such as in Chinese.
2. Runtime is not so stable in some conditions, we're working on it.
3. Compatibility issue, games exported with plugins other then this version(0.4) won't work in 0.4 runtime.
4. Audio output on HMD is not working properly if running game (espcailly a Unreal Game) before hvrService.exe launched.

