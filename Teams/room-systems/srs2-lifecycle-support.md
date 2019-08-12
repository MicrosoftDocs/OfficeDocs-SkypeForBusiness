---
title: "Version Support"
ms.author: v-lanac
author: lanachin
ms.reviewer: davgroom
manager: serdars
ms.date: 4/17/2018
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
ms.collection: M365-voice
localization_priority: Normal
description: "This article discusses lifecycle support for Microsoft Teams Rooms."
---

# Microsoft Teams Rooms app version support
 
Microsoft plans to release updates for Microsoft Teams Rooms a few times per year with each update supported for twelve (12) months from its general availability (GA) release date. Technical support is provided for the entire twelve (12) months. However, the support structure is now dynamic, evolving into two distinct servicing phases that depend on the availability of the latest version.

**Servicing and Critical Updates servicing phase** \- When running the latest version of Microsoft Teams Rooms, you receive regular updates, that contain Security and Servicing updates.

**Security Updates (Only) servicing phase** \- After a new version is released, support for older branches reduces to Security updates only for the remainder of the twelve (12) month Servicing Updates support lifecycle.

> [!NOTE]
> The latest version is always in the Servicing and Critical Updates servicing phase. This means that in the event that you encounter a code defect that warrants a critical update, you must have the latest version installed in order to receive a fix. All other supported versions will only be eligible to receive security updates.

All support ends after the twelve (12) month lifecycle for a version has expired or if more than two updates have been released since then. Then, customers must update to a supported version.

All releases are listed in the [Microsoft Teams Rooms release notes](srs2-release-note.md).

# OS Version support
Windows 10 feature updates for devices running Microsoft Teams Rooms are not offered for six months from the time when Windows makes a release update. This is accomplished by putting a special block for Microsoft Teams Rooms devices on Windows Update for Business channel (that is, Semi-Annual Channel) and through the app settings. During this blocked period Microsoft performs various tests both in-house and through our device OEM partners to make sure that new Windows 10 feature release is working in harmony with the Microsoft Teams Rooms app and peripherals connected to it. This is important to both ensure device security, consistent user experience and to make sure quality of experiences offered through Microsoft Teams Rooms app. 

From the time block is lifted (that is, Window 10 feature update is offered to download on these devices), Microsoft Teams Rooms supports the specific Windows 10 feature release for 12-month period in line with App support policy. Since Windows 10 feature updates are offered about every six months, this also means that Microsoft Teams has two more releases to test by the time support for current version is ended. This also means that a Windows 10 version is unblocked every six months to all Microsoft Teams Rooms customers. The app is continuously changing and developed against the last unblocked Windows release. To ensure that you get the app fix for an issue you encounter on your Microsoft Teams Rooms device, we urge all customers to upgrade these devices to the latest Windows 10 feature update offered to stay within supported windows version guidance.

As such, Microsoft Teams Rooms devices require Windows 10 version 1709 as the minimum supported version starting May 2019. No new app releases are offered to systems on Windows 10 Versions 1703 or below.

> [!NOTE]
> When a Microsoft Teams Rooms device is compatible with the next version of Windows 10 OS, the device automatically updates to the next version through Windows Update. Microsoft Teams Rooms devices should not be upgraded to the next release of Windows 10 manually or via enabling Windows Update for Business (WUFB) group policies using the “Select the Windows readiness level for the updates you want to receive” and "Select when Preview Builds and Feature Updates are received" options through a GPO. Enabling these group policies is known to lead to issues between Windows 10 OS update and the Microsoft Teams Rooms app. 
 
<a name="See"> </a> 
## See also

[Microsoft Teams Rooms help](https://support.office.com/en-us/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2)

[Microsoft Teams Rooms release notes](srs2-release-note.md)

[Plan for Microsoft Teams Rooms](skype-room-systems-v2-0.md)
