---
title: "Microsoft Teams Rooms licenses"
ms.author: v-lanac
author: lanachin
manager: serdars
ms.reviewer: sohailta
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: 
  - M365-collaboration
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
localization_priority: Normal
f1.keywords:
- NOCSH
ms.custom: 
  - Licensing
  - LIL_Placement
  - seo-marvel-apr2020
description: Learn about the available licenses for different types of calling and meeting features in Microsoft Teams Rooms. 
---

# Teams Meeting Room Licensing Update

## Licensing Solutions for Shared Communication Devices

Microsoft has a dedicated SKU for licensing meetings and calling on a per-device basis for meeting room devices (such as Microsoft Teams Rooms, Microsoft Surface Hub, and collaboration bars for Microsoft Teams).

||Meeting Room SKU |  
|:--- |:---: |
|Skype for Business |&#x2714;|
|Microsoft Teams|  &#x2714;|
|Phone System|  &#x2714;|
|Audio Conferencing|&#x2714; &sup1;|
|Microsoft Intune|&#x2714;|  
|Worldwide Availability | &#x2714; &sup2;|
|Channel Availability | EA, EAS, CSP, <br/>Web Direct |
| | | |

&sup1; Availability and included minutes may vary by region. To verify service availability, refer to  [Country and region availability for Audio Conferencing and Calling Plans](https://docs.microsoft.com/microsoftteams/country-and-region-availability-for-audio-conferencing-and-calling-plans). Consumption charges may apply for additional services, such as toll-free, international minutes for domestic plans, etc. Customers can disable these features to avoid additional billing.  

&sup2; Not available in sovereign clouds  


> [!NOTE]
> If you are currently using E1, E3, E4, E5 SKUs with Skype for Business Plan 2 with Audio Conferencing or with Office 365 Phone System and a Calling Plan, these will continue to work. However, you should consider moving to a simpler licensing model in the table above after current licenses expire.

> [!IMPORTANT]
> If you are using Skype for Business Plan 2, you can only use the Microsoft Teams Rooms in Skype for Business Only mode, meaning all of your meetings will be Skype for Business meetings. In order to enable your meeting room for Microsoft Teams meetings, we recommend you purchase the Meeting Room license. 

The following table lists the features that are available in Microsoft Teams Rooms and what licenses you need to buy to get them.
  
> [!NOTE]
> The room that is being set up needs to be a user object and have these licenses assigned to it.

|  | You have Microsoft Teams or Skype for Business Online <br/> Here's what you need to buy:   |You have Skype for Business Server 2015/2019 (on-premises or hybrid). <br/> Here's what you need to buy:|
|:-----|:-----|:-----|
|Join a scheduled meeting  | Meeting Room SKU  |Skype for Business Server Standard CAL  |
|Initiate an ad hoc meeting | Meeting Room SKU  |Skype for Business Server Standard CAL  <br/> Skype for Business Server Enterprise CAL|
|Initiate an ad hoc meeting and dial out from a meeting to phone numbers |  Meeting Room SKU |Skype for Business Standard CAL  <br/> Skype for Business Server Enterprise CAL|
|Give the room a phone number and make or receive a calls from the room or join an audio conference using a phone number  | Meeting Room SKU<br/>Without Direct Routing: Domestic or International Calling Plan is also required  |Skype for Business Server Standard CAL  <br/> Skype for Business Server Plus CAL  |
|Manage your room device with Microsoft Intune |Meeting Room SKU  |Microsoft Intune subscription with [on-premises MDM](https://docs.microsoft.com/configmgr/mdm/plan-design/plan-on-premises-mdm) |
| |||

> [!NOTE]
> If you have existing licenses assigned for room systems, these will continue to work without any interruption. You should move to use the new Meeting Room SKU when existing licenses expire.  

 **Use the right version of Windows 10**: For customers who want to deploy Windows 10 images to their devices, see [Configure a Microsoft Teams Rooms console](https://docs.microsoft.com/microsoftteams/room-systems/console). You can get a copy from the [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/).
