---
title: "Configure hybrid connectivity"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Instructions for implementing  hybrid connectivity between Skype for Business Server and Skype for Business Online."

---

# Configure hybrid connectivity between Skype for Business Server and Office 365
 
**Summary:** Read this topic to learn how to configure hybrid connectivity between Skype for Business Server and Skype for Business Online or Teams.  Hybrid connectivity enables you to move your on-premises users to Skype for Business Online or Teams, and enables your users to take advantage of cloud services.
  
Before performing the steps in this topic, you should have read [Plan hybrid connectivity between Skype for Business Server and Office 365](plan-hybrid-connectivity.md).
  
The following table lists the tasks required to configure Skype for Business hybrid connectivity and provides links to the associated articles for more information.
  
|**Step**|**Description**|
|:-----|:-----|
|Create a tenant account for Office 365 and enable Skype for Business Online  <br/> |Learn about Office 365 and Skype for Business Online at [Office 365](https://go.microsoft.com/fwlink/p/?LinkId=254980).  <br/> To make sure that your environment is ready for Office 365, see the [System Requirements](https://products.office.com/en-US/office-system-requirements).  <br/> For details about setting up Office 365, see [Getting Started with Office 365](https://go.microsoft.com/fwlink/p/?LinkId=254982).  <br/> |
|Add your domain to your Office 365 tenant and verify ownership  <br/> | You must add your domain to your Office 365 tenant, and then follow the steps to validate the domain with Office 365. This is to confirm that you are the owner of the domain. <br/> To add your domain to your Office 365 tenant, follow the steps described in [Add a domain to Office 365](https://support.office.com/en-us/article/add-a-domain-to-office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611?ui=en-US&rs=en-US&ad=US).  <br/> |
|Prepare for Active Directory synchronization  <br/> |Active Directory synchronization keeps your on-premises Active Directory continuously synchronized with Office 365. This lets you create synchronized versions of each user account and group, and also enables global address list (GAL) synchronization from your local Microsoft Exchange Server environment to Microsoft Exchange Online. For more information, see [Integrate your on-premises directories with Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect).  <br/>  **Important:** You need to synchronize the AD accounts for all Skype for Business users in your organization between your on-premises and online deployments, even if users are not moved to Skype for Business Online. If you do not synchronize all users, communication between on-premises and online users in your organization may not work as expected.           |
| Configure Skype for Business hybrid | This consists of three steps:  <br>1. Configure your on-premises Edge service for federation with Skype for Business Online. <br> 2. Configure your Skype for Business Online tenant for a shared SIP address space. <br> 3. Configure authentication if necessary.    <br> For more information, see [Configure Skype for Business hybrid](configure-federation-with-skype-for-business-online.md).
|Move pilot users  <br/> |After you have completed the steps to prepare and configure your environment for Skype for Business Online, you can start moving pilot users to your online Office 365 tenant. For more information, see [Move users from on premises to Skype for Business Online](move-users-from-on-premises-to-skype-for-business-online.md) and [Move users from on premises to Teams](move-users-from-on-premises-to-Teams.md).  <br/> | 

  