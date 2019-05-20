---
title: "Release notes"
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
description: "This article discusses cumulative improvements in Microsoft Teams Rooms."
---

# Release notes 

This article discusses cumulative improvements in Microsoft Teams Rooms.


##  Version history

| Release | Published to <br>Microsoft Store | 
| ---     | ---  |
| 4.0.78.0 | 03/14/2019   |
| 4.0.76.0 | 03/04/2019   |
| 4.0.64.0 | 12/14/2018   |
| 4.0.51.0 | 11/17/2018   | 
| 4.0.31.0 | 10/16/2018   | 
| 4.0.27.0 |  10/1/2018    | 
| 4.0.19.0 |  08/31/2018    |   
| 4.0.18.0 |  08/27/2018    |   
| 4.0.8.0 |  07/06/2018    |   
| 3.1.115.0|  06/18/2018    |
| 3.1.113.0|  06/13/2018    |   
| 3.1.112.0|  06/05/2018    |   
| 3.1.104.0|  04/16/2018    |            
| 3.1.100.0|  03/16/2018    |            
| 3.1.99.0 | 3/14/2018      |  
| 3.1.98.0    | 3/8/2018    |   
|  3.0.16.0    |  11/27/2017   |
| 3.0.15.0 | 10/3/2017  |            
| 3.0.12.0 |  9/1/2017  |            
| 3.0.8.0 | 11/16/2017 | 
| 3.0.6.0 | 11/16/2017 | 
| 2.0.2.0  | 03/15/2017 | 
| RTM (1.0.8) | 12/7/2016  | 


## Microsoft Teams Rooms feature introduction and issue resolution


### 4.0.78.0 (03/14/2018)
Introduced in this update:
- Fix for "hang at app start up" bug that impacted devices on legacy Windows 10 RS2 build.  


### 4.0.76.0 (03/04/2019)
Introduced in this update:
- DTMF keypad for Microsoft Teams P2P meetings and PSTN calls. To make Microsoft Teams your default calling client, admins must set IsTeamsDefaultClient to true
- Pin a remote participant's incoming video to full screen on front of room display. Use "Pin" command from participant roster on the  console
- Improvements to Lobby notifications with addition of Front of Room notification
- Front of Room display removes casting icon when Bluetooth beacon is not enabled on Room system device
- Fix for volume control issue in Teams meetings


### 4.0.64.0 (12/14/2018)
Introduced in this update:
- Display content on both Front of Room (FoR) displays on dual screen room systems
- Theming and Front of Room user interface improvements
- TLS 1.2 client side support. For on premise customers, enabling communciation over TLS 1.2 for Microsoft Teams Rooms requires Skype for Business Server 2015 Cummulative Update 9 (CU9) or Skype for Buisness Server 2019 Cummulative Update 1 (CU1).

### 4.0.51.0 (11/17/2018)
Introduced in this update:
- Dual display (Front of Room) support for Teams Meetings 

### 4.0.31.0 (10/16/2018)
Introduced in this update:
- Quality and reliability fixes 

