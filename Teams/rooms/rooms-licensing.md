---
title: Microsoft Teams Rooms licenses
ms.author: dstrome
author: dstrome
manager: serdars
ms.reviewer: sohailta
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Rooms
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - NOCSH
ms.custom: 
  - Licensing
  - LIL_Placement
  - seo-marvel-apr2020
description: Learn about the available licenses for different types of calling and meeting features in Microsoft Teams Rooms.
---

# Microsoft Teams Rooms licenses

## Service plan availability

Microsoft has two dedicated SKUs for licensing meetings and calling on a per-device basis for meeting room devices (such as Microsoft Teams Rooms, Microsoft Surface Hub, and collaboration bars for Microsoft Teams).

You can assign up to 20 Microsoft Teams Rooms Basic licenses to Teams Rooms devices in your organization. If you need to license more than 20 devices, you need to purchase Microsoft Teams Rooms Pro licenses.

|                                           | Microsoft Teams Rooms Basic                                          | Microsoft Teams Rooms Pro                                              |
|:------------------------------------------|:--------------------------------------------------------------------:|:----------------------------------------------------------------------:|
| **Microsoft Teams**                       | &#x2714;                                                             | &#x2714;                                                               |
| **Audio Conferencing<sup>1</sup>**        | &#x2714;                                                             | &#x2714;                                                               |
| **Whiteboard**                            | &#x2714;                                                             | &#x2714;                                                               |
| **Teams Phone**                           |                                                                      | &#x2714;                                                               |
| **Microsoft Intune**                      |                                                                      | &#x2714;                                                               |
| **Skype for Business Plan 2<sup>2</sup>** |                                                                      | &#x2714;                                                               |
| **Segment availability**                  | Commercial, WorldWide Public Sector, Education, Charity, GCC         | Commercial, WorldWide Public Sector, Education, Charity, GCC, GCC-High |
| **Channel availability**                  | Web Direct, New commerce experience (NCE) - Customer led<sup>3</sup> | EA, EAS, EES, CSP, Web Direct, NCE - Customer led, NCE - Partner led   |

<sup>1</sup> To verify service availability, see [Country and region availability for Audio Conferencing and Calling Plans](../country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md). [Communication Credits](../what-are-communications-credits.md) may apply for additional services, such as toll-free, international minutes for domestic plans, and so on. You can disable these features to avoid additional billing.

<sup>2</sup> Included to enable certain legacy authentication methods.

<sup>3</sup> At launch, you'll need to add and assign a $0 Teams Rooms Basic license for each device via their admin portal. In the future (timing TBD) licenses will be automatically assigned to new devices at initial log-in.

The following table lists the features that are available in Microsoft Teams Rooms and what licenses you need to buy to get them.
  
> [!NOTE]
> The room that is being set up needs to be a user object and have these licenses assigned to it.

| &nbsp; | You have Microsoft Teams. <br/> Here's what you need to buy:   |You have Skype for Business Server 2015/2019 (on-premises). <br/> Here's what you need to buy:|
|:-----|:-----|:-----|
|Join a scheduled meeting  | Microsoft Teams Rooms Standard or Premium  |Skype for Business Server Standard CAL  |
|Initiate an ad hoc meeting | Microsoft Teams Rooms Standard or Premium  |Skype for Business Server Standard CAL  <br/> Skype for Business Server Enterprise CAL|
|Initiate an ad hoc meeting and dial out from a meeting to phone numbers |  Microsoft Teams Rooms Standard or Premium |Skype for Business Standard CAL  <br/> Skype for Business Server Enterprise CAL|
|Give the room a phone number and make or receive a call from the room or join an audio conference using a phone number  | With Direct Routing and/or Operator Connect: Microsoft Teams Rooms Standard or Premium<br/>Without Direct Routing or Operator Connect: Domestic or International Calling Plan<br/>Microsoft 365 Business Voice  |Skype for Business Server Standard CAL  <br/> Skype for Business Server Plus CAL  |
|Manage your room device with Microsoft Intune |Microsoft Teams Rooms Standard or Premium  |Microsoft Intune subscription with [on-premises MDM](/configmgr/mdm/plan-design/plan-on-premises-mdm) |
|Microsoft Teams Rooms Managed Services | Microsoft Teams Rooms Premium ||

You can read [Set up the Common Area Phone license for Microsoft Teams](../set-up-common-area-phones.md) for information on licensing Common Area Phones.

## Teams Rooms console and Teams client feature availability

### Meeting join

|                                                                 | Microsoft Teams Rooms Basic | Microsoft Teams Rooms Pro |
|:----------------------------------------------------------------|:---------------------------:|:-------------------------:|
| **Join Teams meetings with 1-touch, proximity, and meeting ID** | &#x2714;                    | &#x2714;                  |
| **Start ad hoc meetings from the room**                         | &#x2714;                    | &#x2714;                  |
| **Direct Guest Join for Zoom and Webex meetings**               | &#x2714;                    | &#x2714;                  |
| **Join meetings across Teams clouds**                           |                             | &#x2714;                  |
| **Room checking with Teams Panel**                              |                             | &#x2714;                  |

