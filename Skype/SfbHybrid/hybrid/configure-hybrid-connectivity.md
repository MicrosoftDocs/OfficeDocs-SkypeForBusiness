---
title: Configure hybrid connectivity | Deploy Skype for Business Server 2019 connect
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: bjwhalen
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Hybrid 
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
description: "Instructions for implementing  hybrid connectivity between Skype for Business Server and Teams."

---

# Configure hybrid connectivity between Skype for Business Server and Teams

**Summary:** Read this topic to learn how to configure hybrid connectivity between Skype for Business Server and Teams (or Skype for Business Online until its retirement).  Hybrid connectivity enables you to move your on-premises users to Teams (or Skype for Business Online), and enables your users to take advantage of cloud services.
  
Before performing the steps in this topic, you should have read [Plan hybrid connectivity between Skype for Business Server and Teams](plan-hybrid-connectivity.md).
  
The following table lists the tasks required to configure Skype for Business hybrid connectivity and provides links to the associated articles for more information.
  
|Step|Description|
|:-----|:-----|
|Create a tenant account for Microsoft 365   <br/> |Learn about Microsoft 365 at [Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=254980).  <br/> To make sure that your environment is ready for Microsoft 365, see the [System Requirements](https://products.office.com/office-system-requirements).  <br/> For details about setting up Microsoft 365, see [Getting Started with Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=254982).  <br/> |
|Add your domain to your Microsoft 365 organization and verify ownership  <br/> | You must add your domain to your Microsoft 365 organization, and then follow the steps to validate the domain with Microsoft 365. This is to confirm that you are the owner of the domain. <br/> To add your domain to your Microsoft 365 organization, follow the steps described in [Add a domain to Microsoft 365](https://support.office.com/article/add-a-domain-to-office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611?ui=en-US&rs=en-US&ad=US).  <br/> |
|Set up Active Directory synchronization  <br/> |Active Directory synchronization keeps your on-premises Active Directory continuously synchronized with Microsoft 365. This lets you create synchronized versions of each user account and group.  <br/> <br> **Important:** You need to synchronize the AD accounts for all Skype for Business users in your organization between your on-premises and online deployments, even if users are not moved to Teams (or Skype for Business Online). If you do not synchronize all users, communication between on-premises and online users in your organization may not work as expected. For more information, see [Configure Azure AD Connect for hybrid environments](configure-azure-ad-connect.md).         |
| Configure Skype for Business hybrid | There are three basic steps: <br><br> 1. Configure your on-premises environment to federate with Microsoft 365. <br> 2. Configure your on-premises environment to trust Microsoft 365 and enable shared SIP address space with Microsoft 365.<br> 3. Enable shared SIP address space in your Microsoft 365 organization. <br><br> In addition, if you have Exchange on-premises, then you may want to configure OAuth between your Exchange on-premises and Skype for Business Online environments. <br> <br>For more information, see [Configure Skype for Business hybrid](configure-federation-with-skype-for-business-online.md).
|Move pilot users  <br/> |After you have completed the steps to prepare and configure your environment for Teams (or Skype for Business Online), you can start moving pilot users to your online Microsoft 365 organization. For more information, see [Move users from on premises to Teams](move-users-from-on-premises-to-Teams.md) and [Move users from on premises to Skype for Business Online](move-users-from-on-premises-to-skype-for-business-online.md).  <br/> |
