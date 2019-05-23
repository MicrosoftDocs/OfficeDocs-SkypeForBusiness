---
title: "Manage Windows Updates for Microsoft Teams Rooms"
ms.author: jambirk
author: jambirk
ms.reviewer: davgroom
manager: serdars
ms.date: 10/10/2018
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: M365-voice
ms.assetid: 
description: "Manage Windows Updates for Microsoft Teams Rooms"
---

# Manage Windows Updates

Microsoft Teams Rooms runs on Windows 10 Enterprise IoT or Windows 10 Enterprise (VL) and receives the same Windows Updates and OS builds as a standard desktop.

Windows Updates can be managed in a few different ways:

## Hands-off approach 
- Updates can be downloaded directly from Windows Updates automatically and installed during off-hours. If no change is made to configuration this is the default state.
- Non-deferrable Updates will install day-one of release automatically. 
- Quality Updates and drivers will download and install day-one automatically. 
- Feature Updates. See additional notes below. 

## [Windows Updates for Business](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-wufb) (GPO or Intune)   
- Updates are downloaded from WU or your WSUS but with configured delays past the KB’s original release date. 
- Combined with multiple OU’s or filtered policies, this allows for the creation of deployment “rings”, where administrators can specify which devices install Quality Updates first and which ones will install later. This allows for reliability and performance testing on a subset of systems before rolling out updates across the entire deployment without the overhead of managing Windows Updates in SCCM for example.
- WSUS and Windows Updates for Business can be [configured at the same time](https://docs.microsoft.com/windows/deployment/update/waas-integrate-wufb) if you desire both bandwidth management and the control Windows Updates for Business provides.
- Feature updates. See additional notes below.

## [WSUS/SCCM](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-configuration-manager)
- Much like Windows Update for Business, but with the additional option of targeting specific KB's within each "ring" or the entire deployment. Each Update can be individually deployed and tested at will, rather than relying on only a delay. 
- Feature updates. See additional notes below.


### Feature updates

Unlike Quality and Non-Deferable updates, Windows 10 "Feature Updates" (major OS releases) will only be installed after Microsoft tests and validates a given updates functionality with Microsoft Teams Rooms. Even if it is released to the Semi-Annual Channel (or Targeted if you have systems set to that channel for testing) or even manually pushed by your own attempts or configurations, it will not allow the installation until the block on our end is removed.

Microsoft Teams Room "out-of-box", using the hands off approach, will not install a Windows Update or reboot a device automatically because of a Windows Update. Systems may, however, download an update and wait for the next reboot to install it. Unless someone reboots it manually, installation should happen at the automatic nightly reboot. Windows Updates should be transparent in the room, the UI should never be interrupted by Windows Updates.

If you choose to domain join, use SCCM or WSUS, and please pay special attention to policies or actions that may result in the device installing an update or forcing a reboot during business hours. If you have systems in your deployment rebooting during use or alerting about Windows Updates over the UI, you will want to look into your configuration.