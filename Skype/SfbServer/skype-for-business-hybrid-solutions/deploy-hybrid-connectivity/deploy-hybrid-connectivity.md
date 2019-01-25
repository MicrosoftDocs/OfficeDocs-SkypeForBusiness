---
title: Deploy hybrid connectivity | Skype for Business Server 2015 Online
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- Ent_O365_Hybrid
- Ent_O365_Hybrid_Top
- IT_Skype16
- IT_Skype4B_Hybrid
- Strat_SB_Hybrid
ms.custom: 
ms.assetid: 0d16ec3a-28f0-4483-96e7-8e68f30398fa

description: "Summary: Read this topic to learn how to deploy hybrid connectivity between Skype for Business Server and Skype for Business Online."
---

# Deploy hybrid connectivity between Skype for Business Server and Skype for Business Online

**Summary:** Read this topic to learn how to deploy hybrid connectivity between Skype for Business Server and Skype for Business Online.
  
Before performing the steps in this topic, you should have read [Plan hybrid connectivity between Skype for Business Server and Skype for Business Online](../../skype-for-business-hybrid-solutions/plan-hybrid-connectivity.md).
  
Hybrid connectivity between Skype for Business Server and Skype for Business Online means users of a domain, such as contoso.com, are split between using Skype for Business Server on premises and Skype for Business Online. Some of the domain users are homed on premises, and some users are homed online.
  
The following table lists the steps required to prepare your environment for a hybrid deployment with Skype for Business Online and Microsoft Office 365.
  
|Step|Description|
|:-----|:-----|
|Create a tenant account for Office 365 and enable Skype for Business Online  <br/> |Learn about Office 365 and Skype for Business Online at [Office 365](https://go.microsoft.com/fwlink/p/?LinkId=254980).  <br/> To make sure that your environment is ready for Office 365, see the [System Requirements](https://products.office.com/en-US/office-system-requirements).  <br/> For details about setting up Office 365, see [Getting Started with Office 365](https://go.microsoft.com/fwlink/p/?LinkId=254982).  <br/> |
|Add your domain to your Office 365 tenant and verify ownership  <br/> | You must add your domain to your Office 365 tenant, and then follow the steps to validate the domain with Office 365. This is to confirm that you are the owner of the domain. <br/> To add your domain to your Office 365 tenant, follow the steps described at [Add your domain to Office 365](https://support.office.com/en-us/article/add-a-domain-to-office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611?ui=en-US&rs=en-US&ad=US).  <br/> |
|Prepare for Active Directory synchronization  <br/> |Active Directory synchronization keeps your on-premises Active Directory continuously synchronized with Office 365. This lets you create synchronized versions of each user account and group, and also enables global address list (GAL) synchronization from your local Microsoft Exchange Server environment to Microsoft Exchange Online. For more information, see [Directory Integration Tools](https://go.microsoft.com/fwlink/p/?LinkId=530320).  <br/>  **IMPORTANT** You need to synchronize the AD accounts for all Skype for Business users in your organization between your on-premises and online deployments, even if users are not moved to Skype for Business Online. If you do not synchronize all users, communication between on-premises and online users in your organization may not work as expected.           |
|Move pilot users  <br/> |After you have completed the steps to prepare and configure your environment for Skype for Business Online, you can start moving pilot users to your online Office 365 tenant. See [Move users from on premises to Skype for Business Online](move-users-from-on-premises-to-skype-for-business-online.md).  <br/> |

## Related Content

For information on configuring hybrid connectivity between Skype for Business Server and Office 365, see [Configure hybrid connectivity between Skype for Business Server and Office 365](https://docs.microsoft.com/en-us/SkypeForBusiness/hybrid/configure-hybrid-connectivity).