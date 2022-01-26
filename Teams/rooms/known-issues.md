---
title: "Known issues"
ms.author: dstrome
author: dstrome
ms.reviewer: sohailta
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
description: Admin can learn about a list of known issues for Microsoft Teams Rooms, including update, user interface, hardware, and limitations and expected behaviors.
ms.custom: seo-marvel-apr2020
---

# Known issues 
 
This article lists the known issues for Microsoft Teams Rooms, by feature area.
<!-- If we get word that one of these issues no longer applies, contact meerak@microsoft.com or msmets@microsoft.com and let them know to EoL the corresponding KB  -->

<a name="update"> </a>  
## Update 

| Issue title |  Behavior \/ Symptom | Known workaround | KB Article |
|  ---        |      ---             |   ---            | --- |
| Edge browser automatic launch | The Edge browser prior to build 97.0.1072.62 launches automatically alongside the Microsoft Teams Room app when the device starts. | This should resolve automatically, with no user interaction required, on or before Monday, January 17th 2022. If a faster resolution is required: when Edge launches alongside the Microsoft Teams Room, visit the URL edge://settings/help, and an update should automatically start downloading and applying. Select the browser's "restart" button once the update has finished applying. Close Edge, reboot the system, and the problem should be resolved. | None |
| Split Gallery Participant Video   | In dual Front of Room displays mode, when there is no shared content at a meeting with more than 9 remote video participants, 1 video on a Front of Room display with the self preview might appear as audio due to a known issue. Also, a smaller number of audio participants than the actual number of audio participants shows up on dual Front of Room displays. | Issue will be resolved in future update. | None |
| Application not launching |  After updating to application version 4.4.41.0, the system boots to black screen, or go to the sign-in screen after few minutes. | Follow the steps in [Microsoft Teams Rooms application does not start after update to version 4.4.41.0](/microsoftteams/troubleshoot/teams-administration/teams-rooms-app-wont-start-after-update) to fix this issue.  | None |
|  Low meeting volume after content sharing         |   Microsoft Teams Rooms devices on Windows 10 20H2 experience decreased media and meeting volume after sharing content via in-room HDMI. This is caused by an audio issue in Windows 10 20H2. | The fix for this issue is available in application version [4.9.12.0](/microsoftteams/rooms/rooms-release-note#49120-7282021). | None |
|  App out of date         |    The Microsoft Teams Rooms console shows a "system config out of date" error.                |   [Use the Microsoft Teams Rooms recovery tool](recovery-tool.md)             |  None |
|  Device updated to unsupported version of Windows 10   |    Windows 10 device updated from version 1803 to version 1809, which is not supported. The supported version is 1903. |   This can happen if the [Group Policy or MDM setting for DeferFeatureUpdatesPeriodinDays](/windows/deployment/update/waas-configure-wufb) setting, which lets you defer feature updates for a specified number of days, is set to the maximum of 365 days. <br><br> Windows 10 version 1809 isn't supported with Microsoft Teams Rooms, while version 1903 is supported. However, as of March 27, 2020, version 1809 is over 365 days old. If this setting isn't changed, Windows attempts to install version 1809, which may cause issues with Microsoft Teams Rooms.<br><br>To avoid this situation, **remove** any Group Policy or MDM setting for deferring updates. This allows Windows to update to the latest, supported OS version. <br><br>**IMPORTANT:** The Group Policy or MDM setting must be **removed** (left unconfigured) and **not set to 0**. If the policy is set to 0, Windows takes the latest available version which may not be supported. |  None |



<a name="OS-conflicts"> </a>  
## User interface 

| Issue title |  Behavior \/ Symptom | Known workaround | KB Article |
|  ---        |      ---             |   ---            | --- |
|Virtual keyboard missing   | The virtual keyboard doesn't appear when you need to enter information in Microsoft Teams Rooms. This issue occurs in Windows 10, version 1903. | Install 2020-04 Cumulative Update for Windows 10, version 1903 for x64-based Systems through Windows Updates.  | None | 

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

If you desire a front of room display to automatically switch to an active video source (such as an MTR console) when the source wakes from standby mode, certain conditions must be met. This feature is optional but supported by Microsoft Teams Rooms software, provided underlying hardware supports the feature. A consumer TV used as a front of room display needs to support the Consumer Electronics Control (CEC) feature of HDMI.  Depending on the dock or console selected (which might not support CEC, refer to manufacturer support documentation), a controller such as an [HD-RX-201-C-E](https://www.crestron.com/Products/Video/HDMI-Solutions/HDMI-Extenders/HD-RX-201-C-E) from Crestron or [Extron HD CTL 100](https://www.extron.com/article/hdctl100ad) from Extron may be needed to enable the desired behavior.

In addition, a consumer TV used as the front of room display may cause stability issues with Microsoft Teams Rooms software. This is due to inconsistent implementation of standby modes, active video source selection, and communicating faulty EDID information to the Microsoft Teams Rooms device. Known symptoms are a black/gray screen on the front of room display or the Microsoft Teams Rooms console becoming unresponsive after waking from standby.  If experiencing issues when using consumer TVs, we recommend installing a configurable EDID controller or EDID emulator such as the [HD-RX-201-C-E](https://www.crestron.com/Products/Video/HDMI-Solutions/HDMI-Extenders/HD-RX-201-C-E) from Crestron or [DR-EDID Emulator](https://fsrinc.com/fsr-products/product/dr-edid-manager-learner/category_pathway-143) from FSR Video Products Group.

***

Always use a wired 1-Gbps network connection to assure you have the needed bandwidth. 

***

If your Microsoft Teams Rooms device loses trust with the domain, you won't be able to authenticate into the device and open up Settings. For example, if you remove the Microsoft Teams Rooms from the domain after it is domain joined, trust is lost. The workaround is to log in with the local Admin account. 
***
Microsoft Teams Rooms is a multi-window application and requires a front of room display to be connected to the HDMI port of the device, for the app to function correctly. Make sure that you either have an HDMI display connected or use a dummy HDMI plug if you are testing and do not have a display purchased yet.
***
<a name="See"> </a>  
## See also

[Microsoft Teams Rooms help](https://support.office.com/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2)

[Manage Microsoft Teams Rooms](rooms-manage.md)