### 4.0.27.0 (10/1/2018)
Introduced in this update: 
- Code changes necessary to prepare the Microsoft Teams Rooms app for later Windows 10 Version 1803 upgrade
- Fix formatting issue with localized EULAs - specifically Norwegian - which prevents advancing beyond EULA OOBE setup window
- Code changes required to make Microsoft Teams Rooms application run on legacy Lync Room Systems. See more [here](https://aka.ms/lrsupgrade).
 

### 4.0.19.0 (8/31/2018)
Introduced in this update: 
- Hotfix for Crestron application not launching which would normally be accessible by pressing the app button on Crestron SR devices. Microsoft Teams Rooms app restart required after installation of 4.0.19.0. 

### 4.0.18.0 (08/27/2018)
Introduced in this update: 
- "Report a Problem" feature improvements in Teams mode (equivalent of "Give Feedback" in Skype for Business mode)
- Enable ability to fallback from Teams to Skype for Business mode for SIP calls
- Accessibility improvements (Narrator, Magnifier)
- Automatically restart app when required after XML provisioning changes have been applied
- Miscellaneous fixes

### 4.0.8.0 (07/06/2018)
Introduced in this update: 
- This update enables both Skype for Business *and* Teams meetings support on Room Systems devices.  Teams is turned off by default once the update is applied.  Admins can enable Teams locally in device settings or via a remote xml push.

### 3.1.115.0 (06/18/2018)
Introduced in this update: 
- Fix to address error observed on some systems during app launch.

### 3.1.113.0 (06/13/2018)
Introduced in this update: 
- Changes enabling Microsoft to more flexibly manage Windows Updates.
- No change to end-user experience.

### 3.1.112.0 (06/05/2018)
Introduced in this update: 
- Fix to address console responsiveness issues observed on Surface Pro 2017-based devices connected to two front-of-room displays and video ingest
- Automated check to ensure that system is running latest provisioning script.

### 3.1.104.0 (04/16/2018)
Introduced in this update: 
- Fix to improve OSK (on-screen keyboard) behavior in Window 10 Version 1709-based systems
- Improvements to prepare for future operating system updates

### 3.1.100.0 (03/16/2018)
Introduced in this update:  
- Application updated to improve telemetry.

### 3.1.99.0 (03/14/2018)
Introduced in this update: 
- Fixes an issue where intermittent meeting join issues may occur.
- Fixes an issue known to result in a device "hang" experience.

### 3.1.98.0  (3/8/2018)
Introduced in this update: 
- Bug/Crash fixes to improve stability
- Support for variable-sized console
- Peripheral audio processing offloading (additional media whitelisting)
- Optimizations which will enable IT Pros to build do-it-yourself images with Windows 10 Version 1709 January Update and later.  

<!--### 3.1.97.0 (00/00/0000)
Introduced in this update:  
- Support for [Lenovo Hub 500](https://www3.lenovo.com/us/en/hub500)  hardware only.  -->


### 3.0.16.0 (11/27/2017)
Introduced in this update:  
- Fixes an issue with the "Give Feedback" feature.

### 3.0.15.0 (10/3/2017)
Introduced in this update: 
- Support for [Polycom MSR Series](http://www.polycom.com/hd-video-conferencing/microsoft-video/msr-series.mdl) dock hardware
- Support for the [Logitech Brio](https://www.logitech.com/en-us/product/brio)
- Resolves an issue where displays (console and front-of-room) fail to enter sleep mode when there is no activity in the room.


### 3.0.12.0 (9/1/2017)
Introduced in this update:   
- Runs on a Surface Pro (2017) tablet  
- Supports Windows 10 Enterprise Creator's Update (English language, build 1703)    
- Support for [Crestron SR](http://www.crestron.com/products/line/sr-for-skype-for-business-room-system) dock hardware    
- OEM Support for Environment Controls (Crestron)
    
The 64-bit version of Windows 10 Enterprise Anniversary edition (English language, version 1607) is no longer supported as of Microsoft Teams Rooms release 3.0.12.0 (update 3). 

### 3.0.8.0 (8/4/2017) 
Introduced in this update: 
- Resolves issues observed when searching for federated users through the Participants search field. Previous to this fix, search results for external federated users may not have resolved correctly and instead returned incorrect results. 

### 3.0.6.0 (7/7/2017) 
Introduced in this update: 
- Dual-Screen support (for legacy system parity)   
- Themability (built-in themes and the ability to set custom theme) 
- Ability to Give Feedback for public builds     
- Improved Telemetry around meeting join reliability     
- Additional OMS reporting     
- Ability for IT Admin to configure devices remotely 
    <!--  - Front-of-Room UX shows room details pre-meeting U2  --> 


### 2.0.2.0 (03/15/2017)
Introduced in this update: 
- In-app user selection of meeting room audio and video USB devices
- Integrated room console status reporting for customers using Microsoft Operations Management Suite, now Azure Monitor  

### Release to Market  (12/7/2016)
**Feature(s):** 

 **Built for Skype for Business**
  
- One-touch join of Skype Meetings    
- Skype Meeting experience optimized for rooms with screen-filling HD video and HD wideband audio
- All participants can connect to the Skype Meeting using their device of choice from wherever they may be located
- Invite people from your directory where you can instantly see their availability or via a phone call
- Supports Skype for Business PSTN Conferencing and PSTN Calling to replace the stand-alone conference phone in your room
    
  **Transform Any Meeting Room**
  
- Dedicated Skype Meeting app optimized for center of table touch controller and large front of room display
- Re-use existing investments in your front of room display or projectors
- Works in all types of meeting spaces from huddle spaces to large conference rooms
- Certified Skype for Business audio and video devices are available for various room sizes
- Built-in wired ingest for to project desktop sharing to the room and to the Skype Meeting
    
  **Easy to Deploy, Simple to Manage**
  
- Always-on appliance that will automatically wake up the displays when it detects people in the room
- Simple deployment and updating of the UWP (Universal Windows Platform) Skype Meeting App
- Windows AppLocker locks down the device to the Skype Meeting app
- Monitored and managed as a Windows 10 Enterprise device via Intune and SCCM (MDM)
- Enterprise-grade reliability
- Low training effort of end-users due to familiar Skype user interface
- Runs on Surface Pro 4 tablet
 

<a name="See"> </a>  
## See also

[Microsoft Teams Rooms help](https://support.office.com/en-us/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2)

[Prepare your environment](srs-v2-prep.md)

[Support for Microsoft Teams Rooms current branch versions](srs2-lifecycle-support.md)

[Known issues for Microsoft Teams Rooms](known-issues.md)

[Plan for Microsoft Teams Rooms](skype-room-systems-v2-0.md)

[Manage Microsoft Teams Rooms](skype-room-systems-v2.md)
