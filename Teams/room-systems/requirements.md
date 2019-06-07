---
title: "Microsoft Teams Rooms requirements"
ms.author: v-lanac
author: lanachin
ms.reviewer: davgroom
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 6b2b2684-8e9e-49ea-8c46-1c690964f982
ms.collection: M365-voice
description: "This article summarizes the requirements for supporting Microsoft Teams Rooms."
---

# Microsoft Teams Rooms requirements

This article summarizes the requirements for supporting Microsoft Teams Rooms. 

Your deployment will involve account creation as described in [Deploy Microsoft Teams Rooms](room-systems-v2.md) and setting up a meeting console as described in [Configure a Microsoft Teams Rooms console](console.md). 

You may also need to refer to:

- [Skype for Business add-on licensing](/SkypeForBusiness/skype-for-business-and-microsoft-teams-add-on-licensing/skype-for-business-and-microsoft-teams-add-on-licensing)
- [License options based on your plan: Microsoft Teams Rooms](/SkypeForBusiness/skype-for-business-and-microsoft-teams-add-on-licensing/license-options-based-on-your-plan/skype-room-systems-v2)

> [!NOTE]
> Microsoft Teams Rooms is intended for use with Microsoft Teams, Skype for Business Server 2019, Skype for Business Server 2015, or Skype for Business Online. <br><br>Earlier platforms like Lync Server 2013 aren't expected to work with Microsoft Teams Rooms.

> [!NOTE]
> If using an on-prem Exchange server, Microsoft Teams Rooms requires the use of Exchange Server 2013 SP1 or later.

## Hardware requirements

Microsoft Teams Rooms can scale to different room sizes through accessories depending on audio and video peripherals. The hardware listed in this article supports both Skype and Teams meeting modes.  Audio and video peripherals connect to Microsoft Teams Rooms via a USB or HDMI connection on the docking device. You will also need:

- A  32GB or larger USB disk you will configure as bootable Windows installation media for Windows 10 Enterprise. 

- One of the following tablets or consoles:

**Supported tablets**

|Tablet|Processor|RAM|Disk|
|:-----|:-----|:-----|:-----|
|Surface Pro 6          |Core i5  |16GB or 8GB |128GB or more  |
|Surface Pro (5th Gen)  |Core i5  |8GB or 4GB  |128GB or more  |
|Surface Pro 4          |Core i5  |8GB or 4GB  |128GB or more  |

