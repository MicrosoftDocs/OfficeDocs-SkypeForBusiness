---
title: "Skype Room Systems v2 requirements"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 2/16/2018
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6b2b2684-8e9e-49ea-8c46-1c690964f982
description: "This article summarizes the requirements for supporting a Skype Room Systems v2."
---

# Skype Room Systems v2 requirements
[]
This article summarizes the requirements for supporting a Skype Room Systems v2. 
  
Your deployment will involve account creation as described in [Deploy Skype Room Systems v2](../../deploy-1/deploy-clients/room-systems-v2.md) and setting up a meeting console as described in[Configure a Skype Room Systems v2 console](../../deploy-1/deploy-clients/console.md). You may also need to refer to [Skype for Business add-on licensing](https://support.office.com/en-US/article/Skype-for-Business-add-on-licensing-3ed752b1-5983-43f9-bcfd-760619ab40a7).
  
## Hardware requirements

Skype Room Systems v2 can scale to different room sizes through accessories depending on audio and video peripherals. Audio and video peripherals connect to Skype Room Systems v2 via a USB or HDMI connection on the docking device. You will also need:
  
- An 8GB or larger USB disk you will configure as bootable Windows installation media for Windows 10 Enterprise. 
    
- One of the following tablets:
    
   **Supported tablets**

|
|
|**Tablet**|**Processor**|**RAM**|**Disk**|
|:-----|:-----|:-----|:-----|
|Surface Pro 4 \*  <br/> |Core i5  <br/> |4GB  <br/> |128GB  <br/> |
|Surface Pro 4 \*  <br/> |Core i5  <br/> |8GB  <br/> |256GB  <br/> |
|Surface Pro § <br/> |Core i5  <br/> |4GB  <br/> |128GB  <br/> |
|Surface Pro § <br/> |Core i5  <br/> |8GB  <br/> |256GB  <br/> |
|Surface Pro § <br/> |Core i7  <br/> |8GB  <br/> |128GB  <br/> |
|Surface Pro § <br/> |Core i7  <br/> |16GB  <br/> |512GB  <br/> |
|Surface Pro § <br/> |Core i7  <br/> |16GB  <br/> |1TB  <br/> |
   
    \* — Core M3 processors are not supported on this model.
    
    § — Core M3 processors are not supported on this model.
    
- One of the following docking station options to secure the tablet to the meeting room table. 
    
  - [Logitech SmartDock](https://www.logitech.com/en-us/product/smartdock)
    
  - [Crestron SR](http://www.crestron.com/products/line/sr-for-skype-for-business-room-system )
    
  - [Polycom MSR Series](http://www.polycom.com/hd-video-conferencing/microsoft-video/msr-series.mdl)
    
- 
   **Certified firmware versions for USB audio and video peripherals**

|
|
|**Skype Room Systems v2 peripherals**|**Firmware version certified for Skype Room Systems v2**|
|:-----|:-----|
|[Logitech BRIO](https://www.logitech.com/en-us/product/brio) <br/> ||
|[Logitech MeetUp](http://www.logitech.com/en-us/product/meetup-conferencecam) <br/> |Audio - 1.0.172  <br/> Video - 1.0.156  <br/> |
|[Logitech ConferenceCam Connect](http://www.logitech.com/en-us/product/conferencecam-connect) <br/> |1.1.248.0  <br/> 1.1.684  <br/> |
|[Logitech Group](http://www.logitech.com/en-us/product/conferencecam-group) <br/> |8.5.778  <br/> |
|[Logitech 930e](http://www.logitech.com/en-us/product/c930e-webcam) <br/> | 8.0.914 <br/> |
|[Logitech PTZ Pro](http://www.logitech.com/en-us/product/conferencecam-ptz-pro) <br/> | 1.1.219 <br/> |
|[Polycom RealPresence Trio](http://www.polycom.com/voice-conferencing-solutions/conference-phones/realpresence-trio.mdl) <br/> |5.4.4.7511  <br/> |
|[Polycom EagleEye IV](http://www.polycom.com/products-services/hd-telepresence-video-conferencing/realpresence-accessories/eagleeye-cameras.mdl) <br/> |1.0.0  <br/> |
|[Polycom CX5100](http://www.polycom.com/products-services/products-for-microsoft/lync-optimized/cx5100-unified-conference-station.mdl) <br/> | 1.2.0.70232 <br/> |
|[Sennheiser SP 220 MS](http://no-no.sennheiser.com/dual-speakerphones-sp-220-ms-uc) <br/> |2.0.12.0  <br/> |
|[Sennheiser SP20](http://en-us.sennheiser.com/sp-20-og-sp-20-ml) <br/> |1.2.15  <br/> |
|[Jabra 510](http://www.jabra.com/support/Jabra-SPEAK™-510_7510-209) <br/> |2.10.0  <br/> |
|[Jabra 710](http://www.jabra.com/business/speakerphones/jabra-speak-series/jabra-speak-710) <br/> |1.8.0  <br/> |
|[Jabra 810](http://www.jabra.com/supportpages/jabra-speak-810) <br/> |1.2.23  <br/> |
|[Yamaha YVC-1000](http://www.yamaha.com/products/en/communication/usb_conference_speakerphones/yvc-1000/) <br/> |100c  <br/> |
   
- **USB extenders**:
    
  - USB ports on tablet docks are USB 3.0 compatible. You can use a USB 2.x extender, but doing so will limit you to USB 2.x speeds on the far end and doing so is not recommended for USB 3.0 peripherals.
    
  - An extender must meet USB 2.0 or newer specifications.
    
  - Tablet docks support at least two stages of external USB hub extension. If need to connect more than two USB hubs in series, you will need to check with the dock manufacturer to confirm doing so is supported.
    
- Wired GbE connection in the room. Ethernet cable of appropriate length.
    
- Up to two 1080p displays with HDMI connections. HDMI cables of appropriate length.
    
    > [!NOTE]
    > A consumer TV used as a front of room display needs to support/enable the Consumer Electronics Control (CEC) feature of HDMI so that it can switch automatically to an active video source from standby mode. This feature is not supported on all TVs. 
  
> [!NOTE]
> Skype Room Systems v2 does not use a keyboard. If needed, the Admin should use the on-screen keyboard. A USB keyboard or mouse will be required when imaging the Skype Room Systems v2 device. 
  
The following tables provide recommendations for peripherals based on room size:
  
**Skype Room Systems v2 Certified Audio Peripherals**

|**Room Type**|**Number of People**|**Recommended maximum distance from microphone to person speaking**|**Device by maximum room size**|**Comments**|
|:-----|:-----|:-----|:-----|:-----|
|**Focus** <br/> 10' x 9'  <br/> |2-4  <br/> |1.5m  <br/> |Logitech Connect  <br/> |The Logitech Connect devices include a camera so it must be positioned at the front of the room (not center of table) to capture local meeting attendees.  <br/> |
|**Small** <br/> 16' x 16'  <br/> |4-6  <br/> |2.0m  <br/> |Jabra 510  <br/> Sennheiser SP20  <br/> |Playback volume may be limited for larger rooms.  <br/> |
|**Medium** <br/> 18' x 20'  <br/> |6-12  <br/> |2.4m  <br/> |Jabra 710  <br/> Jabra 810  <br/> Logitech MeetUp  <br/> Logitech Group  <br/> Polycom Trio  <br/> Polycom CX5100  <br/> Sennheiser SP 220 MS  <br/> Yamaha YVC-1000MS  <br/> |The Logitech MeetUp includes a camera so it must be positioned at the front of room (not center of table to capture local meeting attendees).  <br/> In general, rooms with long rectangular or u-shaped tables may benefit from additional satellite microphones.  <br/> SP 220 MS must be used in daisy-chain configuration.  <br/> |
|**Large** <br/> 15' x 20'  <br/> |12-16  <br/> |3m  <br/> This distance also applies to the area covered by each additional satellite microphone connected to the audio device in question.  <br/> |Logitech Group + satellite mics  <br/> Polycom Trio+ satellite mics  <br/> Polycom CX5100 + satellite mics  <br/> Sennheiser SP 220 MS  <br/> Yamaha YVC-1000MS + satellite mics  <br/> |All audio devices listed in this row support satellite microphone options.  <br/> CX5100 includes a built-in 360 degree camera so that the device can be positioned in the center of table.  <br/> SP 220 MS must be used in daisy-chain configuration.  <br/> |
   
**Skype Room Systems v2 Certified Video Peripherals**

|**Room Type**|**Number of People**|**Device by Optimal room size**|**Comments**|
|:-----|:-----|:-----|:-----|
|**Focus** <br/> 10' x 9'  <br/> |2-4  <br/> |Logitech Connect  <br/> Logitech MeetUp  <br/> Polycom CX5100  <br/> ||
|**Small** <br/> 16' x 16'  <br/> |4-6  <br/> |Logitech C930e  <br/> Logitech MeetUp  <br/> Logitech BRIO  <br/> Logitech PTZ Pro  <br/> Polycom MSR  <br/> Polycom CX5100  <br/> |Logitech PTZ Pro often bundled with Logitech Group  <br/> |
|**Medium** <br/> 18' x 20'  <br/> |6-12  <br/> |Logitech MeetUp  <br/> Logitech BRIO  <br/> Logitech PTZ Pro  <br/> Polycom MSR  <br/> Polycom CX5100  <br/> ||
|**Large** <br/> 15' x 20'  <br/> |12-16  <br/> |Logitech PTZ Pro  <br/> Polycom MSR  <br/> Polycom CX5100  <br/> ||
   
## Required Software Downloads

You will need the following downloads to build your own Skype Room Systems v2 image:
  
- The [Skype Room Systems v2 installation package](https://go.microsoft.com/fwlink/?linkid=851168).
    
- Obtain a copy of the 64-bit version of Windows 10 Enterprise Creator's Update (English language, build 1703). 
    
    > [!NOTE]
    > The 64-bit version of Windows 10 Enterprise Anniversary edition (English language, version 1607) is no longer supported as of Skype Room Systems v2 release 3.0.12.0 (update 3). 
  
- The supported [Surface Pro 4 drivers](https://go.microsoft.com/fwlink/?linkid=856887) or[Surface Pro drivers](https://go.microsoft.com/fwlink/?linkid=856888).
    
These downloads need to be combined into a bootable Windows installation media disk in a specific way, described further in [Configure a Skype Room Systems v2 console](../../deploy-1/deploy-clients/console.md). 
  
In addition, you will probably want a copy of the [Powershell script](http://download.microsoft.com/download/9/0/D/90D4826A-9FD2-47D2-B911-97BF1737F4F7/SkypeRoomProvisioningScript.ps1.txt) used to provision Skype Room Systems v2 accounts.
  
## See also

#### 

[Plan for Skype Room Systems v2](skype-room-systems-v2-0.md)
  
[Deploy Skype Room Systems v2](../../deploy-1/deploy-clients/room-systems-v2.md)
  
[Configure a Skype Room Systems v2 console](../../deploy-1/deploy-clients/console.md)
  
[Manage Skype Room Systems v2](../../manage/skype-room-systems-v2/skype-room-systems-v2.md)
#### 

[Skype for Business add-on licensing](https://support.office.com/en-US/article/Skype-for-Business-add-on-licensing-3ed752b1-5983-43f9-bcfd-760619ab40a7)

