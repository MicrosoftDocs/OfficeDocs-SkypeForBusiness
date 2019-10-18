---
title: "Manage Windows Updates for Microsoft Teams Rooms"
ms.author: jambirk
author: jambirk
ms.reviewer: sohailta
manager: serdars
ms.date: 10/10/2018
audience: ITPro
ms.topic: article
ms.service: msteams
localization_priority: Normal
ms.collection: 
  - M365-collaboration
ms.assetid: 
description: "Manage Windows Updates for Microsoft Teams Rooms"
---

# Manage Windows Updates

Microsoft Teams Rooms runs on Windows 10 Enterprise IoT or Windows 10 Enterprise (VL) and receives the same Windows Updates and OS builds as a standard desktop computer.

Windows Updates can be managed as discussed in the following sections:

## Hands-off approach 

- By default, updates are downloaded directly from Windows Updates automatically and installed during off-hours.
- Non-deferrable Updates install day-one of release automatically.
- Quality Updates and drivers download and install day-one automatically.
- Feature Updates. See the notes that follow.

## Windows Updates for Business (GPO or Intune)  

- [Windows Updates for Business](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-wufb) download
- Updates are downloaded from Windows Update or your WSUS but with configured delays past the original release date.
- You can use multiple OUs or filtered policies to create deployment “rings” where administrators can specify which devices install Quality Updates first and which ones install later. Reliability and performance can be tested on a subset of systems before rolling out updates across the entire deployment without the overhead of managing Windows Updates in SCCM.
- WSUS and Windows Updates for Business can be [configured at the same time](https://docs.microsoft.com/windows/deployment/update/waas-integrate-wufb) if you desire both the bandwidth management and the control Windows Updates for Business provides.
- Feature updates. See the notes that follow.

## WSUS/SCCM

- [WSUS/SCCM](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-configuration-manager) download
- Much like Windows Update for Business, but with the additional option of targeting specific KB's within each "ring" or the entire deployment. Each Update can be individually deployed and tested at will, rather than relying on only a delay.
- Feature updates. See the notes that follow.

### Feature updates

Unlike Quality and Non-Deferrable updates, Windows 10 "Feature Updates" (major OS releases) will only be installed after Microsoft tests and validates a given updates functionality with Microsoft Teams Rooms. Even if the update is released to the Semi-Annual Channel (or Targeted if you have systems set to that channel for testing) or manually pushed, a Microsoft Room Systems device won't allow the untested update to install.

Microsoft Teams Rooms functions "out-of-box" with a hands-off approach, and will not install a Windows Update or reboot a device automatically for a Windows Update. Systems download an update and wait for the next reboot to install it. Unless someone reboots it manually, installation only happens at the automatic nightly reboot. Windows Updates should be transparent in the room, and normal operation should never be interrupted by Windows Updates.

If you choose to domain join devices, use SCCM or WSUS. Pay special attention to policies or actions that result in a device update or forced reboot during business hours. Systems in your deployment should not reboot during use or alert about Windows Updates over the UI during usage hours, review your configuration if that behavior happens.