- One of the following docking station options to secure a tablet to the meeting room table. 

  - [Logitech SmartDock](https://partnersolutions.skypeforbusiness.com/solutionscatalog/all/logitech-smart-dock)

  - [Crestron SR](http://www.crestron.com/products/line/sr-for-skype-for-business-room-system )

  - [Polycom MSR Series](http://www.polycom.com/hd-video-conferencing/microsoft-video/msr-series.html)


**Supported consoles**

|Console|Processor|RAM|Disk|Firmware version|
|:-----|:-----|:-----|:-----|:----|
|[Crestron Flex M150](https://crestron.com/en-US/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Tabletop-Conferencing-Systems/UC-M150-T)|Core i7|8GB |128GB|1.0.16.490|
|[HP Elite Slice for Meeting Rooms G2](https://www8.hp.com/us/en/elite-family/elite-slice-for-meetings.html) |Core i5  |8GB  |128GB  | |
|[HP Elite Slice G2 Audio Ready with Microsoft Teams Rooms](https://store.hp.com/us/en/pdp/hp-elite-slice-for-meeting-rooms-g2-skype-room-systems-audio-ready?jumpid=cp_r12131_us/en/psg/elite_slice_for_meetings/product/shop-now-eliteslicemeeting-g2-audio) |Core i5 |8GB |128GB | |
|[Lenovo ThinkSmart Hub 500](https://www3.lenovo.com/us/en/hub500) |Core i5  |8GB  |128GB  |  |
|[Yealink MVC800](https://www.yealink.com/products_125.html)|Core i5|8GB|128GB|Audio-92.10.0.15</br>Video-92.10.0.15|
|
> [!NOTE]
> Core M3 processors are not supported.

**Certified firmware versions for USB audio and video peripherals**

|Microsoft Teams Rooms peripherals|Firmware version certified for Microsoft Teams Rooms|
|:-----|:-----|
|[Logitech Rally](https://www.logitech.com/en-us/product/rally-ultra-hd-conferencecam) <br/> |1.2.4 |
|[Logitech BRIO](https://www.logitech.com/en-us/product/brio) <br/> |v240|
|[Logitech MeetUp](http://www.logitech.com/en-us/product/meetup-conferencecam) <br/> |Audio - 1.0.172  <br/> Video - 1.0.156  <br/> |
|[Logitech ConferenceCam Connect](http://www.logitech.com/en-us/product/conferencecam-connect) <br/> |1.1.248.0  <br/> 1.1.684  <br/> |
|[Logitech Group](http://www.logitech.com/en-us/product/conferencecam-group) <br/> |8.5.778  <br/> |
|[Logitech 930e](http://www.logitech.com/en-us/product/c930e-webcam) <br/> | 8.0.914 <br/> |
|[Logitech PTZ Pro](http://www.logitech.com/en-us/product/conferencecam-ptz-pro) <br/> | 1.1.219 <br/> |
|[Logitech PTZ Pro 2](http://www.logitech.com/en-us/product/conferencecam-ptz-pro2) <br/> |
|[Polycom Trio 8500](http://www.polycom.com/voice-conferencing-solutions/conference-phones/realpresence-trio.mdl) <br/> |5.4.4.7511  <br/> |
|[Polycom EagleEye IV](http://www.polycom.com/products-services/hd-telepresence-video-conferencing/realpresence-accessories/eagleeye-cameras.mdl) <br/> |1.0.0  <br/> |
|[Polycom CX5100](http://www.polycom.com/products-services/products-for-microsoft/lync-optimized/cx5100-unified-conference-station.mdl) <br/> | 1.2.0.70232 <br/> |
|[Polycom Eagle Eye Director II](https://www.polycom.com/hd-video-conferencing/peripherals/eagleeye-director-ii.html)|2.1.0.10|
|[Polycom Trio 8500 / 8800](https://www.polycom.com/voice-conferencing-solutions/conference-phones/trio.html) <br/> |5.7.2.3205|
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
> Microsoft Teams Rooms does not use a keyboard. If needed, the Admin should use the on-screen keyboard. A USB keyboard or mouse will be required when imaging the Microsoft Teams Rooms device. 

The following tables provide recommendations for peripherals based on room size:

**Microsoft Teams Rooms Certified Audio Peripherals**

|Room Type|Number of People|Recommended maximum distance from microphone to person speaking|Device by maximum room size|Comments|
|:-----|:-----|:-----|:-----|:-----|
|**Focus** <br/> 10' x 9'  <br/> |2-4  <br/> |1.5m  <br/> |Logitech Connect  <br/> |The Logitech Connect devices include a camera so it must be positioned at the front of the room (not center of table) to capture local meeting attendees.  <br/> |
|**Small** <br/> 16' x 16'  <br/> |4-6  <br/> |2.0m  <br/> |Jabra 510  <br/> Sennheiser SP20  <br/> |Playback volume may be limited for larger rooms.  <br/> |
|**Medium** <br/> 18' x 20'  <br/> |6-12  <br/> |2.4m  <br/> |Jabra 710  <br/> Jabra 810  <br/> Logitech MeetUp  <br/> Logitech Group  <br/> Polycom Trio  <br/> Polycom CX5100  <br/> Sennheiser SP 220 MS  <br/> Yamaha YVC-1000MS  <br/> |The Logitech MeetUp includes a camera so it must be positioned at the front of room (not center of table to capture local meeting attendees).  <br/> In general, rooms with long rectangular or u-shaped tables may benefit from additional satellite microphones.  <br/> SP 220 MS must be used in daisy-chain configuration.  <br/> |
|**Large** <br/> 15' x 32'  <br/> |12-16  <br/> |3m  <br/> This distance also applies to the area covered by each additional satellite microphone connected to the audio device in question.  <br/> |Logitech Group + satellite mics  <br/> Polycom Trio+ satellite mics  <br/> Polycom CX5100 + satellite mics  <br/> Sennheiser SP 220 MS  <br/> Yamaha YVC-1000MS + satellite mics  <br/> |All audio devices listed in this row support satellite microphone options.  <br/> CX5100 includes a built-in 360 degree camera so that the device can be positioned in the center of table.  <br/> SP 220 MS must be used in daisy-chain configuration.  <br/> |

**Microsoft Teams Rooms Certified Video Peripherals**

|Room Type|Number of People|Device by Optimal room size|Comments|
|:-----|:-----|:-----|:-----|
|**Focus** <br/> 10' x 9'  <br/> |2-4  <br/> |Logitech Connect  <br/> Logitech MeetUp  <br/> Polycom CX5100  <br/> ||
|**Small** <br/> 16' x 16'  <br/> |4-6  <br/> |Logitech C930e  <br/> Logitech MeetUp  <br/> Logitech BRIO  <br/> Logitech PTZ Pro  <br/> Polycom MSR  <br/> Polycom CX5100  <br/> |Logitech PTZ Pro often bundled with Logitech Group  <br/> |
|**Medium** <br/> 18' x 20'  <br/> |6-12  <br/> |Logitech MeetUp  <br/> Logitech BRIO  <br/> Logitech PTZ Pro  <br/> Polycom MSR  <br/> Polycom CX5100  <br/> ||
|**Large** <br/> 15' x 32'  <br/> |12-16  <br/> |Logitech PTZ Pro  <br/> Polycom MSR  <br/> Polycom CX5100  <br/> ||

 > [!NOTE]
 > Front of room display resolution should be set to no greater than 1920x1080p.

## Required software downloads

To build your own Microsoft Teams Rooms image, follow the instructions in [Configure a Microsoft Teams Rooms console](console.md). Those instructions will guide you through downloading all necessary software for the installation process. 

> [!NOTE]
> IT professionals will need access to Windows 10 Enterprise ISO files through their volume licensing agreement.

In addition, you will probably want a copy of [SkypeRoomProvisioningScript.ps1](https://go.microsoft.com/fwlink/?linkid=870105), which you can use to provision Microsoft Teams Rooms accounts.

## See also
[Browse All Bundles](https://products.office.com/en-us/microsoft-teams/across-devices/devices)

[Plan for Microsoft Teams Rooms](skype-room-systems-v2-0.md)

[Deploy Microsoft Teams Rooms](room-systems-v2.md)

[Configure a Microsoft Teams Rooms console](console.md)

[Manage Microsoft Teams Rooms](skype-room-systems-v2.md)

[Skype for Business add-on licensing](https://support.office.com/en-US/article/Skype-for-Business-add-on-licensing-3ed752b1-5983-43f9-bcfd-760619ab40a7)
