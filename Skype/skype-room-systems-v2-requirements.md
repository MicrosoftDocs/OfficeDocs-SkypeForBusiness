---
title: Skype Room Systems v2 requirements
ms.prod: SKYPEFORBUSINESS
ms.assetid: 6b2b2684-8e9e-49ea-8c46-1c690964f982
---


# Skype Room Systems v2 requirements
[]
This article summarizes the requirements for supporting a Skype Room Systems v2. 
  
    
    

Your deployment will involve account creation as described in  [Deploy Skype Room Systems v2](deploy-skype-room-systems-v2.md) and setting up a meeting console as described in [Configure a Skype Room Systems v2 console](configure-a-skype-room-systems-v2-console.md). You may also need to refer to  [Skype for Business add-on licensing](https://support.office.com/en-US/article/Skype-for-Business-add-on-licensing-3ed752b1-5983-43f9-bcfd-760619ab40a7).
## Hardware requirements

Skype Room Systems v2 can scale to different room sizes through accessories depending on audio and video peripherals. Audio and video peripherals connect to Skype Room Systems v2 via a USB or HDMI connection on the docking device. You will also need:
  
    
    

- An 8GB or larger USB disk you will configure as bootable Windows installation media for Windows 10 Enterprise. 
    
  
- A Surface Pro 4 tablet with i5 processor
    
  
- Logitech  [SmartDock](https://www.logitech.com/en-us/product/smartdock) to secure the Surface Pro 4 tablet and anchor to the meeting room table.
    
  
- Certified USB audio and video peripherals appropriate to your room size (the manufacturer information will help you decide which to order). Choose from among the following:
    
|
|
|**Skype Room Systems v2 peripherals**|**Firmware version certified for Skype Room Systems v2**|
|:-----|:-----|
| [Logitech ConferenceCam Connect](http://www.logitech.com/en-us/product/conferencecam-connect) <br/> |1.1.248.0  <br/> 1.1.684  <br/> |
| [Logitech Group](http://www.logitech.com/en-us/product/conferencecam-group) <br/> |8.5.778  <br/> |
| [Logitech 930e](http://www.logitech.com/en-us/product/c930e-webcam) <br/> | 8.0.914 <br/> |
| [Logitech PTZ Pro](http://www.logitech.com/en-us/product/conferencecam-ptz-pro) <br/> | 1.1.219 <br/> |
| [Polycom RealPresence Trio](http://www.polycom.com/voice-conferencing-solutions/conference-phones/realpresence-trio.mdl) <br/> |5.4.4.7511  <br/> |
| [Polycom EagleEye MSR](http://www.polycom.com/hd-video-conferencing/microsoft-video/msr-series.mdl) <br/> |1.0.0  <br/> |
| [Polycom CX5100](http://www.polycom.com/products-services/products-for-microsoft/lync-optimized/cx5100-unified-conference-station.mdl) <br/> | 1.2.0.70232 <br/> |
| [Sennheiser SP 220 MS](http://no-no.sennheiser.com/dual-speakerphones-sp-220-ms-uc) <br/> |2.0.12.0  <br/> |
| [Sennheiser SP20](http://en-us.sennheiser.com/sp-20-og-sp-20-ml) <br/> |1.2.15  <br/> |
| [Jabra 510](http://www.jabra.com/support/Jabra-SPEAK™-510_7510-209) <br/> |2.10.0  <br/> |
| [Jabra 810](http://www.jabra.com/supportpages/jabra-speak-810) <br/> |1.2.23  <br/> |
   
- **USB extenders**: Crestron, Icron and C2G TruLink USB 2.0 Super Booster USB extenders are recommended for conference room use with Skype Room Systems v2. The extender must use a speed appropriate for the peripherals it will support.
    
  
- 1Gb Wired Ethernet connection in the room. Ethernet cable of appropriate length.
    
  
- 1080p display with an HDMI connection. HDMI cable of appropriate length.
    
  

> [!NOTE]
> Skype Room Systems v2 does not use a keyboard. If needed, the Admin should use the on-screen keyboard. A USB keyboard or mouse will be required when imaging the Skype Room Systems v2 device. 
  
    
    

The following table provides recommendations for peripherals based on room size:
  
    
    


|**Room Type**|**Number of People**|**Recommended maximum distance from microphone to person speaking**|**Device by maximum room size**|**Comments**|
|:-----|:-----|:-----|:-----|:-----|
|Focus  <br/> |2 - 4  <br/> |1.5m  <br/> |Logitech Connect  <br/> |The Logitech Connect devices includes a camera so it must be positioned at the front of the room (not center of table) to capture local meeting attendees.  <br/> |
|Small  <br/> |4 - 6  <br/> |2.0m  <br/> |Jabra 510  <br/> Sennheiser SP20  <br/> |Playback volume may be limited for larger rooms.  <br/> |
|Medium  <br/> |6 - 12  <br/> |2.4m  <br/> |Jabra 810  <br/> ||
|Large  <br/> |12 - 16  <br/> |3m  <br/> This distance also applies to the area covered by each additional satellite microphone connected to the audio device in question.  <br/> |Logitech Group  <br/> Polycom Trio  <br/> Polycom CX5100  <br/> Sennheiser SP 220 MS  <br/> |All audio devices listed in this row support satellite microphone options.  <br/> CX5100 includes a built-in 360 degree camera so that the device can be positioned in the center of table.  <br/> SP 220 MS must be used in daisy-chain configuration.  <br/> |
   

## Required Software Downloads

You will need the following downloads to build your own Skype Room Systems v2 image:
  
    
    

- The  [Skype Room Systems v2 installation package](https://go.microsoft.com/fwlink/?linkid=851168).
    
  
- Obtain a copy of the 64-bit version of Windows 10 Enterprise Anniversary edition (English language, build 1607). 
    
  
- The supported  [Surface Pro 4 drivers](http://download.microsoft.com/download/6/a/c/6acb37c4-e4c1-4e0e-bbae-ac7a0c303593/SurfacePro4_Win10_1701001_0.zip).
    
  

> [!NOTE]
> Windows 10 Enterprise Creators Update (build 1703) is not supported for Skype Room Systems v2 image creation. 
  
    
    

These downloads need to be combined into a bootable Windows installation media disk in a specific way, described further in  [Configure a Skype Room Systems v2 console](configure-a-skype-room-systems-v2-console.md). 
  
    
    
In addition, you will probably want a copy of the  [Powershell script](http://download.microsoft.com/download/9/0/D/90D4826A-9FD2-47D2-B911-97BF1737F4F7/SkypeRoomProvisioningScript.ps1.txt) used to provision Skype Room Systems v2 accounts.
  
    
    

## See also


#### 


  
    
    
 [Plan for Skype Room Systems v2](plan-for-skype-room-systems-v2.md)
  
    
    
 [Deploy Skype Room Systems v2](deploy-skype-room-systems-v2.md)
  
    
    
 [Configure a Skype Room Systems v2 console](configure-a-skype-room-systems-v2-console.md)
  
    
    
 [Manage Skype Room Systems v2](manage-skype-room-systems-v2.md)
#### 


  
    
    
 [Skype for Business add-on licensing](https://support.office.com/en-US/article/Skype-for-Business-add-on-licensing-3ed752b1-5983-43f9-bcfd-760619ab40a7)
