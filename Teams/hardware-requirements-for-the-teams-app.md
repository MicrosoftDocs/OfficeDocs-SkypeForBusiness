---
title: Hardware requirements for Microsoft Teams
ms.reviewer: 
author: LolaJacobsen
ms.author: lolaj
manager: serdars
audience: Admin
ms.topic: reference
ms.service: msteams
ms.collection: 
  - M365-collaboration
localization_priority: Normal
search.appverid: MET150
description: In this article, you will learn about the hardware requirements that are needed to install and run Microsoft Teams.
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

|**Component**|**Requirement**  |
|---------|---------|
|Computer and processor    | Minimum 1.6 GHz (or higher) (32-bit or 64-bit).        |
|Memory     |    2.0 GB RAM     |
|Hard disk    | 3.0 GB of available disk space        |
|Display    |   1024 x 768 screen resolution |
|Graphics hardware |  Minimum of 128 MB graphics memory
|Operating system  |    Windows Server 2012 R2+, Windows 10, or Windows 8.1 in 32-bit and 64-bit. For the best experience, use the latest version of your operating system.|
|.NET version    |  Requires .NET 4.5 CLR or later       |
|Video    |  USB 2.0 video camera       |
|Devices    |   Standard laptop camera, microphone, and speakers    | 
|Video calls and meetings | <ul><li>For a better experience with 1:1 video calls, we recommend using a computer that has a single-core processor and 4.0 GB RAM (or higher). </li><li>For a better experience with online meetings, we recommend using a computer that has a dual-core processor and 8.0 GB RAM (or higher). </li><li>The optional **Blur my background** video effect requires a processor with Advanced Vector Extensions 2 (AVX2) support. See [Hardware decoder and encoder driver recommendations](hardware-decoders-and-encoders.md) for a list of unsupported decoders and encoders.</li><li>Joining a meeting using proximity detection in a Microsoft Teams Room requires Bluetooth LE, which requires Bluetooth to be enabled on the client device, and for Windows clients requires the 64-bit Teams client. It's not available on 32-bit Teams clients.</li></ul> |
|Teams live events | If you are producing a Teams live events, we recommend using a computer that has a Core i5 Kaby Lake processor, 4.0 GB RAM (or higher) and hardware encoder. See [Hardware decoder and encoder driver recommendations](hardware-decoders-and-encoders.md) for a list of unsupported decoders and encoders. |

## Hardware requirements for Teams on a Mac

|**Component**|**Requirement**  |
|---------|---------|
|Processor    | Minimum Intel processor, Core 2 Duo or higher |
|Memory     |   2.0 GB RAM      |
|Hard disk    |   1.5 GB of available disk space      |
|Display    | 1280 x 800 or higher resolution    |
|Operating system  |    Mac OS X 10.11 El Capitan or later     |
|Video  |    Compatible webcam     |
|Voice    |  Compatible microphone and speakers, headset with microphone, or equivalent device       |
|Video calls and meetings | <ul><li>For a better experience with 1:1 video calls, we recommend using a computer that has a single-core processor and 4.0 GB RAM (or higher). </li><li>For a better experience with online meetings, we recommend using a computer that has a dual-core processor and 8.0 GB RAM (or higher). </li><li>The optional **Blur my background** video effect requires a processor with Advanced Vector Extensions 2 (AVX2) support, supported on most late 2013 Mac devices and later. See [Hardware decoder and encoder driver recommendations](hardware-decoders-and-encoders.md) for a list of unsupported decoders and encoders.</li><li>Joining a meeting using proximity detection in a Microsoft Teams Room is not available on Mac OS.</li></ul> |

## Hardware requirements for Teams on Linux

|**Component**|**Requirement**  |
|---------|---------|
|Computer and processor    | Minimum 1.6 GHz (or higher) (32-bit or 64-bit).        |
|Memory     |    2.0 GB RAM     |
|Hard disk    | 3.0 GB of available disk space        |
|Display    |   1024 x 768 screen resolution |
|Graphics hardware |  Minimum of 128 MB graphics memory
|Operating system  | Linux distribution capable of installing DEB or RPM. |
|Video    |  USB 2.0 video camera       |
|Devices    |   Standard laptop camera, microphone, and speakers    | 
|Voice    |  Compatible microphone and speakers, headset with microphone, or equivalent device       |
|Video calls and meetings | <ul><li>For a better experience with 1:1 video calls, we recommend using a computer that has a single-core processor and 4.0 GB RAM (or higher). </li><li>For a better experience with online meetings, we recommend using a computer that has a dual-core processor and 8.0 GB RAM (or higher).  </li><li>Background video effects require a processor with Advanced Vector Extensions 2 (AVX2) support, supported on most late 2013 Mac devices and later. See [Hardware decoder and encoder driver recommendations](hardware-decoders-and-encoders.md) for a list of unsupported decoders and encoders.</li><li>Joining a meeting using proximity detection in a Microsoft Teams Room is not available on Linux.</li></ul>
|Supported Linux distributions | Ubuntu 16.04 LTS, 18.04 LTS, Fedora 30 Workstation, RHEL 8 Workstation, CentOS 8

## Hardware requirements for Teams on mobile devices

You can use Teams on these mobile platforms:

- Android: Compatible with Android phones and tablets.

  Support is limited to the last four major versions of Android. When a new major version of Android is released, the new version and the previous three versions are officially supported.

- iOS: Compatible with iPhone, iPad, and iPod touch.

  Support is limited to the two most recent major versions of iOS. When a new major version of iOS is released, the new version of iOS and the previous version are officially supported.

For the best experience with Teams, use the latest version of iOS and Android.

## Hardware requirements for Teams in a Virtual Desktop Infrastructure (VDI) environment

See [Teams for Virtualized Desktop Infrastructure](teams-for-vdi.md) for requirements for running Teams in a virtualized environment.

### Related topics
- [Get Teams apps](get-clients.md)
- [Microsoft Teams on mobile devices](https://support.office.com/article/Microsoft-Teams-on-mobile-devices-2ACBCF73-8FD4-4929-9B31-AE403B88C2D3)
- [Install the Microsoft Teams app using an MSI](msi-deployment.md)
- [Limits and specifications for Microsoft Teams](limits-specifications-teams.md)
