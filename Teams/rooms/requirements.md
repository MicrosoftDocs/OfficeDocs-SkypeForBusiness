---
title: "Microsoft Teams Rooms requirements"
ms.author: v-lanac
author: lanachin
ms.reviewer: sohailta
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: msteams
localization_priority: Normal
ms.assetid: 6b2b2684-8e9e-49ea-8c46-1c690964f982
ms.collection: 
  - M365-collaboration
description: "This article summarizes the requirements for supporting Microsoft Teams Rooms."
---

# Microsoft Teams Rooms requirements

Microsoft Teams Rooms scale to different room sizes by using a wide variety of certified audio and video peripherals based on the size and use of the room. By selecting the right core device and console, combined with microphones, speakers, cameras, and displays appropriate for the space, you can deploy Microsoft Teams Rooms into spaces of any size from very small huddle spaces up through very large conference spaces and boardrooms.  The full set of all available certified audio and video peripherals that may be used to configure your room is available in the [Device Showcase](https://products.office.com/microsoft-teams/across-devices).

This article summarizes the device deployment and configuration requirements for supporting Microsoft Teams Rooms.

Your deployment involves account creation as described in [Deploy Microsoft Teams Rooms](room-systems-v2.md) and set up of meeting consoles as described in [Configure a Microsoft Teams Rooms console](console.md).

Also, refer to:

- [Skype for Business add-on licensing](/SkypeForBusiness/skype-for-business-and-microsoft-teams-add-on-licensing/skype-for-business-and-microsoft-teams-add-on-licensing)
- [License options based on your plan: Microsoft Teams Rooms](/SkypeForBusiness/skype-for-business-and-microsoft-teams-add-on-licensing/license-options-based-on-your-plan/skype-room-systems-v2)

> [!NOTE]
> Microsoft Teams Rooms sign in to Microsoft Teams, Skype for Business Server 2019, Skype for Business Server 2015, or Skype for Business Online, and may join meetings hosted by any of these services.
>
> Earlier platforms like Lync Server 2013 are not supported by Microsoft Teams Rooms. Microsoft Teams Rooms is not supported in Office 365 operated by 21Vianet, or in GCC-High, or DoD environments.
>
> If you have an on-prem Exchange server, Microsoft Teams Rooms requires the use of Exchange Server 2013 SP1 or later.

## Hardware requirements
A hardware deployment includes a selection of a Microsoft Teams Room system, combined with certified audio and video peripherals, and a cabling solution to integrate these devices together.  These options are described here.

**Supported Microsoft Teams Room systems**

All current Microsoft Teams Room devices and bundles are available in the [Room Systems product showcase](https://products.office.com/microsoft-teams/across-devices/devices/category?devicetype=20&page=1&filterIds=).

  |Console|Processor|RAM|Disk|
  |:-----|:-----|:-----|:-----|
  |[Crestron Flex UC-M130-T](https://crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Tabletop-Conferencing-Systems/UC-M130-T)|Core i5|8 GB |128 GB |
  |[Crestron Flex UC- B130-T](https://crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Wall-Mount-Conferencing-Systems/UC-B130-T)|Core i5|8 GB |128 GB |
  |[Crestron Flex UC-B140-T](https://crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Wall-Mount-Conferencing-Systems/UC-B140-T)|Core i5|8 GB |128 GB |
  |[Crestron Flex UC-M150-T](https://crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Tabletop-Conferencing-Systems/UC-M150-T)|Core i7|8 GB |128 GB |
  [Crestron Flex UC-B160-T](https://crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Wall-Mount-Conferencing-Systems/UC-B160-T)|Core i7|8 GB |128 GB|
  |[Crestron Flex UC-C160-T](https://crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Integrator-Kits/UC-C160-T)|Core i7|8 GB|128 GB|
  |[HP Elite Slice for Meeting Rooms G2](https://www8.hp.com/us/en/elite-family/elite-slice-for-meetings.html) |Core i5 |8 GB |128 GB |
  |[HP Elite Slice G2 Audio Ready with Microsoft Teams Rooms](https://store.hp.com/us/en/pdp/hp-elite-slice-for-meeting-rooms-g2-skype-room-systems-audio-ready?jumpid=cp_r12131_us/en/psg/elite_slice_for_meetings/product/shop-now-eliteslicemeeting-g2-audio) |Core i5 |8 GB |128 GB |
  |[Lenovo ThinkSmart Hub 500](https://www3.lenovo.com/us/en/hub500) |Core i5 |8 GB |128 GB |
  |[Logitech Tap](https://www.logitech.com/product/microsoft-rooms)|Core i5|8 GB |128 GB |
  |[Yealink MVC800](https://www.yealink.com/products_125.html)|Core i5|8 GB|128 GB|
  |[Yealink MVC500](https://www.yealink.com/products_126.html)|Core i5|8 GB |128 GB |
  |[Yealink MVC300](https://www.yealink.com/products_154.html)|Core i5|8 GB |128 GB |
  ||||||

> [!NOTE]
> - Core M3 processors are not supported.
> - You need a 32 GB or larger USB drive configured as bootable Windows installation media for Windows 10 Enterprise.

**Supported Surface Pro tablets for dock-style systems**

  |Tablet|Processor|RAM|Disk|
  |:-----|:-----|:-----|:-----|
  |Surface Pro 6| Core i5 |16 GB or 8 GB |128 GB or more |
  |Surface Pro </br>(fifth Gen) |Core i5 |8 GB or 4 GB |128 GB or more |
  |Surface Pro 4 |Core i5 |8 GB or 4 GB |128 GB or more |

- One of the following docking station options to secure a tablet to the meeting room table.

  - [Logitech SmartDock](https://www.logitech.com/product/smartdock)
  - [Crestron SR](http://www.crestron.com/products/line/sr-for-skype-for-business-room-system )
  - [Polycom MSR Series](http://www.polycom.com/hd-video-conferencing/microsoft-video/msr-series.html)

### Certified firmware versions for USB audio and video peripherals

These devices are available at the [Room System Accessories product showcase](https://products.office.com/microsoft-teams/across-devices/devices/category?devicetype=73&page=1&filterIds=) and [https://office.com/teamsdevices](https://office.com/teamsdevices).

|Microsoft Teams Rooms peripheral|Certified firmware version | Camera supports content camera use|
|:--- |:--- | :--- |
|[Crestron Huddly IQ](https://www.crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Accessories/CCS-CAM-USB-F-400)   | 1.02.09.33901  | &#x2714; |
|[Logitech Brio](https://www.logitech.com/product/brio)   |V2.2.50| &#x2714; |
|[Logitech 930e](http://www.logitech.com/product/c930e-webcam)   | 8.0.914   | &#x2714; |
|[Logitech Rally](https://www.logitech.com/product/rally-ultra-hd-conferencecam)   |1.2.4 |
|[Logitech MeetUp](http://www.logitech.com/product/meetup-conferencecam)   |Audio — 1.0.172 <br/> Video — 1.0.156  |
|[Logitech ConferenceCam Connect](http://www.logitech.com/product/conferencecam-connect)   |1.1.248.0 <br/> 1.1.684   |
|[Logitech Group](http://www.logitech.com/product/conferencecam-group)   |8.5.778   |
|[Logitech PTZ Pro](http://www.logitech.com/product/conferencecam-ptz-pro)   | 1.1.219   |
|[Logitech PTZ Pro 2](http://www.logitech.com/product/conferencecam-ptz-pro2)   |
|[Polycom EagleEye IV](http://www.polycom.com/products-services/hd-telepresence-video-conferencing/realpresence-accessories/eagleeye-cameras.mdl)   |1.0.0   |
|[Polycom CX5100](http://www.polycom.com/products-services/products-for-microsoft/lync-optimized/cx5100-unified-conference-station.mdl)   | 1.2.0.70232   |
|[Polycom Eagle Eye Director II](https://www.polycom.com/hd-video-conferencing/peripherals/eagleeye-director-ii.html)|2.1.0.10|
|[Polycom Studio Soundbar](https://www.polycom.com/hd-video-conferencing/room-video-systems/polycom-studio.html)|1.1.2.000570|
|[Polycom Trio 8500 / 8800](https://www.polycom.com/voice-conferencing-solutions/conference-phones/trio.html)   |5.7.2.3205|
|[Sennheiser SP 220 MS](http://no-no.sennheiser.com/dual-speakerphones-sp-220-ms-uc)   |2.0.12.0   |
|[Sennheiser SP20](http://en-us.sennheiser.com/sp-20-og-sp-20-ml)   |1.2.15   |
|[Sennheiser SP30](https://en-us.sennheiser.com/sp-30)   |2.1.52  |
|[Sennheiser SP30T](https://en-us.sennheiser.com/sp-30)  |3.2.63  |
|[Jabra 510](http://www.jabra.com/support/Jabra-SPEAK™-510_7510-209)   |2.10.0   |
|[Jabra 710](http://www.jabra.com/business/speakerphones/jabra-speak-series/jabra-speak-710)   |1.8.0   |
|[Jabra 810](http://www.jabra.com/supportpages/jabra-speak-810)   |1.2.23   |
|[Yamaha YVC-1000](http://www.yamaha.com/products/en/communication/usb_conference_speakerphones/yvc-1000/)   |100c   |
|[Yealink CP900](https://www.yealink.com/products_150.html) |100.20.0.29 |
|[Biamp Tesira Fore AVB VT4 Fixed audio DSP](https://www.biamp.com/products/tesira-fixed-audio-dsp)+ &Dagger;</br></br> [Sennheiser TeamConnect Ceiling 2 Microphone](https://en-us.sennheiser.com/tcc2)+ &Dagger;</br></br> [Tesira EX-UBT](https://www.biamp.com/products/tesira/tesira-expanders) &Dagger; |  Biamp DSP: 3.12.0.15  </br></br> TCC2: 1.3.3 </br></br> EX-UBT: 3.12.0.15 |  |
||||||

&Dagger; Customers may choose either the Dante interface or the network switch recommended by Biamp/Sennheiser for this bundle.

#### USB extenders

- USB ports on tablet docks are USB 3.0 compatible. You can use a USB 2.x extender but doing this limits you to USB 2.x speeds on the far end. Extenders are not recommended for USB 3.0 peripherals.
- An extender must meet USB 2.0 or newer specifications.
  - Tablet docks support at least two stages of external USB hub extension. If you connect more than two USB hubs in series, check with the dock manufacturer to confirm whether they support series connection.
  - Wired GbE connection in the room. Ethernet cable of appropriate length.
  - Up to two 1080-p displays with HDMI connections. HDMI cables of appropriate length.

> [!NOTE]
> A consumer TV used as a front of room display needs to support/enable the Consumer Electronics Control (CEC) feature of HDMI so that it can switch automatically to an active video source from standby mode. This feature is not supported on all TVs.
>
> Microsoft Teams Rooms does not use a keyboard. If needed, the Admin should use the on-screen keyboard. A USB keyboard or mouse will be required when imaging the Microsoft Teams Rooms device.

The following tables provide recommendations for peripherals based on room size:

**Microsoft Teams Rooms Certified Audio Peripherals**

|Room Type|Number of People|Recommended maximum distance from microphone to speaker|Device by maximum room size|Comments|
|:-----|:-----|:-----|:-----|:-----|
|**Focus** <br/> 10' x 9'   |2–4  |1.5 m  |Logitech Connect  |Logitech Connect devices include a camera that must be positioned at the front of the room (not center of table) to capture local meeting attendees. |
|**Small** <br/> 16' x 16'  |4–6  |2.0 m  |Jabra 510 <br/> Sennheiser SP20  |Playback volume can be limited for larger rooms.  |
|**Medium** <br/> 18' x 20'  |6–12  |2.4 m  |Jabra 710 <br/> Jabra 810 <br/> Logitech MeetUp <br/> Logitech Group <br/> Polycom Trio <br/> Polycom CX5100 <br/> Sennheiser SP 220 MS <br/> Yamaha YVC-1000MS  |The Logitech MeetUp includes a camera so it must be positioned at the front of room (not center of table to capture local meeting attendees). <br/> In general, rooms with long rectangular or u-shaped tables may benefit from satellite microphones. <br/> SP 220 MS must be used in daisy-chain configuration.  |
|**Large** <br/> 15' x 32'  |12–16  |3 m <br/> This distance also applies to the area covered by each connected satellite microphone.  |Logitech Group + satellite mics <br/> Polycom Trio+ satellite mics <br/> Polycom CX5100 + satellite mics <br/> Sennheiser SP 220 MS <br/> Yamaha YVC-1000MS + satellite mics  |All audio devices listed in this row support satellite microphone options. <br/> CX5100 includes a built-in 360-degree camera so that the device can be positioned in the center of table. <br/> SP 220 MS must be used in daisy-chain configuration.  |

**Microsoft Teams Rooms Certified Video Peripherals**

|Room Type|Number of People|Device by Optimal room size|Comments|
|:-----|:-----|:-----|:-----|
|**Focus** <br/> 10' x 9'  |2–4  |Logitech Connect <br/> Logitech MeetUp <br/> Polycom CX5100  ||
|**Small** <br/> 16' x 16'  |4–6  |Logitech C930e <br/> Logitech MeetUp <br/> Logitech BRIO <br/> Logitech PTZ Pro <br/> Polycom MSR <br/> Polycom CX5100  |Logitech PTZ Pro often bundled with Logitech Group  |
|**Medium** <br/> 18' x 20'  |6–12  |Logitech MeetUp <br/> Logitech BRIO <br/> Logitech PTZ Pro <br/> Polycom MSR <br/> Polycom CX5100  ||
|**Large** <br/> 15' x 32'  |12–16  |Logitech PTZ Pro <br/> Polycom MSR <br/> Polycom CX5100  ||

 > [!NOTE]
 > Front of room display resolution should be set to no greater than 1920x1080p.

## Required software downloads

To build your own Microsoft Teams Rooms image, follow the instructions in [Configure a Microsoft Teams Rooms console](console.md). Those instructions guide you through download of all software necessary for installation.

> [!NOTE]
> IT professionals will need access to Windows 10 Enterprise ISO files through their volume licensing agreement.

[SkypeRoomProvisioningScript.ps1](https://go.microsoft.com/fwlink/?linkid=870105) is an optional download you can use to provision Microsoft Teams Rooms accounts.

## See also

[Browse All Bundles](https://products.office.com/microsoft-teams/across-devices/devices)

[Plan for Microsoft Teams Rooms](rooms-plan.md)

[Deploy Microsoft Teams Rooms](rooms-deploy.md)

[Configure a Microsoft Teams Rooms console](console.md)

[Manage Microsoft Teams Rooms](rooms-manage.md)

[Skype for Business add-on licensing](https://support.office.com/article/Skype-for-Business-add-on-licensing-3ed752b1-5983-43f9-bcfd-760619ab40a7)
