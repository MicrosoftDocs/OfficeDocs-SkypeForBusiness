---
title: Hardware requirements for Microsoft Teams
ms.reviewer: microthk, sthurlow
author: SerdarSoysal
ms.author: serdars
manager: serdars
audience: Admin
ms.topic: reference
ms.service: msteams
ms.collection: 
  - M365-collaboration
  - m365initiative-deployteams
ms.localizationpriority: high
search.appverid: MET150
description: In this article, you'll learn about the hardware requirements needed to install and run Microsoft Teams.
f1.keywords:
- CSH
ms.custom: 
  - NewAdminCenter_Update
  - seo-marvel-apr2020
appliesto: 
  - Microsoft Teams
---

# Hardware requirements for Microsoft Teams

All of the requirements in the following sections apply to both the Microsoft Teams desktop app and the Teams Web app.

## Hardware requirements for Teams on a Windows PC

| Component | Requirement |
|---------|---------|
|Computer and processor    | Minimum 1.1 GHz or faster, 2 core<br><br>Note: For Intel processors, the maximum speed achieved using Intel Turbo Boost Technology (Max Turbo Frequency) must be considered         |
|Memory     |  4.0 GB RAM |
|Hard disk    | 3.0 GB of available disk space        |
|Display    |   1024 x 768 screen resolution |
|Graphics hardware |  Windows OS: Graphics hardware acceleration requires DirectX 9 or later, with WDDM 2.0 or higher for Windows 10 (or WDDM 1.3 or higher for Windows 10 Fall Creators Update)
|Operating system  |    Windows 11, Windows 10 (excluding Windows 10 LTSC), Windows 10 on ARM, Windows 8.1, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2. Note: We recommend using the latest Windows version and security patches available.|
|.NET version    |  Requires .NET 4.5 CLR or later       |
|Video    |  USB 2.0 video camera       |
|Devices    |   Standard laptop camera, microphone, and speakers    |
|Video calls and meetings|<ul><li>Requires 2-core processor. For higher video/screen share resolution and frame rate, a 4-core processor or better is recommended.</li> <li>Background video effects require Windows 10 or a processor with AVX2 instruction set.</li> <li>See [Hardware decoder and encoder driver recommendations](hardware-decoders-and-encoders.md) for a list of unsupported decoders and encoders.</li><li>Joining a meeting using proximity detection in a Microsoft Teams Room requires Bluetooth LE, which requires Bluetooth to be enabled on the client device, and for Windows clients it also requires the 64-bit Teams client. This feature is not available on 32-bit Teams clients.</li></ul> |
|Teams live events | If you are producing a Teams live event, we recommend using a computer that has a Core i5 Kaby Lake processor, 4.0-GB RAM (or higher), and hardware encoder. See [Hardware decoder and encoder driver recommendations](hardware-decoders-and-encoders.md) for a list of **unsupported** decoders and encoders. |

## Hardware requirements for Teams on a Mac

| Component | Requirement |
|---------|---------|
|Computer and processor    | Intel Core Duo processor |
|Memory     |   4.0 GB RAM|
|Hard disk    |   1.5 GB of available disk space      |
|Display    | 1280 x 800 or higher resolution    |
|Operating system  |    One of the three most recent versions of macOS. You can find information about the latest macOS versions, and how to upgrade your version of macOS, [here](https://support.apple.com/en-us/HT201260). For example, when a new version of macOS is released, the new version and the two immediately preceding it become the supported versions.      |
|Video  |    Compatible webcam     |
|Voice    |  Compatible microphone and speakers, headset with microphone, or equivalent device       |
|Video calls and meetings | <ul><li>Requires 2-core processor. For higher video/screen share resolution and frame rate, a 4-core processor or better is recommended. </li><li>Joining a meeting using proximity detection in a Microsoft Teams Room is not available on macOS.</li></ul>
|

## Hardware requirements for Teams on Linux

| Component | Requirement |
|---------|---------|
|Computer and processor    | 1.6 GHz (or higher) (32-bit or 64-bit), 2 core        |
|Memory     |    4.0 GB RAM |
|Hard disk    | 3.0 GB of available disk space        |
|Display    |   1024 x 768 screen resolution |
|Graphics hardware |  128 MB graphics memory
|Operating system  | Linux distribution capable of installing DEB or RPM. |
|Video    |  USB 2.0 video camera       |
|Devices    |   Standard laptop camera, microphone, and speakers    |
|Voice    |  Compatible microphone and speakers, headset with microphone, or equivalent device       |
|Video calls and meetings | <ul><li>Requires 2-core processor. For higher video/screen share resolution and frame rate, a 4-core processor or better is recommended.</li><li>Joining a meeting using proximity detection in a Microsoft Teams Room is not available on Linux.</li></ul>
|Supported Linux distributions | Ubuntu 18.04 LTS, 20.04 LTS, Fedora 30 Workstation, RHEL 8 Workstation, CentOS 8       |
|Supported Desktop environment | GNOME, KDE       |
|Supported Display server | X11       |

## Hardware requirements for Teams on mobile devices

You can use Teams on these mobile platforms:

- Android: Compatible with Android phones and tablets.

  Support is limited to the **last four** major versions of Android. For example, when a new, major version of Android is released, the Android requirement is the new version and the three most recent versions that precede it.

- iOS: Compatible with iPhone, iPad, and iPod touch.

  Support is limited to the **two** most recent major versions of iOS. For example, when a new, major version of iOS is released, the iOS requirement is the new version and the most recent versions that preceded it. The optional **Blur my background** video effect on iOS requires an operating system of iOS 12 or later, compatible with the following devices: iPhone 7 or later, iPad 2018 (6th generation) or later, and the iPod touch 2019 (7th generation).

> [!Note]
> For the best experience with Teams, use the latest version of iOS and Android.

## Hardware requirements for Teams in a Virtual Desktop Infrastructure (VDI) environment

See [Teams for Virtualized Desktop Infrastructure](teams-for-vdi.md) for requirements for running Teams in a virtualized environment.

### Related topics

- [Get Teams apps](get-clients.md)
- [Microsoft Teams on mobile devices](https://support.microsoft.com/office/set-up-your-teams-mobile-apps-1ba8dce3-1122-47f4-8db6-00a4f93117e8)
- [Install the Microsoft Teams app using an MSI](msi-deployment.md)
- [Limits and specifications for Microsoft Teams](limits-specifications-teams.md)
