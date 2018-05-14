---
title: "Release notes"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 4/17/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "This article discusses cumulative improvements in Skype Room Systems v2."
---

# Release notes 

This article discusses cumulative improvements in Skype Room Systems v2.


##  Version history

| Release | Published to <br>Microsoft Store | 
| ---     | ---                              |
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



## Skype Room Systems v2 feature introduction and issue resolution


### 3.1.104.0 (04/16/2018)
**New feature(s)** introduced in this update: 
- Fix to improve OSK (on-screen keyboard) behavior in Window 10 Version 1709-based systems
- Improvements to prepare for future operating system updates


### 3.1.100.0 (03/16/2018)
**New feature(s)** introduced in this update: 
- Application updated to improve telemetry.

### 3.1.99.0 (03/14/2018)
**New feature(s)** introduced in this update: 
- Fixes an issue where intermittent meeting join issues may occur.
- Fixes an issue know to result in a device "hang" experience.

### 3.1.98.0  (3/8/2018)
**New feature(s)** introduced in this update: 
- Bug/Crash fixes to improve stability
- Support for variable-sized console
- Peripheral audio processing offloading (additional media whitelisting)
- Also includes optimizations which will enable IT Pros to build do-it-yourself images with Windows 10 Version 1709 January Update and later.  

<!--### 3.1.97.0 (00/00/0000)
**New feature(s)** introduced in this update: 
- Support for [Lenovo Hub 500](https://www3.lenovo.com/us/en/hub500)  hardware only.  -->


### 3.0.16.0 (11/27/2017)
**New feature(s)** introduced in this update: 
- Fixes an issue with "Give Feedback" feature.

### 3.0.15.0 (10/3/2017)
**New feature(s)** introduced in this update: 
- Support for [Polycom MSR Series](http://www.polycom.com/hd-video-conferencing/microsoft-video/msr-series.mdl) dock hardware
- Support for the [Logitech Brio](https://www.logitech.com/en-us/product/brio)
- [10:52 AM] David Groom
- resolves an issue where displays (console and front-of-room) fail to enter sleep mode when there is no activity in the room.


### 3.0.12.0 (9/1/2017)
**New feature(s)** introduced in this update:  
- Runs on Surface Pro (2017) tablet  
- Supports Windows 10 Enterprise Creator's Update (English language, build 1703)    
- Support for [Crestron SR](http://www.crestron.com/products/line/sr-for-skype-for-business-room-system) dock hardware    
- OEM Support for Environment Controls (Crestron)
    
The 64-bit version of Windows 10 Enterprise Anniversary edition (English language, version 1607) is no longer supported as of Skype Room Systems v2 release 3.0.12.0 (update 3). 

### 3.0.8.0 (8/4/2017) 
**New feature(s)** introduced in this update: 
- Resolves issues observed when searching for federated users through the Participants search field. Previous to this fix, search results for external federated users may not have resolved correctly and instead returned incorrect results. 

### 3.0.6.0 (7/7/2017) 
**New feature(s)** introduced in this update:  
- Dual-Screen support (for legacy system parity)   
- Themability (built-in themes and the ability to set custom theme) 
- Ability to Give Feedback for public builds     
- Improved Telemetry around meeting join reliability     
- Additional OMS reporting     
- Ability for IT Admin to configure devices remotely 
    <!--  - Front-of-Room UX shows room details pre-meeting U2  --> 


### 2.0.2.0 (03/15/2017)
**New feature(s)** introduced in this update: 
- In-app user selection of meeting room audio and video USB devices
- Integrated room console status reporting for customers using Microsoft Operations Management Suite (see [Plan 
Skype Room Systems v2 management with OMS](oms-management.md)) 

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


#### 
[Skype Room Systems version 2 help](https://support.office.com/en-us/article/Skype-Room-Systems-version-2-help-e667f40e-5aab-40c1-bd68-611fe0002ba2)

[Prepare your Skype for Business Environment](srs-v2-prep.md)

[Support for Skype Room Systems v2 current branch versions](srs2-lifecycle-support.md)

[Known issues for Skype Room Systems v2](../../manage/skype-room-systems-v2/known-issues.md)

[Plan for Skype Room Systems v2](skype-room-systems-v2-0.md)

[Manage Skype Room Systems v2](../../manage/skype-room-systems-v2/skype-room-systems-v2.md)
#### 
