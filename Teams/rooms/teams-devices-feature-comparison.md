---
title: "Teams devices for shared spaces feature comparison between Windows and Android"
author: amandafrechinjackson
ms.author: v-amandaf
manager: jsarrasin
ms.date: 9/30/2021
ms.topic: conceptual
audience: ITPro
ms.service: msteams
search.appverid: MET150 
ms.reviewer: 
description: A guide comparing the Teams devices for shared spaces features between Windows and Android.
ms.collection: 
  - M365-voice
  - M365-collaboration
  - skype-for-business-itpro
  - skype-for-business-online
f1.keywords:
- NOCSH
localization_priority: Normal
appliesto: 
  - Microsoft Teams
---

# Teams devices for shared spaces feature comparison between Windows and Android 
This document compares the features of Teams devices between Windows and Android versions. These features and specifications are current as of September 2021.

**Table key:** 

● Available

◔ Coming soon 

○ Not available  

|                  |Features |Teams Rooms (Windows)|Teams Rooms (Android) as shared device|
|------------------|---------|--------|--------|
|**Join a Teams Meeting**|One-touch-join scheduled Teams meeting  |●  |● |
||Proximity-based Teams meeting join |●  |● |
||Meet Now/Ad-hoc Teams meeting |●  |● |
||Join Teams webinar meeting |●  |● |
|**Join other meetings**|One-touch-join scheduled Cisco Webex meeting |●  |◔ |
||One-touch-join scheduled Zoom meeting |●  |◔ |
||Join via SIP URI |●  |○ |
||One-touch-join scheduled Skype for Business meeting |●  |○ |
||Meet Now/Ad-hoc Skype for Business meeting |●  |○ |
|**Out-of-meeting experiences**|Share content via HDMI |●  |● |
||Share content via wireless casting |●  |● |
||Share HDMI audio |●  |○ |
||Duplicate content on both displays |●  |○ |
||Room controls (OEMs) |●  |○ |
||Accessibility – high contrast |●  |● (Yealink, Poly, EPOS)|
||Accessibility – magnifier |●  |● (Yealink, Poly, EPOS)|
||Accessibility – narrator |●  |◔ |
||Built-in themes/wallpapers |●  |◔ |
||Custom themes/wallpapers |●  |◔ |
|**Calendar**|External Teams meetings (parsing) |●  |● |
||External Teams meetings (safelink) |●  |○ |
||Private meetings |●  |● |
||Hide meeting names (for privacy) |●  |● |
|**Meeting engagement and inclusivity**|Video gallery (3x3) |●  |● |
||Together mode |●  |● |
||Large gallery (up to 50 videos) |●  |● |
||Dynamic gallery |●  |● |
||Dual display support |●  |● |
||Split gallery across two screens |●  |◔ |
||Local layouts (Content, Gallery, Combined) |●  |● |
||Chat bubbles |●  |◔ |
||Meeting reactions (control and consume) |●  |◔ |
||Pin multiple participants |●  |◔ |
||Spotlight multiple participants |●  |◔ |
||Raise Hand or Lower all hands |●  |● |
||Coordinated meeting join (with Surface Hub) |●  |○ |
||Presenter Mode (consume) |●  |◔ |
||View panoramic video from room |●  |○ |
||Join Live event as presenter |●  |○ |
|**Intelligence and collaboration**|Video-based screen-share (VbSS) content sharing |●  |● |
||Optimize bandwidth dynamically |●  |● |
||View and use Microsoft Whiteboard (touchscreen required) |●  |● |
||Intelligent content capture |●  |◔ |
||Live closed captions |●  |● |
||Cortana voice skills |●  |◔ |
||Call quality dashboard in Teams Admin Center |●  |● |
||Room remote |●  |● |
||Remote PTZ |●  |◔ |
||Speaker attribution with intelligent speakers |●  |○ |
|**Meeting and device controls**|Meeting participants roster (grouping, raised-hand sorting) |●  |● |
||Search and add participant to meeting/call (Tenant) |●  |● |
||Search and add a federated user to the meeting/call |●  |● |
||Remove participant from meeting |●  |● |
||Mute all (including muting a group) |●  |● |
||Hard mute and request to speak |●  |◔ |
||Ability to un-mute all attendees (audio/video) |●  |◔ |
||Lock Teams meeting for organizers/co-organizers |●  |● |
||Supported video resolution |1080p, 30 FPS |1080p, 30 FPS |
||Supported content resolution |1080p, 30 FPS |1080p, 30 FPS |
||Large meetings support |●  |● |
||Attendee, presenter, and organizer roles (structured meetings) |●  |● |
|**Teams Calling**|Microsoft 365 Audio Conferencing |●  |● |
||Microsoft 365 Phone System |●  |● |
||PSTN Calling |●  |● |
||Make a P2P call |●  |● |
||Make a group call |●  |● |
||Escalate call to meeting |●  |● |
||Teams Emergency Calling |●  |● |
||Federated tenant call |●  |● |
||Skype for Business interop audio calls |●  |● |
|**Security and Compliance**|Secure mounting, security lock slot (Kensington lock), I/O ports access |●  |● |
||Operating System |Windows 10 |Android 8.1+ |
||OS security features |TPM 2.0, disable specific ports, secure boot, Credential Guard, OOBE setting access control, direct memory access protection, network security |Android full disc encryption, OEM-specific features |
||Kiosk mode |●  |● |
||MEM enrollment |●  |● |
||MEM configuration profiles |●  |● |
||File-based encryption |● (via MEM) |● |
||Azure AD Conditional Access |●  |● |
||Limited Bluetooth exposure for beaconing only (PDU) |●  |● |
|**Device management**|Device inventory |●  |● |
||Custom tagging |●  |● |
||Overall device health monitoring |●  |● |
||Connected peripheral health monitoring |●  |◔ |
||Remote configuration (restart, settings, log collection) |●  |● |
||Bulk device management |●  |● |
||Application update management |●  |● |
||Role-based access control (RBAC) (Teams device admin) |●  |● |
||Admin on behalf of (AoBo) support through partner center |●  |● |
||Device management alerts (offline) |●  |● |
||ITSM provider notification through Webhooks |●  |● |
||Peripheral health impact management |●  |◔ |
||Call quality and performance reporting |●  |● |
||Adjustable default volume |●  |○ |
|**Hardware ecosystem**|MTR solution OEM partners |Crestron, HP, Lenovo, Logitech, Poly, Yealink [(details)](/microsoftteams/rooms/requirements) |Logitech, Poly, Yealink, AudioCodes, EPOS |
||USB video cameras |●  |◔ |
||USB audio devices |●  |◔ |
||DSP (digital signal processor) audio devices |●  |◔ |
||IP audio devices |●  |◔ |
||Audio-video partner peripherals |● |Aver, EPOS, Biamp, Bose, Huddly, Jabra, Lenovo, Logitech, Nureva, Poly, QSC, Shure, Sennheiser, Yamaha, Yealink [(details)](/microsoftteams/rooms/requirements) |
||USB content cameras |Logitech, Huddly, Crestron, Yealink, Jabra |◔ |
||HDMI outputs |2 outputs |1 or 2 outputs |
||HDMI ingests |1 ingest |Varies with OEM |
||USB 3.0 ports |4 ports |At least 2 ports |
||Audio port (headphone/mic jack) |1 |Not required |
||Ethernet (LAN of GbE) |1 |1 |
||CPU |Dual core, 1.6+ GHz with Turbo boost, 15W+ TDP  |64-bit ARMv8-A architecture CPU with 8 or more cores, 70K DMIPS or higher |
||GPU |Hardware accelerated H/264 decoding/encoding, MJPEG decoding support, and DXVA compatible |4x1080P/30fps H.264 decoding, 2x1080P/30 + 2x720P/30 encoding |
||RAM |8 GB+ |4 GB or above |
||Storage |120 GB+ SSD |8 GB or above |
||Touchscreen console |7”+ with a minimum resolution of 1280x800 |7” to 11” with 1280x720 or higher resolution |
||Motion sensor |● |● |
||Bluetooth |Bluetooth 4.1+ with dual mode (BR/EDR + LE) |Bluetooth 5.0 with dual mode (BR/EDR + LE) |
|**Good for/Space**|Focus (2-4 people) |●  |● |
||Small (4-6 people) |●  |● |
||Medium (6-12 people) |●  |● |
||Large (12-16 people) |●  |◔ |
||MPR (multi-purpose room) (16+ people) |●  |○ |