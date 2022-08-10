---
title: Microsoft Teams Rooms requirements
ms.author: dstrome
author: dstrome
ms.reviewer: sohailta
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: msteams
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.assetid: 6b2b2684-8e9e-49ea-8c46-1c690964f982
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Rooms
description: Learn about the requirements for supporting Microsoft Teams Rooms, including choosing the appropriate device, microphones, speakers, cameras, and displays.
ms.custom: seo-marvel-apr2020
---

# Microsoft Teams Rooms requirements

Microsoft Teams Rooms scale to different room sizes. Teams Rooms use a wide variety of certified audio and video peripherals based on the size and use of the room. By selecting the right core device and console, combined with microphones, speakers, cameras, and displays appropriate for the space, you can deploy Microsoft Teams Rooms into spaces of any size from small huddle spaces up through large conference spaces and boardrooms.  The full set of all available certified audio and video peripherals that may be used to configure your room is available in the [Device Showcase](https://products.office.com/microsoft-teams/across-devices).

This article summarizes the device deployment and configuration requirements for supporting Microsoft Teams Rooms.

Your deployment involves resource account creation and setup of Teams Rooms as described in [Deploy Microsoft Teams Rooms](rooms-deploy.md).

Refer to:

- [License options based on your plan: Microsoft Teams Rooms](rooms-licensing.md)

> [!NOTE]
> Microsoft Teams Rooms sign in to Microsoft Teams, Skype for Business Server 2019, or Skype for Business Server 2015 and may join meetings hosted by any of these services.
>
> Earlier platforms like Lync Server 2013 are not supported by Microsoft Teams Rooms. Microsoft Teams Rooms is not supported in Microsoft 365 or Office 365 operated by 21Vianet, or DoD environments.
>
> If you have an on-prem Exchange server, Microsoft Teams Rooms requires the use of Exchange Server 2013 SP1 or later.

## Hardware requirements
A hardware deployment includes a selection of a Microsoft Teams Room system, combined with certified audio and video peripherals, and a cabling solution to integrate these devices together.  These options are described here.

**Supported Microsoft Teams Room systems**

All current Microsoft Teams Room devices and bundles are available in the [Room Systems product showcase](https://products.office.com/microsoft-teams/across-devices/devices/category?devicetype=20&page=1&filterIds=).

  |Console|Processor|RAM|Disk|
  |:-----|:-----|:-----|:-----|
  |[Crestron Flex UC-M130-T with Intel NUC](https://crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Tabletop-Conferencing-Systems/UC-M130-T)|Core i5|8 GB |128 GB |
  |[Crestron Flex UC- B130-T with Intel NUC](https://crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Wall-Mount-Conferencing-Systems/UC-B130-T)|Core i5|8 GB |128 GB |
  |[Crestron Flex UC-B140-T with Intel NUC](https://crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Wall-Mount-Conferencing-Systems/UC-B140-T)|Core i5|8 GB |128 GB |
  [Crestron Flex UC-C140-T with Intel NUC](https://www.crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Integrator-Kits/UC-C140-T)|Core i7|8 GB |128 GB|
  |[Crestron Flex UC-M150-T with Intel NUC](https://crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Tabletop-Conferencing-Systems/UC-M150-T) + [CCS-UCA-MIC](https://www.crestron.com/Products/Audio/Microphones/Wired-Microphones/CCS-UCA-MIC-KIT)|Core i7|8 GB |128 GB |
  |[Crestron Flex UC-MX150-T with Intel NUC](https://www.crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Tabletop-Conferencing-Systems/UC-MX150-T)|Core i5|8 GB |128 GB |
   [Crestron Flex UC-B160-T with Intel NUC](https://crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Wall-Mount-Conferencing-Systems/UC-B160-T)|Core i7|8 GB |128 GB|
  |[Crestron Flex UC-C160-T with Intel NUC](https://crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Integrator-Kits/UC-C160-T)|Core i7|8 GB|128 GB|
  |[Crestron Flex UC-MMX30-T with UC Presentation Transmitter (UC-PR) and ASUS PC](https://www.crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Tabletop-Conferencing-Systems/UC-MMX30-T)|Core i5/i7|8 GB |128 GB |
  |[Crestron Flex UC-BX30-T with UC Presentation Transmitter (UC-PR) and ASUS PC](https://www.crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Wall-Mount-Conferencing-Systems/UC-BX30-T)|Core i5/i7|8 GB |128 GB |
  |[Crestron Flex UC-CX100-T with UC Presentation Transmitter (UC-PR) and ASUS PC](https://www.crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Integrator-Kits/UC-CX100-T)|Core i5/i7|8 GB |128 GB |
  |[Crestron Flex UC-B30-T with ASUS PC](https://www.crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Wall-Mount-Conferencing-Systems/UC-B30-T)|Core i5/i7|8 GB |128 GB |
   |[Crestron Flex UC-C100-T with ASUS PC](https://www.crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Integrator-Kits/UC-C100-T)|Core i5/i7|8 GB |128 GB |
   |[Crestron Flex UC-M50-T with ASUS PC](https://www.crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Tabletop-Conferencing-Systems/UC-M50-T)|Core i5/i7|8 GB |128 GB |
   |[Crestron Flex UC-M70-T with ASUS PC](https://www.crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Tabletop-Conferencing-Systems/UC-M70-T)|Core i5/i7|8 GB |128 GB |
   |[Crestron Flex UC-MX50-T with ASUS PC](https://www.crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Tabletop-Conferencing-Systems/UC-MX50-T)|Core i5/i7|8 GB |128 GB |
   |[Crestron Flex UC-MX70-T with ASUS PC](https://www.crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Tabletop-Conferencing-Systems/UC-MX70-T)|Core i5/i7|8 GB |128 GB |
   |Crestron FLEX UC-B30-T with Dell OPTIPLEX|Core i5|8 GB|128 GB|
   |Crestron FLEX UC-Bx30-T with Dell OPTIPLEX|Core i5|8 GB|128 GB|
   |Crestron FLEX UC-MM30-T with Dell OPTIPLEX|Core i5|8 GB|128 GB|
   |Crestron FLEX UC-MMX30-T with Dell OPTIPLEX|Core i5|8 GB|128 GB|
   |Crestron FLEX UC-M50-T with Dell OPTIPLEX|Core i5|8 GB|128 GB|
   |Crestron FLEX UC-MX50-T with Dell OPTIPLEX|Core i5|8 GB|128 GB|
   |Crestron FLEX UC-M70-T with Dell OPTIPLEX|Core i5|8 GB|128 GB|
   |Crestron FLEX UC-MX70-T with Dell OPTIPLEX|Core i5|8 GB|128 GB|
   |Crestron FLEX UC-C100-T with Dell OPTIPLEX|Core i5|8 GB|128 GB|
   |Crestron FLEX UC-CX100-T with Dell OPTIPLEX|Core i5|8 GB|128 GB|
  |[Crestron Mercury Mini UC-MM30-T](https://www.crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Tabletop-Conferencing-Systems/UC-MM30-T)|Core i5|8 GB |128 GB |
  |[Dell OptiPlex 7080 with Logitech TAP](https://www.dell.com/en-us/work/shop/cty/pdp/spd/optiplex-7080-xe-teams) | Core i7 |16 GB |128 GB|
  |[HP Elite Slice for Meeting Rooms G2](https://www8.hp.com/us/en/elite-family/elite-slice-for-meetings.html) |Core i5 |8 GB |128 GB |
  |[HP Elite Slice G2 Audio Ready with Microsoft Teams Rooms](https://store.hp.com/us/en/pdp/hp-elite-slice-for-meeting-rooms-g2-skype-room-systems-audio-ready?jumpid=cp_r12131_us/en/psg/elite_slice_for_meetings/product/shop-now-eliteslicemeeting-g2-audio) |Core i5 |8 GB |128 GB |
  |[HP Slice Partner Ready with Logitech TAP]( https://www.logitech.com/video-collaboration/partners/hp.html)|Core i5|8 GB|128 GB| 
  |[HP Presence Small Space Solution with Microsoft Teams Rooms](https://www.hp.com/us-en/solutions/presence.html)|Core i5/i7|8 GB/16 GB|256 GB|
  |[HP Presence Small Space Solution Plus AI Camera with Microsoft Teams Rooms](https://www.hp.com/us-en/solutions/presence.html)|Core i5/i7|8 GB/16 GB|256 GB|
  | Lenovo ThinkSmart Hub 500 |Core i5 |8 GB |128 GB |
  |[Lenovo ThinkSmart Hub](https://news.lenovo.com/pressroom/press-releases/new-thinksmart-hub-collaboration-solution-from-lenovo-helps-organizations-embrace-hybrid-working-model/) |Core i5 |8 GB |128 GB|
  |Lenovo ThinkSmart Core Kit |Core i5|8 GB|128 GB|
  |[Logitech Tap with Intel NUC](https://www.logitech.com/product/microsoft-rooms)|Core i5|8 GB |128 GB |
  |Logitech Tap and Intel Tiger Canyon NUC PC |Core i5|8 GB|128 GB|
  |Logitech TAP Console with Lenovo Core Compute |Core i5|8 GB|128 GB|
  |[Logitech Tap and Lenovo ThinkSmart Tiny](https://www.logitech.com/video-collaboration/partners/lenovo.html)|Core i5|8 GB |128 GB|
  |[Poly G10-T with Lenovo ThinkSmart Tiny](https://www.poly.com/us/en/products/video-conferencing/g/g10) |Core i5| 8 GB | 128 GB|
  |[Poly G40-T Kit with Poly Studio USB, with Lenovo](https://www.poly.com/us/en/support/products/video-conferencing/poly-room-solutions/g40) |Core i5| 8 GB | 128 GB|
  |[Poly G85-T Kit with Poly Eagle Eye Director II, with Lenovo](https://www.poly.com/us/en/support/products/video-conferencing/poly-room-solutions/g85) |Core i5| 8 GB | 128 GB|
  |Poly GC8 Console with Lenovo Thinksmart Core|Core i5|8 GB|128 GB|
  |Poly GC8 Console with Dell Optiplex 7080|Core i5|8 GB|128 GB|
  |[Yealink MVC300 with Intel NUC](https://www.yealink.com/products_154.html)|Core i5|8 GB |128 GB |
  |[Yealink MVC500 with Intel NUC](https://www.yealink.com/products_126.html)|Core i5|8 GB |128 GB |
  |[Yealink MVC800 with Intel NUC](https://www.yealink.com/products_125.html)|Core i5|8 GB|128 GB|
  |[Yealink MVC900 with Intel NUC](https://www.yealink.com/product/microsoft-teams-room-system-mvc900)|Core i5|8 GB|128 GB|
  |[Yealink MVC 300 II](https://www.yealink.com/product/microsoft-teams-room-system-mvc300II) |Core i5|8 GB | 128 GB|
  |[Yealink MVC400](https://www.yealink.com/product/microsoft-teams-room-system-mvc400)        |Core i5|8 GB | 128 GB|
  |[Yealink MVC 500 II](https://www.yealink.com/product/microsoft-teams-room-system-mvc500II) |Core i5|8 GB | 128 GB|
  |[Yealink MVC 800 II](https://www.yealink.com/product/microsoft-teams-room-system-mvc800II) |Core i5|8 GB | 128 GB|
  |[Yealink MVC 900 II](https://www.yealink.com/product/microsoft-teams-room-system-mvc900II) |Core i5|8 GB | 128 GB|
  |[Yealink MVC840](https://www.yealink.com/product/microsoft-teams-room-system-mvc840) |Core i5|8 GB | 128 GB|
  |[Yealink MVC940](https://www.yealink.com/product/microsoft-teams-room-system-mvc940) |Core i5|8 GB | 128 GB|
  |Yealink MVC660|Core i5|8 GB | 128 GB|
  |Yealink MVC640|Core i5|8 GB | 128 GB|
  |Yealink MVC320|Core i5|8 GB | 128 GB|
  |Yealink MVC340|Core i5|8 GB | 128 GB|
  
  
> [!NOTE]
> - Core M3 processors are not supported.
> - You need a 32 GB or larger USB drive configured as bootable Windows installation media for Windows 10 Enterprise.

**Supported Surface Pro tablets for dock-style systems**

  |Tablet|Processor|RAM|Disk|
  |:-----|:-----|:-----|:-----|
  |Surface Pro 6| Core i5 |16 GB or 8 GB |128 GB or more |
  |Surface Pro </br>(fifth Gen) |Core i5 |8 GB or 4 GB |128 GB or more |
  |Surface Pro 4 |Core i5 |8 GB or 4 GB |128 GB or more |

- Surface Pro devices require one of the following docking station options:

  - [Logitech SmartDock](https://www.logitech.com/product/smartdock)
  - [Crestron SR](https://www.crestron.com/products/line/sr-for-skype-for-business-room-system )
  - [Polycom MSR Series](https://www.polycom.com/hd-video-conferencing/microsoft-video/msr-series.html)

### Certified firmware versions for USB audio and video peripherals

These devices are available at the [Room System Accessories product showcase](https://products.office.com/microsoft-teams/across-devices/devices/category?devicetype=73&page=1&filterIds=) and [https://office.com/teamsdevices](https://office.com/teamsdevices).

|Microsoft Teams Rooms peripheral|Certified firmware version | Supports content camera|Intelligent camera|
|:--- |:--- | :--- |:--- |
|[Aver VC520 Pro Camera + Speakerphone](https://www.averusa.com/products/conference-camera/vc520pro) |1004.35|
|[Aver VC520 PRO2 Conferencing System](https://www.averusa.com/products/conference-camera/vc520pro2) | 00.0.7200.79 |
|[Aver VB342+ Camera Soundbar](https://www.averusa.com/products/conference-camera/vb342plus) | Soundbar: 0.0.0000.97|
|[Aver CAM 540](https://www.averusa.com/products/conference-camera/cam540) |0.0.6002.83 |
|[Aver CAM 520 Pro](https://www.averusa.com/products/conference-camera/cam520pro) |0.0.1000.73 |
|[Aver CAM 520 Pro 2](https://www.averusa.com/products/conference-camera/cam520pro2) |0.0.7200.3 |
|[Aver CAM 130](https://www.averusa.com/products/conference-camera/cam130) |0.0.7450.02 | &#x2714; |
|[Aver VB130 Camera Soundbar](https://www.averusa.com/products/conference-camera/vb130) |0.0.7300.71 |
|[Audiocodes RXVCAM50L](https://www.audiocodes.com/solutions-products/products/room-experience-rx-suite/rxvcam50lm-video-camera) |1.0.5 |
|[Bose Video Bar VB1](https://pro.bose.com/en_us/products/conferencing/videobars/bose-videobar-vb1.html?mc=25_PS_VB_BO_00_BI_&&msclkid=fc99b79880f714727a63e86ea0e5642a&utm_source=bing&utm_medium=cpc&utm_campaign=US%20-%20Brand_Videobar%20VB1_Exact&utm_term=bose%20videobar%20vb1&utm_content=Bose%20Videobar%20VB1&gclid=fc99b79880f714727a63e86ea0e5642a&gclsrc=3p.ds) |19.2|
|[Biamp Devio SCR-20CX Web-Based Conferencing Hub with Ceiling Microphone](https://www.biamp.com/products/product-families/devio/huddle-room-solutions) |2.2.0.9|
|[Biamp Devio SCR-20TX Web-Based Conferencing Hub with Tabletop Microphone](https://www.biamp.com/products/product-families/devio/huddle-room-solutions) |2.2.0.9 |
|[Crestron Huddly IQ](https://www.crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Accessories/CCS-CAM-USB-F-400)   | 1.02.09.33901  | 
|HP Presence See Camera| 1.0.23.0 |
|[Huddly Canvas](https://www.huddly.com/blog/say-hello-to-huddly-canvas-our-latest-ai-technology-for-content-capture-and-enhancement/) | 1.3.25 |  &#x2714; |
|[Huddly IQ](https://www.huddly.com/conference-cameras/iq/) |1.3.22|
|[Huddly IQ Lite](https://www.huddly.com/conference-cameras/iq/) |1.3.29|
|[Huddly IQ Camera](https://www.huddly.com/conference-cameras/iq/) |1.3.27|
|[Huddly L1](https://www.huddly.com/conference-cameras/l1/) | 1.2.9 |
|Huddly L1 Camera with [Crestron UC-C100-T MTR](https://www.crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Integrator-Kits/UC-C100-T) kit | Huddly L1 Camera: 1.2.1 </br> Crestron UC-C100-T with ASUS Tek Computer INC 9934 compute 1.0.20.246 or above |
|Huddly L1 Camera with [Crestron UC-CX100-T](https://www.crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Integrator-Kits/UC-CX100-T) MTR-W Kit | Huddly L1 Camera: 1.2.9 </br> Crestron UC-CX100-T with ASUS Tek Computer INC 9934 1.00.20.246 or above |
|Huddly L1 Camera with Crestron UC-M70-T MTR kit | Huddly L1 Camera: 1.2.1 </br> Crestron UC-M70-T with ASUS Tek Computer INC 9934 compute 1.0.20.246 or above |
|Huddly L1 Camera with Crestron UC-MX70-T MTR kit | Huddly L1 Camera: 1.2.1 </br> Crestron UC-MX70-T with ASUS Tek Computer INC 9934 compute 1.0.20.246 or above |
|[Jabra Panacast3 Camera](https://www.jabra.com/business/video-conferencing/jabra-panacast)|1.3.9.12|
|[Jabra Panacast 50 Video Bar](https://www.jabra.com/business/video-conferencing/jabra-panacast-50)|4.0.15| &#x2714; | &#x2714;|
|[Lenovo ThinkSmart Cam Camera](https://www.lenovo.com/us/en/accessories-and-monitors/webcams-and-video/webcams/SMARTOF-BO-ThinkSmart-Cam/p/4Y71C41660)|1.0.111.4|
|[Lenovo ThinkSmart Bar](https://www.lenovo.com/us/en/virtual-reality-and-smart-devices/smart-collaboration/thinksmart/ThinkSmart-Bar/p/11SP1TSSDBR)|0.9.3|
|Lenovo ThinkSmart Bar Expand XL|5.9.5|
|[Logitech Brio](https://www.logitech.com/product/brio)   |V2.2.50| &#x2714; |
|[Logitech 930e](https://www.logitech.com/product/c930e-webcam)   | 8.0.914   | &#x2714; |
|[Logitech Rally](https://www.logitech.com/product/rally-ultra-hd-conferencecam)   |1.2.4 |
|[Logitech Rally Bar](https://www.logitech.com/products/video-conferencing/room-solutions/rallybar.960-001308.html)   |10.3.82|
|[Logitech Rally Bar Mini](https://www.logitech.com/en-us/products/video-conferencing/room-solutions/rallybarmini.960-001336.html) |10.5.880|
|[Logitech MeetUp](https://www.logitech.com/product/meetup-conferencecam)   |Audio — 1.0.172 <br/> Video — 1.0.156  |
|[Logitech ConferenceCam Connect](https://www.logitech.com/product/conferencecam-connect)   |1.1.248.0 <br/> 1.1.684   |
|[Logitech Group](https://www.logitech.com/product/conferencecam-group)   |8.5.778   |
|[Logitech PTZ Pro](https://www.logitech.com/product/conferencecam-ptz-pro)   | 1.1.219   |
|[Logitech PTZ Pro 2](https://www.logitech.com/product/conferencecam-ptz-pro2)   |
|[Logitech Scribe](https://www.logitech.com/en-us/products/video-conferencing/room-solutions/scribe.960-001332.html) | 1.1.1 | &#x2714; |
|[Nureva HDL300](https://www.nureva.com/audio-conferencing/hdl300) |2.3.6|
|[Poly Eagle Eye Cube Camera](https://www.polycom.com/products-services/hd-telepresence-video-conferencing/realpresence-accessories/eagleeye-cameras.html)  |1.2.0 |
|[Polycom EagleEye IV](https://www.poly.com/us/en/products/video-conferencing/eagleeye/eagleeye-iv)   |1.0.0   |
|[Polycom CX5100](https://www.polycom.com/products-services/products-for-microsoft/lync-optimized/cx5100-unified-conference-station.md)   | 1.2.0.70232   |
|[Polycom Eagle Eye Director II](https://support.polycom.com/content/dam/polycom-support/products/peripherals/eagle-eye-director-ii/user/en/eagleeye-director-ii-admin-guide-2-0.pdf#:~:text=The%20Polycom%C2%AE%20EagleEye%E2%84%A2%20Director%20II%20camera%20is%20a,while%20the%20other%20camera%20tracks%20the%20second%20speaker.)|2.1.0.10|
|[Polycom Studio Soundbar](https://www.polycom.com/hd-video-conferencing/room-video-systems/polycom-studio.html)|1.1.2.000570|
|[Poly Sync 40](https://www.poly.com/us/en/products/phones/sync/sync-40)|0.0.94.1461|
|[Poly Sync 60](https://www.poly.com/us/en/products/phones/sync/sync-60)|0.0.150.1671|
|[Polycom Trio 8500 / 8800](https://www.polycom.com/voice-conferencing-solutions/conference-phones/trio.html)   |5.7.2.3205|
|[Poly Trio C60](https://www.poly.com/us/en/products/phones/trio/trio-c60)  |5.9.5.3066|
|[Poly Studio P15 Video Bar](https://www.poly.com/us/en/products/video-conferencing/studio-p/studio-p15)|1.2.0.000287 |
|[Poly Studio E70 Camera](https://www.poly.com/us/en/products/video-conferencing/studio/studio-e70)|1.1|
|[Poly Studio R30](https://www.poly.com/us/en/products/video-conferencing/studio/studio-r30)|2.0.0.001096|
|[EPOS SP 220 MS](http://no-no.sennheiser.com/dual-speakerphones-sp-220-ms-uc)   |2.0.12.0   |
|[EPOS SP20](https://www.eposaudio.com/en/us/enterprise/products/sp-20-ml-142ee5ca-speakerphone-1000226)   |1.2.15   |
|[EPOS SP30](https://www.eposaudio.com/en/us/enterprise/products/sp-30-78c0cecc-bluetooth-speakerphone-1000223)   |2.1.52  |
|[EPOS SP30T](https://www.eposaudio.com/en/us/enterprise/products/sp-30t-b949fe9a-bluetooth-speakerphone-1000225)  |3.2.63  |
|[EPOS Expand 80T + 2 Extension Mics](https://www.eposaudio.com/en/us/enterprise/products/expand-80t-bluetooth-speakerphone-1000203) |Speakerphone — 4.6.55 <br/> Extension Mic — 0.2.314|
|[EPOS Expand Capture 5](https://www.eposaudio.com/en/us/enterprise/products/expand-capture-5-speakerphone-1000895)  |1.0.1|
|[Extron DMP128 PLUS C V AT DSP System (DMP 128 Plus C V AT, DMP 128 Plus C AT, DMP 128 Plus C V, DMP 128 Plus C, DMP 128 Plus AT, DMP 128 Plus, DMP 128 FlexPlus C AT, DMP 128 FlexPlus C V AT)](https://www.extron.com/product/dmp128plus) | 1.08 |
|[Extron DMP 64 PLUS C V AT DSP System (DMP 64 Plus C V AT, DMP 64 Plus C AT, DMP 64 Plus C V, DMP 64 Plus C)](https://www.extron.com/product/dmp64plus) | 1.08|
|[Jabra 510](http://www.jabra.com/support/Jabra-SPEAK&trade;-510_7510-209)   |2.10.0   |
|[Jabra 710](http://www.jabra.com/business/speakerphones/jabra-speak-series/jabra-speak-710)   |1.8.0   |
|[Jabra 810](http://www.jabra.com/supportpages/jabra-speak-810)   |1.2.23   |
|[Yamaha YVC-1000](http://www.yamaha.com/products/en/communication/usb_conference_speakerphones/yvc-1000/)   |100c   |
|[Yamaha YVC-1000MS](https://uc.yamaha.com/products/conference-phones/usb-bluetooth/) |1.0.0 |
|[Yamaha ADECIA Ceiling Solution](https://uc.yamaha.com/products/microphone-systems/adecia/)|1.2.0|
|[Yamaha ADECIA Tabletop Solution](https://uc.yamaha.com/products/adecia/adecia-tabletop/)|E1.2.0 for table mic, D1.2.0 for processor (Both same content as V1.5.1)|
|[Yealink CP900](https://www.yealink.com/products_150.html) |100.20.0.29 |
|[Yealink UVC30](https://www.yealink.com/product/microsoft-teams-room-system-uvc30)| 105.420.0.11 |  &#x2714; |
|[Yealink UVC34 All-in-one video bar](https://www.yealink.com/product/usb-videobar-uvc34) | 265.410.0.9 |
|[Yealink UVC40 All-in-one Video bar](https://www.yealink.com/product/usb-videobar-uvc40) |128.410.0.10|  
|[Yealink UVC84](https://www.yealink.com/product/camera-uvc84) |262.410.0.10|
|[Yealink UVC86]( https://www.yealink.com/product/camera-uvc86) |151.410.0.5|
|[Shure Intellimix P300 Audio Conferencing Processor](https://www.shure.com/products/mixers/p300)+</br>[Shure MXA 310 Table Array Mic ](https://www.shure.com/products/microphones/mxa310) | 4.1 |
|[Shure Intellimix P300 Audio Conferencing Processor](https://www.shure.com/products/mixers/p300) +</br>[Shure MXA 910 with Intellimix Ceiling Array Mic](https://www.shure.com/products/microphones/mxa910) | 4.1|
|[Shure Intellimix P300 Audio Conferencing Processor](https://www.shure.com/products/mixers/p300)+</br>[Shure MXA 310 Table Array Mic ](https://www.shure.com/products/microphones/mxa310) +</br>[MXN5W-C Ceiling speaker](https://www.shure.com/en-US/products/loudspeakers/mxn5)| P300 DSP: 4.1.11 </br> MXA310 Table Array mic: 4.1.41 </br> MXN5W-C Speaker: 1.0.4 |
|[Shure Intellimix P300 Audio Conferencing Processor](https://www.shure.com/products/mixers/p300) + </br>[Shure MXA 920 with Intellimix Ceiling Array Mic](https://www.shure.com/en-US/products/microphones/mxa920?utm_source=linkedin&utm_medium=social&sfid=&prod=) +</br>[MXN5W-C Ceiling speaker](https://www.shure.com/en-US/products/loudspeakers/mxn5)| P300 DSP: 4.7.7 </br> MXA920 Ceiling Array mic: 1.1.56 </br> MXN5W-C Speaker: 1.5.6 |
|ANIUSB + </br> [Shure MXA 920 with Intellimix Ceiling Array Mic](https://www.shure.com/en-US/products/microphones/mxa920?utm_source=linkedin&utm_medium=social&sfid=&prod=) +</br>[MXN5 Ceiling speaker](https://www.shure.com/en-US/products/loudspeakers/mxn5)| ANIUSB: 4.4.7 </br> MXA920: 1.1.56 </br> MXN5: 1.5.6|
|[Shure MXA 710 2ft Table Linear Array Microphone](https://www.shure.com/products/microphones/mxa710) + </br>[Shure Intellimix P300 Audio Conferencing Processor](https://www.shure.com/products/mixers/p300) +</br>[MXN5-C Ceiling Speaker](https://www.shure.com/en-US/products/loudspeakers/mxn5)| MXA710 2ft Table Linear Array Mic: 1.2.0 </br> P300 DSP: 4.4.8 </br> MXN5-C Speaker: 1.1.1 |
|[Shure MXA 710 4ft Wall Linear Array Microphone](https://www.shure.com/products/microphones/mxa710) + </br>[Shure Intellimix P300 Audio Conferencing Processor](https://www.shure.com/products/mixers/p300) +</br>[MXN5-C Ceiling Speaker](https://www.shure.com/en-US/products/loudspeakers/mxn5)| MXA710 4ft Wall Linear Array Mic: 1.2.0 </br> P300 DSP: 4.4.8 </br> MXN5-C Speaker: 1.1.1 |
|[Shure MXA 910 with Intellimix Ceiling Array Microphone](https://www.shure.com/products/microphones/mxa910) + </br> [Shure Intellimix Room Software](https://www.shure.com/products/software/intellimix_room) +</br> [Crestron UC-C100-T](https://www.crestron.com/Products/Workspace-Solutions/Unified-Communications/Crestron-Flex-Integrator-Kits/UC-C100-T)| Shure Intellimix Room Software: 3.0.4.14 </br> Shure MXA 910 with Intellimix Ceiling Array Microphone: 4.4.11 </br> Shure MXN5-C Speakers: 1.2.1 </br> Crestron UC-C100-T with ASUS Tek Computer INC 9934 compute | 
|[Shure MXA 910 with Intellimix Ceiling Array Microphone](https://www.shure.com/products/microphones/mxa910) + </br> [Shure Intellimix Room Software](https://www.shure.com/products/software/intellimix_room) +</br>Lenovo ThinkSmart Core | Shure Intellimix Room Software: 3.2.0.52 </br> Shure MXA 910 with Intellimix Ceiling Array Microphone: 4.4.11 </br> Shure MXN5-C Speakers: 1.2.1 </br> Lenovo ThinkSmart Core: Windows IoT 19h2/20h2 OS version |
|[Sennheiser TeamConnect Intelligent Speaker/TC ISP (T-Rock)](https://en-us.sennheiser.com/tcisp)|1.0.2|
|[Biamp Tesira Fore AVB VT4 Fixed audio DSP](https://www.biamp.com/products/tesira-fixed-audio-dsp)+ &Dagger;</br>[Sennheiser TeamConnect Ceiling 2 Microphone](https://sennheiser.com/tcc2)+ &Dagger;</br>[Tesira EX-UBT](https://www.biamp.com/products/tesira/tesira-expanders) &Dagger; |  Biamp DSP: 3.12.0.15 </br> TCC2: 1.3.3 </br>EX-UBT: 3.12.0.15 |
|[Biamp Tesira FORTÉ AVB VT4 Audio DSP](https://www.biamp.com/products/tesira-fixed-audio-dsp)+</br>[Biamp Parlé TCM-XA Ceiling Microphone](https://www.biamp.com/products/product-families/parle/parle-microphones)+</br>[Biamp Desono C-IC6 ceiling mounted loudspeaker](https://www.biamp.com/products/tesira-speakers)| Audio FW version: 3.15|
|[Biamp TesiraFORTE AVB VT4](https://www.biamp.com/products/tesira-fixed-audio-dsp)+ </br>[Parle TTM-X(Table Mic)](https://www.biamp.com/products/product-families/parle/parle-microphones)+</br>[Ex-UBT]() |Audio FW version: 3.15|
|Biamp Tesira FORTE X Series +</br>[Devio SCX Series](https://www.biamp.com/products/product-families/devio/medium-large-room-solutions#devio-scx-400)|Tesira FORTE X Series: 4.2.5 </br> Devio SCX Series: 4.2.5|
|[Bose ControlSpace EX-440C DSP + </br>Bose P2600A AmpLink Amplifier +</br> Sennheiser TCC2 Ceiling Microphone + </br> Bose EdgeMax EM180 Ceiling Speaker](https://pro.bose.com/en_us/solutions/bose-work/es1-ceiling-audio-solution.html)|  Bose DSP: 2.290  </br> P2600A: 1.160  </br> TCC2: 1.4.2  |  |
|[Bose ControlSpace EX-440C DSP + </br>Bose P2600A AmpLink Amplifier + Sennheiser TCC2 Ceiling Microphone + </br> Bose DesignMax DM2C-P Ceiling Speaker](https://pro.bose.com/en_us/solutions/bose-work/es1-ceiling-audio-solution.html)|  Bose DSP: 2.290  </br> P2600A: 1.160  </br> TCC2: 1.4.2  |  |
|[Bose ControlSpace EX-1280C DSP](https://pro.bose.com/en_us/products/signal_processing_and_networking/controlspace_ex/cs_ex_1280c.html#v=cs_ex_1280c_black) +</br>Bose P2600A AmpLink Amplifier +</br> [Sennheiser TCC2 Ceiling Microphone](https://pro.bose.com/en_us/solutions/bose-work/es1-ceiling-audio-solution.html) +</br> [DesignMax DM2C -LP  Ceiling Speaker](https://pro.bose.com/en_us/products/loudspeakers/background_foreground/designmax/designmax_dm2c_lp.html#v=designmax_dm2c_lp_black) | Bose DSP: 2.290  </br> P2600A: 1.160  </br> TCC2: 1.4.2  | 
|[Bose ControlSpace EX-1280C DSP](https://pro.bose.com/en_us/products/signal_processing_and_networking/controlspace_ex/cs_ex_1280c.html#v=cs_ex_1280c_black) +</br>Bose P2600A AmpLink Amplifier+</br> [Sennheiser TCC2 Ceiling Microphone](https://pro.bose.com/en_us/solutions/bose-work/es1-ceiling-audio-solution.html) +</br> [EdgeMax EM180 Ceiling Speaker](https://pro.bose.com/en_us/products/loudspeakers/background_foreground/edgemax/edgemax_em180.html#v=edgemax_em180_white) | Bose DSP: 2.290  </br> P2600A: 1.160  </br> TCC2: 1.4.2  |
|QSC Q-SYS Core ([110f](https://www.qsc.com/solutions-products/q-sys-ecosystem/processing/core-110f/), [8 Flex](https://www.qsc.com/solutions-products/q-sys-ecosystem/processing/core-8-flex/), [Nano](https://www.qsc.com/solutions-products/q-sys-ecosystem/processing/core-nano/), or [NV-32-H](https://www.qsc.com/solutions-products/q-sys-ecosystem/processing/nv-32-h-core-capable/)) + </br> [Sennheiser TCC2 Ceiling Microphone](https://en-us.sennheiser.com/tcc2) + </br> QSC Amplifier ([SPA series](https://www.qsc.com/solutions-products/power-amplifiers/installed/non-network/low-power-applications/spa-series/) or [CX-Q series](https://www.qsc.com/solutions-products/power-amplifiers/installed/network/cx-q-series/)) + </br> [QSC AcousticDesign Series Speakers](https://www.qsc.com/solutions-products/loudspeakers/installed/passive/solutions/acousticdesigntm-series-solutions/) + </br> QSC IP Camera ([PTZ-IP 20x60](https://www.qsc.com/solutions-products/q-sys-ecosystem/video/ptz-ip-conference-cameras/), [PTZ-IP 12x72](https://www.qsc.com/solutions-products/q-sys-ecosystem/video/ptz-ip-conference-cameras/)) optional + </br> [QSC Q-SYS I/O USB Bridge](https://www.qsc.com/solutions-products/q-sys-ecosystem/audio-io-peripherals/io-usb-bridge/) optional | QSC Q-SYS Core, PTZ-IP Camera, and I/O USB Bridge: QSC Q-SYS Designer 9.0.1-2104.022 </br> Sennheiser TCC2 Ceiling Microphone: TCC2 - 1.5.1, Dante 1.2.0 </br> QSC Amplifiers: N/A </br> QSC AcousticDesign Series Loudspeakers: N/A | 


&Dagger; Customers may choose either the Dante interface or the network switch recommended by Biamp/Sennheiser for this bundle.

#### USB extenders

- USB ports on tablet docks are USB 3.0 compatible. You can use a USB 2.x extender but you'll be limited to USB 2.x speeds on the far end. Extenders are not recommended for USB 3.0 peripherals.
- An extender must meet USB 2.0 or newer specifications.
  - Tablet docks support at least two stages of external USB hub extension. If you connect more than two USB hubs in series, check with the dock manufacturer to confirm whether they support series connection.
  - Wired GbE connection in the room. Ethernet cable of appropriate length.
  - Up to two 1080p displays with HDMI connections. HDMI cables of appropriate length.

> [!NOTE]
> A consumer TV used as a front of room display needs to support/enable the Consumer Electronics Control (CEC) feature of HDMI so that it can switch automatically to an active video source from standby mode. This feature is not supported on all TVs.
>
> Microsoft Teams Rooms does not use a keyboard. If needed, the Admin should use the on-screen keyboard. A USB keyboard or mouse will be required when imaging the Microsoft Teams Rooms device.

The following tables provide recommendations for peripherals based on room size:

**Microsoft Teams Rooms Certified Audio Peripherals**

|Room Type|Number of People|Recommended maximum distance from microphone to speaker|
|:-----|:-----|:-----|
|**Focus** <br/> 10' x 9'   |2–4  |1.5 m  |
|**Small** <br/> 16' x 16'  |4–6  |2.0 m  |
|**Medium** <br/> 18' x 20'  |6–12  |2.4 m  |
|**Large** <br/> 15' x 32'  |12–16  |3 m <br/> This distance also applies to the area covered by each connected satellite microphone.  |

**Microsoft Teams Rooms Certified Video Peripherals**

|Room Type|Number of People|
|:-----|:-----|
|**Focus** <br/> 10' x 9'  |2–4  |
|**Small** <br/> 16' x 16'  |4–6  |
|**Medium** <br/> 18' x 20'  |6–12  |
|**Large** <br/> 15' x 32'  |12–16  |

 > [!NOTE]
 > Front of room display resolution should be set to no greater than 1920x1080p.


## See also

[Browse All Bundles](https://products.office.com/microsoft-teams/across-devices/devices)

[Plan for Microsoft Teams Rooms](rooms-plan.md)

[Deploy Microsoft Teams Rooms](rooms-deploy.md)

[Configure a Microsoft Teams Rooms console](console.md)

[Manage Microsoft Teams Rooms](rooms-manage.md)