### Share and collaborate

|                                                  | Microsoft Teams Rooms Basic | Microsoft Teams Rooms Pro |
|:-------------------------------------------------|:---------------------------:|:-------------------------:|
| **Share and view all Teams content types**       | &#x2714;                    | &#x2714;                  |
| **Share whiteboard with Content Capture Camera** |                             | &#x2714;                  |

### Meeting engagement

|                                                      | Microsoft Teams Rooms Basic | Microsoft Teams Rooms Pro |
|:-----------------------------------------------------|:---------------------------:|:-------------------------:|
| **Teams video gallery with multiple layout options** | &#x2714;                    | &#x2714;                  |
| **Front row**                                        |                             | &#x2714;                  |
| **Together mode**                                    |                             | &#x2714;                  |
| **Large gallery (up to 50 videos)**                  |                             | &#x2714;                  |
| **Split gallery across two screen**                  |                             | &#x2714;                  |

### Calling

|                                                   | Microsoft Teams Rooms Basic | Microsoft Teams Rooms Pro |
|:--------------------------------------------------|:---------------------------:|:-------------------------:|
| **Make and receive peer to peer and group calls** | &#x2714;                    | &#x2714;                  |
| **Microsoft 365 Phone System**                    |                             | &#x2714;                  |

### Intelligent audio and video

|                                                                                 | Microsoft Teams Rooms Basic | Microsoft Teams Rooms Pro |
|:--------------------------------------------------------------------------------|:---------------------------:|:-------------------------:|
| **Support for Intelligent Speaker live transcript with speaker identification** |                             | &#x2714;                  |
| **Multi-camera support**                                                        |                             | &#x2714;                  |
| **Panoramic room view**                                                         |                             | &#x2714;                  |
| **AI noise suppression**                                                        |                             | &#x2714;                  |
| **People counting**                                                             |                             | &#x2714;                  |

### Security and compliance

|                                                                     | Microsoft Teams Rooms Basic | Microsoft Teams Rooms Pro |
|:--------------------------------------------------------------------|:---------------------------:|:-------------------------:|
| **Secure operating system**                                         | &#x2714;                    | &#x2714;                  |
| **System level security (Secure boot, Assigned Access mode, etc.)** | &#x2714;                    | &#x2714;                  |
| **Azure AD condition access policies**                              |                             | &#x2714;                  |

### Device management

|                                                   | Microsoft Teams Rooms Basic | Microsoft Teams Rooms Pro |
|:--------------------------------------------------|:---------------------------:|:-------------------------:|
| **Teams Admin Center enrollment and inventory**   | &#x2714;                    | &#x2714;                  |
| **Automatic software updates**                    | &#x2714;                    | &#x2714;                  |
| **Detailed system and configuration information** |                             | &#x2714;                  |
| **Peripheral health management**                  |                             | &#x2714;                  |
| **Remote configuration**                          |                             | &#x2714;                  |
| **Device history and activity**                   |                             | &#x2714;                  |
| **ITSM integration**                              |                             | &#x2714;                  |
| **Custom health alerts**                          |                             | &#x2714;                  |
| **Device analytics**                              |                             | &#x2714;                  |

## Teams admin center feature availability

|                                               | Microsoft Teams Rooms Basic | Microsoft Teams Rooms Pro |
|:----------------------------------------------|:---------------------------:|:-------------------------:|
| **Automatic device updates**                  | &#x2714;                    | &#x2714;                  |
| **Basic device analytics**                    | &#x2714;                    | &#x2714;                  |
| **Basic device health**                       | &#x2714;                    | &#x2714;                  |
| **Call quality dashboard**                    | &#x2714;                    | &#x2714;                  |
| **Create and view workspaces**                | &#x2714;                    | &#x2714;                  |
| **Real-time telemetry**                       | &#x2714;                    | &#x2714;                  |
| **Regular feature updates**                   | &#x2714;                    | &#x2714;                  |
| **Remote sign-in and sign-out**               | &#x2714;                    | &#x2714;                  |
| **Android device configurations**             |                             | &#x2714;                  |
| **Device alerts**                             |                             | &#x2714;                  |
| **Device analytics - health and utilization** |                             | &#x2714;                  |
| **Device detail view**                        |                             | &#x2714;                  |
| **Device health details**                     |                             | &#x2714;                  |
| **Device tags**                               |                             | &#x2714;                  |
| **Graph APIs**                                |                             | &#x2714;                  |
| **Manual device updates**                     |                             | &#x2714;                  |
| **Remote restart**                            |                             | &#x2714;                  |
| **Windows device peripherals management**     |                             | &#x2714;                  |
| **Windows device settings**                   |                             | &#x2714;                  |
