---
title: ITAdmin information for Microsoft Teams RealWear client (Preview)
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: 
description: A, ITAdmin walkthrough of the RealWear client for Microsoft Teams.
localization_priority: Priority
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_RemoteWorkers
  - remotework
appliesto: 
  - Microsoft Teams
---
# RealWear for Microsoft Teams

> [!NOTE]
> This is a preview or early release feature.

This article covers the Microsoft Teams client for RealWear head-mounted wearables. FirstLine Workers using RealWear HMT-1 and HMT-1Z1 can now collaborate with a remote expert using video calling on Teams. Through a voice-controlled user interface, Teams for RealWear allows field workers to remain 100% hands-free while maintaining situational awareness in loud and hazardous environments. By showing what they see in real-time, field workers can accelerate the time to resolve issues and reduce the risk of an expensive downtime.

## How to deploy Microsoft Teams for RealWear

Microsoft Teams client for RealWear is currently in Public Preview. To participate in this preview, you will need the following:

RealWear devices updated to release 10.5.0 or above. More information [here](https://realwear.com/knowledge-center/configure-on-release-10/wireless-update/).

> [!IMPORTANT]
> Register [here](https://www.realwear.com/solutions/microsoft-teams/#C1) for access to Teams for RealWear client in [RealWear Foresight](https://cloud.realwear.com/).

## Required Licenses

Microsoft Teams licenses are part of Office 365 subscriptions. No additional licensing is required to use Teams for RealWear. For more information about getting Teams, check out [How do I get access to Microsoft Teams](https://support.office.com/article/fc7f1634-abd3-4f26-a597-9df16e4ca65b).

## Managing RealWear devices

### Microsoft Endpoint Manager

RealWear devices can be managed using Android Device Administrator mode. Support for management via Android Enterprise is limited, as the devices currently don't have Google Mobile Services (GMS) available.

- To learn more about managing RealWear devices on Microsoft Endpoint Manager, see [Android device administrator enrollment in Intune](https://docs.microsoft.com/mem/intune/enrollment/android-enroll-device-administrator).

### Third-party Enterprise Mobility Managers (EMMs)

For guidance on third-party EMMs, see [Supported Enterprise Mobility Management Providers](https://www.realwear.com/knowledge-center/configure-on-release-10/remote-from-a-web-browser/emm/).
