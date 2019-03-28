---
title: "How many phone numbers can you get?"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: mikedav, roykuntz, jastark
ms.topic: conceptual
ms.assetid: 61dfb27c-5bfa-4481-a930-9c026e73ff3a
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:  
- Teams_ITAdmin_Help
- M365-voice
ms.audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Calling Plans
description: "When you are looking for and getting phone numbers for your organization, you can get more phone numbers than you have assigned licenses. But this depends on the types of phone numbers and types of licenses you have bought and assigned. You can click Different kinds of phone numbers used for Calling Plans to find out about the different phone numbers that are used in Skype for Business Online."
---

# How many phone numbers can you get?

When you are looking for and getting phone numbers for your organization, you can get more phone numbers than you have assigned licenses. But this depends on the types of phone numbers and types of licenses you have bought and assigned. You can click [Different kinds of phone numbers used for Calling Plans](different-kinds-of-phone-numbers-used-for-calling-plans.md) to find out about the different phone numbers that are used in Skype for Business Online.
  
You can see the number of phone numbers you can get on the **Phone numbers** page in the Skype for Business admin center, or you can run the [Get-CsOnlineTelephoneNumberAvailableCount](https://technet.microsoft.com/library/mt634605.aspx) cmdlet.
  
> [!IMPORTANT]
> The limits below don't include phone numbers you have ported or transferred to Microsoft. 
  
## How many phone numbers you can get?

||||
|:-----|:-----|:-----|
|**Here's the type of phone number** <br/> |**How do you get the total phone numbers?** <br/> |**Here's an example** <br/> |
|User (subscriber) number  <br/> |The number of phone numbers is equal to the total number of **Domestic Calling Plan** and/or **Domestic and International Calling Plan** licenses multiplied by 1.1 + 10 additional phone numbers. <br/> |If I have 50 users in total with either a Domestic Calling Plan and/or Domestic and International Calling Plan, you can acquire **65** phone number **(50 x 1.1 + 10)**. <br/> |
|Toll service number  <br/> | The number of phone numbers is equal to the total number of **Phone System** and **Audio Conferencing** licenses and uses the following: <br/>  If there are **1-25 licenses** then **5** telephone numbers are given. <br/>  If there are **26-49 licenses** then **10** telephone numbers are given. <br/>  If there are **50-99 licenses** then **20** telephone numbers are given. <br/>  If there are **100-149 licenses** then **30** telephone numbers are given. <br/>  If there are **150-199 licenses** then **40** telephone numbers are given. <br/>  If there are **200-499 licenses** then **65** telephone numbers are given. <br/>  If there are **500-749 licenses** then **90** telephone numbers are given. <br/>  If there are **750-999 licenses** then **110** telephone numbers are given. <br/>  If there are **1,000-1,249 licenses** then **125** telephone numbers are given. <br/>  If there are **1,250-1,499 licenses** then **135** telephone numbers are given. <br/>  If there are **1,500-1,999 licenses** then **160** telephone numbers are given. <br/>  If there are **2,000-2,999 licenses** then **210** telephone numbers are given. <br/>  If there are **3,000-6,999 licenses** then **420** telephone numbers are given. <br/>  If there are **7,000-9,999 licenses** then **500** telephone numbers are given. <br/>  If there are **10,000-14,999 licenses** then **600** telephone numbers are given. <br/>  If there are **15,000-19,999 licenses** then **700** telephone numbers are given. <br/>  If there are **20,000-49,999 licenses** then **1000** telephone numbers are given. <br/>  If there are **50,000+ licenses** then **1500** telephone numbers are given. <br/> |If you have a total of **51** **Phone System** and **Audio Conferencing** licenses, you can get **20** toll service numbers. <br/> |
|Toll-free service number  <br/> | The number of phone numbers is equal to the total number of **Phone System** and **Audio Conferencing** licenses and uses the following: <br/>  If there are **1-25 licenses** then **5** telephone numbers are given. <br/>  If there are **26-49 licenses** then **10** telephone numbers are given. <br/>  If there are **50-99 licenses** then **20** telephone numbers are given. <br/>  If there are **100-149 licenses** then **30** telephone numbers are given. <br/>  If there are **150-199 licenses** then **40** telephone numbers are given. <br/>  If there are **200-499 licenses** then **65** telephone numbers are given. <br/>  If there are **500-749 licenses** then **90** telephone numbers are given. <br/>  If there are **750-999 licenses** then **110** telephone numbers are given. <br/>  If there are **1,000-1,249 licenses** then **125** telephone numbers are given. <br/>  If there are **1,250-1,499 licenses** then **135** telephone numbers are given. <br/>  If there are **1,500-1,999 licenses** then **160** telephone numbers are given. <br/>  If there are **2,000-2,999 licenses** then **210** telephone numbers are given. <br/>  If there are **3,000-6,999 licenses** then **420** telephone numbers are given. <br/>  If there are **7,000-9,999 licenses** then **500** telephone numbers are given. <br/>  If there are **10,000-14,999 licenses** then **600** telephone numbers are given. <br/>  If there are **15,000-19,999 licenses** then **700** telephone numbers are given. <br/>  If there are **20,000-49,999 licenses** then **1000** telephone numbers are given. <br/>  If there are **50,000+ licenses** then **1500** telephone numbers are given. <br/> |If you have a total of **1001** **Phone System** and **Audio Conferencing** licenses, you can get **125** toll-free service numbers. <br/> <br/> **Important:** [Communications Credits billing](set-up-communications-credits-for-your-organization.md) is required to reserve and use toll-free phone numbers.          |
   
> [!NOTE]
> If you need to get more telephone numbers than this, please [contact support for business products - Admin Help](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
  
## Related topics
[Transferring phone numbers common questions](transferring-phone-numbers-common-questions.md)

[Different kinds of phone numbers used for Calling Plans](different-kinds-of-phone-numbers-used-for-calling-plans.md)

[Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md)

[Emergency calling terms and conditions](emergency-calling-terms-and-conditions.md)

[Skype for Business Online: Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)

  
 