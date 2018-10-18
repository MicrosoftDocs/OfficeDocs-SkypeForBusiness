---
title: "Known issues"
ms.author: jambirk
author: jambirk
ms.reviewer: davgroom
manager: serdars
ms.date: 4/17/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "This article discusses known issues for Skype Room Systems v2, by feature area."
---

# Known issues 
 
This article lists the known issues for Skype Room Systems v2, by feature area.
<!-- If we get word that one of these issues no longer applies, contact meerak@microsoft.com or msmets@microsoft.com and let them know to EoL the corresponding KB  -->

<a name="update"> </a>  
## Update 

| Issue title |  Behavior \/ Symptom | Known workaround | KB Article |
|  ---        |      ---             |   ---            | --- |
|  App out of date         |    The Skype Room Systems v2 console shows a "system config out of date" error.                |   [Use the Skype Room Systems v2 recovery tool](recovery-tool.md)             |  None |


<a name="OS-conflicts"> </a>  
## User interface 

| Issue title |  Behavior \/ Symptom | Known workaround | KB Article |
|  ---        |      ---             |   ---            | --- |
|Virtual keyboard missing   | The virtual keyboard doesn't appear when you need to enter information in Skype Room Systems v2. This issue occurs after the Windows 10 Creators Update (version 1703) is installed on the Surface Pro 4 on which Skype Room Systems v2 is running. | To work around this issue, manually open the virtual keyboard. To do this, follow these steps:<br><br> **1.** Tap and hold the task bar, and then tap **Show touch keyboard** button. A keyboard icon should appear on the right side of the task bar. <br><br> **2.** Tap the keyboard icon to open the virtual keyboard. | [KB4037694](https://support.microsoft.com/en-us/help/4037694/virtual-keyboard-missing-in-skype-room-systems-v2) | 
   

<a name="Hardware"> </a>  
## Hardware

| Issue title |  Behavior \/ Symptom | Known workaround | KB Article |
|  ---        |      ---             |   ---            |   --- |
| Monitors not detected | When you run Skype Room Systems v2 on a Surface Pro (Model 2017) device, monitors are not detected. |  Hold down the Surface Pro power button for 20 or more seconds. When you do this, the device restarts and clears the graphics cache. |[KB4055681](https://support.microsoft.com/en-us/help/4055681/monitors-are-not-detected-when-you-run-skype-room-systems-on-a-surface)       | 
          
<a name="Limits"> </a>
## Limitations and expected behaviors
***
Skype Room Systems v2 does not support HDCP input, which has been observed to cause issues with HDMI ingest functionality (video, audio). Take care to ensure that switches connected to Skype Room Systems v2 have HDCP options turned off. 
***
A consumer TV used as a front of room display needs to support/enable the Consumer Electronics Control (CEC) feature of HDMI so that it can switch automatically to an active video source from standby mode. This feature is not supported on all TVs. 
***
Always use a wired 1 Gbps network connection to assure you will have the needed bandwidth. 
***
If your Skype Room Systems v2 device loses trust with the domain (for example, if you remove the Skype Room Systems v2 from the domain after it is domain joined), you won't be able to authenticate into the device and open up Settings. The workaround is to log in with the local Admin account. 
***
The 64-bit version of Windows 10 Enterprise Anniversary edition (English language, version 1607) is no longer supported as of Skype Room Systems v2 release 3.0.12.0. 
***

<a name="See"> </a>  
## See also

[Skype Room Systems version 2 help](https://support.office.com/en-us/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2)

[Manage Skype Room Systems v2](skype-room-systems-v2.md)