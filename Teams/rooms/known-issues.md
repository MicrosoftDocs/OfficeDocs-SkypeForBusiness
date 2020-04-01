---
title: "Known issues"
ms.author: v-lanac
author: lanachin
ms.reviewer: sohailta
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
f1.keywords:
- NOCSH
localization_priority: Normal
ms.collection: 
  - M365-collaboration
description: "This article discusses known issues for Microsoft Teams Rooms, by feature area."
---

# Known issues 
 
This article lists the known issues for Microsoft Teams Rooms, by feature area.
<!-- If we get word that one of these issues no longer applies, contact meerak@microsoft.com or msmets@microsoft.com and let them know to EoL the corresponding KB  -->

<a name="update"> </a>  
## Update 

| Issue title |  Behavior \/ Symptom | Known workaround | KB Article |
|  ---        |      ---             |   ---            | --- |
|  App out of date         |    The Microsoft Teams Rooms console shows a "system config out of date" error.                |   [Use the Microsoft Teams Rooms recovery tool](recovery-tool.md)             |  None |
|  Device updated to Windows 10 version 1809   |    Device upgraded from Windows 10 1803 to unsupported version 1809 and not upgrading to 1903 |   This can be caused if the [Group Policy or MDM setting for DeferFeatureUpdatesPeriodinDays](https://docs.microsoft.com/en-us/windows/deployment/update/waas-configure-wufb) is set to the maximum of 365 days. Such a setting prevents an 1803 device from taking any newer updates that have not been in market for 365 days. Windows 10 1809 version is not support for Microsoft Teams Rooms, and has been in-market for 365 days as of March 27th, 2020 while version 1903, will not have been in-market until May 20th, 2020. The fix for this situation is to **remove** any Group Policy or MDM settings for deferring updates - this will allow the system to upgrade to the latest, supported OS version. It is imperitive that the Group Policy or MDM setting be **removed** (left completely unconfigured) and **not set to 0**. If the policy is set to 0, the system will take latest available version which may not yet be supported (sucha as 1909). |  None |

<a name="OS-conflicts"> </a>  
## User interface 

| Issue title |  Behavior \/ Symptom | Known workaround | KB Article |
|  ---        |      ---             |   ---            | --- |
|Virtual keyboard missing   | The virtual keyboard doesn't appear when you need to enter information in Microsoft Teams Rooms. This issue occurs in Windows 10 1903. | Install 2020-04 Cummulative Update for Windows 10 version 1903 for x64-based Systems through Windows Updates  | None | 

<a name="Hardware"> </a>  
## Hardware

| Issue title |  Behavior \/ Symptom | Known workaround | KB Article |
|  ---        |      ---             |   ---            |   --- |
| Monitors not detected | When you run Microsoft Teams Rooms on a Surface Pro (Model 2017) device, monitors are not detected. |  Hold down the Surface Pro power button for 20 or more seconds. When you do this, the device restarts and clears the graphics cache. |[KB4055681](https://support.microsoft.com/help/4055681/monitors-are-not-detected-when-you-run-skype-room-systems-on-a-surface)       | 

<a name="Limits"> </a>
## Limitations and expected behaviors

***

Microsoft Teams Rooms does not support HDCP input, which has been observed to cause issues with HDMI ingest functionality (video, audio). Take care to ensure that switches connected to Microsoft Teams Rooms have HDCP options turned off. 

***

If you desire a front of room display to automatically switch to an active video source (such as an MTR console) when the source wakes from standby mode, certain conditions must be met. This feature is optional but supported by Microsoft Teams Rooms software, provided underlying hardware supports the feature. A consumer TV used as a front of room display needs to support the Consumer Electronics Control (CEC) feature of HDMI.  Depending on the dock or console selected (which might not support CEC, refer to manufacturer support documentation), a workspace controller such as an [Extron HD CTL 100](https://www.extron.com/article/hdctl100ad) may be needed to enable the desired behavior. 

***

Always use a wired 1-Gbps network connection to assure you have the needed bandwidth. 

***

If your Microsoft Teams Rooms device loses trust with the domain, you won't be able to authenticate into the device and open up Settings. For example, if you remove the Microsoft Teams Rooms from the domain after it is domain joined, trust is lost. The workaround is to log in with the local Admin account. 
***
The 64-bit version of Windows 10 Enterprise Anniversary edition (English language, version 1607) is no longer supported as of Microsoft Teams Rooms release 3.0.12.0. 
***
Microsoft Teams Rooms is a multi-window application and requires a front of room display to be connected to the HDMI port of the device, for the app to function correctly. Make sure that you either have an HDMI display connected or use a dummy HDMI plug if you are testing and do not have a display purchased yet.
***
<a name="See"> </a>  
## See also

[Microsoft Teams Rooms help](https://support.office.com/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2)

[Manage Microsoft Teams Rooms](rooms-manage.md)
