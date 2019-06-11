---
title: "Microsoft Teams Rooms licenses"
ms.author: v-lanac
author: lanachin
manager: serdars
ms.reviewer: davgroom
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: 
- Adm_Skype4B_Online
- Strat_SB_PSTN
- M365-voice
audience: Admin
appliesto:
- Skype for Business 
localization_priority: Normal
f1keywords: None
ms.custom:
- Licensing
- LIL_Placement
description: "Learn about features available in Microsoft Teams Rooms. "
---

# Teams Meeting Room Licensing Update 

## Licensing Solutions for Shared Communication Devices 

Microsoft has two SKUs for licensing meetings and calling on a per-device basis - one for meeting room devices (such as Microsoft Teams Rooms) and one for common area phones (such as lobby phones available for guest use).


|   |Meeting Room | Common Area Phone   |
|:--- |:---: |:---: |
|Skype for Business |&#x2714;  |&#x2714;  |
|Microsoft Teams      |  &#x2714;       |    &#x2714;     |
|Phone Systems      |  &#x2714;       |      &#x2714;   |
|Audio Conferencing      |  &#x2714; &sup1;      |     &#x2718; &sup2;   |
|Microsoft Intune      |    &#x2714;     |   &#x2718;   &sup3;   |
|Worldwide Availability | &#x2714; &sup3;       |   &#x2714;      |
|Channel Availability | EA, EAS, CSP, <br>Web Direct | EA, EAS, CSP, GCC,<br> EES, Web Direct |
| | | |

&sup1; Availability and included minutes may vary by region. To verify service availability, refer to  [Country and region availability for Audio Conferencing and Calling Plans](http://docs.microsoft.com/microsoftteams/country-and-region-availability-for-audio-conferencing-and-calling-plans). Consumption charges may apply for additional services, such as toll-free, international minutes for domestic plans, etc. Customers can disable these features to avoid additional billing.  

&sup2; Common Area Phones can join audio conferences via dial-in number provided by the meeting organizer 

&sup3; Not available in sovereign clouds  


> [!NOTE]
> If you are currently using E1, E3, E4, E5 SKUs with Skype for Business Standalone Plan 1 or Skype for Business Plan 2 or Skype for Business Plan 2 with Audio conferencing or with Office365 Phone System and a Calling Plan, these will continue to work. However, you should consider moving to a simpler licensing model in the table above after current licenses expire.  

The following table lists the features that are available in Microsoft Teams Rooms and what licenses you need to buy to get them.
  
> [!NOTE]
> The room that is being set up needs to be a user object and have these licenses assigned to it.

|  | You have Microsoft Teams or Skype for Business Online <br/> Here's what you need to buy:   |You have Skype for Business Server 2015/2019 (on-premises or hybrid). <br/> Here's what you need to buy:|
|:-----|:-----|:-----|
|Join a scheduled meeting  | Meeting Room SKU  |Skype for Business Server Standard CAL  |
|Initiate an ad-hoc meeting | Meeting Room SKU  |Skype for Business Server Standard CAL  <br/> Skype for Business Server Enterprise CAL|
|Initiate an ad-hoc meeting and dial out from a meeting to phone numbers |  Meeting Room SKU |Skype for Business Standard CAL  <br/> Skype for Business Server Enterprise CAL|
|Give the room a phone number and make or receive a calls from the room or join an audio conference using a phone number  | Meeting Room SKU  |Skype for Business Server Standard CAL  <br/> Skype for Business Server Plus CAL  |
|Mange your room device with Microsoft Intune |Meeting Room SKU  |Microsoft Intune subscription with [on premise MDM](https://docs.microsoft.com/sccm/mdm/plan-design/plan-on-premises-mdm) |
| |||

> [!NOTE]
> If you have existing licenses assigned for room systems, these will continue to work without any interruption. You should move to use the new Meeting Room SKU when existing licenses expire.  

 **Use the right version of Windows 10**: For customers who want to deploy Windows 10 images to their devices, see [Configure a Microsoft Teams Rooms console](https://docs.microsoft.com/microsoftteams/room-systems/console). You can get a copy from the [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/).
