---
title: "Microsoft Teams Rooms licenses"
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

Microsoft has two dedicated SKUs for licensing meetings and calling on a per-device basis for meeting room devices (such as Microsoft Teams Rooms, Microsoft Surface Hub, and collaboration bars for Microsoft Teams).

|Feature |Microsoft Teams Rooms Standard |Microsoft Teams Rooms Premium |
|:--- |:---: |:---: |
|Skype for Business |&#x2714;| &#x2714;|
|Microsoft Teams|  &#x2714;|  &#x2714;|
|Phone System|  &#x2714;|  &#x2714;|
|Audio Conferencing|&#x2714; &sup1;|&#x2714; &sup1;|
|Microsoft Intune|&#x2714;|&#x2714;|  
|Worldwide Availability | &#x2714; &sup2;| &#x2714; &sup2;|
|Channel Availability | EA, EAS, CSP, <br/>Web Direct | EA, EAS, CSP, <br/>Web Direct |
|Managed Services | | &#x2714; &sup3;|
| | | |

&sup1; Availability and included minutes may vary by region. To verify service availability, refer to  [Country and region availability for Audio Conferencing and Calling Plans](/microsoftteams/country-and-region-availability-for-audio-conferencing-and-calling-plans). Consumption charges may apply for additional services, such as toll-free, international minutes for domestic plans, etc. Customers can disable these features to avoid additional billing.  

&sup2; Not available in sovereign clouds  

&sup3; For more information and availability, see [Microsoft Teams Rooms managed service](microsoft-teams-rooms-premium.md).

> [!NOTE]
> If you are currently using E1, E3, E4, E5 SKUs with Skype for Business Plan 2 with Audio Conferencing or with Office 365 Phone System and a Calling Plan, these will continue to work. However, you should consider moving to a simpler licensing model in the table above after current licenses expire.

> [!IMPORTANT]
> If you are using Skype for Business Plan 2, you can only use the Microsoft Teams Rooms in Skype for Business Only mode, meaning all of your meetings will be Skype for Business meetings. In order to enable your meeting room for Microsoft Teams meetings, we recommend you purchase the Meeting Room license. 

The following table lists the features that are available in Microsoft Teams Rooms and what licenses you need to buy to get them.
  
> [!NOTE]
> The room that is being set up needs to be a user object and have these licenses assigned to it.

|Activity  | You have Microsoft Teams or Skype for Business Online <br/> Here's what you need to buy:   |You have Skype for Business Server 2015/2019 (on-premises or hybrid). <br/> Here's what you need to buy:|
|:-----|:-----|:-----|
|Join a scheduled meeting  | Microsoft Teams Rooms Standard or Premium  |Skype for Business Server Standard CAL  |
|Initiate an ad hoc meeting | Microsoft Teams Rooms Standard or Premium  |Skype for Business Server Standard CAL  <br/> Skype for Business Server Enterprise CAL|
|Initiate an ad hoc meeting and dial out from a meeting to phone numbers |  Microsoft Teams Rooms Standard or Premium |Skype for Business Standard CAL  <br/> Skype for Business Server Enterprise CAL|
|Give the room a phone number and make or receive a call from the room or join an audio conference using a phone number  | With Direct Routing: Microsoft Teams Rooms Standard or Premium<br/>Without Direct Routing: Domestic or International Calling Plan<br/>Microsoft 365 Business Voice  |Skype for Business Server Standard CAL  <br/> Skype for Business Server Plus CAL  |
|Manage your room device with Microsoft Intune |Microsoft Teams Rooms Standard or Premium  |Microsoft Intune subscription with [on-premises MDM](/configmgr/mdm/plan-design/plan-on-premises-mdm) |
|Microsoft Teams Rooms Managed Services | Microsoft Teams Rooms Premium ||
| |||

> [!NOTE]
> If you have existing licenses assigned for room systems, these will continue to work without any interruption. You should move to use the new Meeting Room SKU when existing licenses expire.  

 **Use the right version of Windows 10**: For customers who want to deploy Windows 10 images to their devices, see [Configure a Microsoft Teams Rooms console](./console.md). You can get a copy from the [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/). 
 
 See also [Great meeting room experiences: Meet the new Microsoft Teams Rooms Standard and Premium](https://www.microsoft.com/microsoft-365/blog/2020/07/21/microsoft-teams-meetings-hybrid-workplace-options/).