---
title: "Known issues"
ms.author: v-lanac
author: lanachin
ms.reviewer: davgroom
manager: serdars
ms.date: 4/17/2018
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: M365-voice
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


<a name="OS-conflicts"> </a>  
## User interface 

| Issue title |  Behavior \/ Symptom | Known workaround | KB Article |
|  ---        |      ---             |   ---            | --- |
|Virtual keyboard missing   | The virtual keyboard doesn't appear when you need to enter information in Microsoft Teams Rooms. This issue occurs after the Windows 10 Creators Update (version 1703) is installed on the Surface Pro 4 on which Microsoft Teams Rooms is running. | To work around this issue, manually open the virtual keyboard. To do this, follow these steps:<br><br> **1.** Tap and hold the task bar, and then tap **Show touch keyboard** button. A keyboard icon should appear on the right side of the task bar. <br><br> **2.** Tap the keyboard icon to open the virtual keyboard. | [KB4037694](https://support.microsoft.com/en-us/help/4037694/virtual-keyboard-missing-in-skype-room-systems-v2) | 
   

<a name="Hardware"> </a>  
## Hardware

| Issue title |  Behavior \/ Symptom | Known workaround | KB Article |
|  ---        |      ---             |   ---            |   --- |
| Monitors not detected | When you run Microsoft Teams Rooms on a Surface Pro (Model 2017) device, monitors are not detected. |  Hold down the Surface Pro power button for 20 or more seconds. When you do this, the device restarts and clears the graphics cache. |[KB4055681](https://support.microsoft.com/en-us/help/4055681/monitors-are-not-detected-when-you-run-skype-room-systems-on-a-surface)       | 
          
<a name="Limits"> </a>
## Limitations and expected behaviors
***
Microsoft Teams Rooms does not support HDCP input, which has been observed to cause issues with HDMI ingest functionality (video, audio). Take care to ensure that switches connected to Microsoft Teams Rooms have HDCP options turned off. 
***
A consumer TV used as a front of room display needs to support/enable the Consumer Electronics Control (CEC) feature of HDMI so that it can switch automatically to an active video source from standby mode. This feature is not supported on all TVs. 
***
Always use a wired 1 Gbps network connection to assure you will have the needed bandwidth. 
***
If your Microsoft Teams Rooms device loses trust with the domain (for example, if you remove the Microsoft Teams Rooms from the domain after it is domain joined), you won't be able to authenticate into the device and open up Settings. The workaround is to log in with the local Admin account. 
***
The 64-bit version of Windows 10 Enterprise Anniversary edition (English language, version 1607) is no longer supported as of Microsoft Teams Rooms release 3.0.12.0. 
***
Microsoft Teams Room is a multi-window application and requires a front of room display to be connected to the HDMI port of the device, for the app to function correctly. Make sure you either have an HDMI display connected or use a dummy HDMI plug if you are testing and do not have a display purchased yet.
***
<a name="See"> </a>  
## See also

[Microsoft Teams Rooms help](https://support.office.com/en-us/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2)

[Manage Microsoft Teams Rooms](skype-room-systems-v2.md)
