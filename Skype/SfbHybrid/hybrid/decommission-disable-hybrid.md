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
description: "Instructions for implementing  hybrid connectivity between Skype for Business Server and Skype for Business Online."

---

# Disable hybrid to complete migration to the cloud 

This article describes how to disable your hybrid configuration before decommissioning your on-premises Skype for Business environment. This is step 2 of the following steps to decommission your on-premises environment:

- Step 1. [Move all required users and application endpoints from on-premises to online](decommission-move-on-prem-users.md).

- **Step 2. Disable your hybrid configuration. (This article.)**

- Step 3. [Remove your on-premises Skype for Business deployment](decommission-remove-on-prem.md).


## Overview

After you have upgraded all users from Skype for Business on-premises to Teams Only in Microsoft 365 or Office 365, you can decommission the on-premises Skype for Business deployment. Before decommission of the on-premises Skype for Business and removing any hardware, a critical step is to logically separate the on-premises deployment from Microsoft 365 or Office 365 by disabling hybrid. Disabling hybrid consists of 3 steps:

1.	Update DNS records to point to Microsoft 365 or Office 365.

2.	Disable split domain in the Microsoft 365 or Office 365 organization.

3.	Disable the ability in on-premises to communicate with Microsoft 365 or Office 365.

These steps logically separate your on-premise deployment of Skype for Business Server from Office 365 and should be done together as a unit. Details for each step are provided in this article below. Once that is complete, you can decommission your on-premises Skype for Business Deployment using one of 2 methods referenced below.

> [!Note] 
> Once this logical separation is complete, msRTCSIP attributes from your on-premises Active Directory still have values and will continue to sync via Azure AD Connect into Azure AD. How you decommission the on-premises environment depends on whether you intend to leave these attributes in place, or first clear them from your on-premises Active Directory. Details and tradeoffs of the two decommissioning approaches are described below.
















# Configure hybrid connectivity between Skype for Business Server and Office 365

**Summary:** Read this topic to learn how to configure hybrid connectivity between Skype for Business Server and Teams or Skype for Business Online.  Hybrid connectivity enables you to move your on-premises users to Teams or Skype for Business Online, and enables your users to take advantage of cloud services.
  
Before performing the steps in this topic, you should have read [Plan hybrid connectivity between Skype for Business Server and Office 365](plan-hybrid-connectivity.md).
  
The following table lists the tasks required to configure Skype for Business hybrid connectivity and provides links to the associated articles for more information.
  
|Step|Description|
|:-----|:-----|
|Create a tenant account for Office 365   <br/> |Learn about Office 365 at [Office 365](https://go.microsoft.com/fwlink/p/?LinkId=254980).  <br/> To make sure that your environment is ready for Office 365, see the [System Requirements](https://products.office.com/office-system-requirements).  <br/> For details about setting up Office 365, see [Getting Started with Office 365](https://go.microsoft.com/fwlink/p/?LinkId=254982).  <br/> |
|Add your domain to your Office 365 organization and verify ownership  <br/> | You must add your domain to your Office 365 organization, and then follow the steps to validate the domain with Office 365. This is to confirm that you are the owner of the domain. <br/> To add your domain to your Office 365 organization, follow the steps described in [Add a domain to Office 365](https://support.office.com/article/add-a-domain-to-office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611?ui=en-US&rs=en-US&ad=US).  <br/> |
|Set up Active Directory synchronization  <br/> |Active Directory synchronization keeps your on-premises Active Directory continuously synchronized with Office 365. This lets you create synchronized versions of each user account and group.  <br/> <br> **Important:** You need to synchronize the AD accounts for all Skype for Business users in your organization between your on-premises and online deployments, even if users are not moved to Teams or Skype for Business Online. If you do not synchronize all users, communication between on-premises and online users in your organization may not work as expected. For more information, see [Configure Azure AD Connect for hybrid environments](configure-azure-ad-connect.md).         |
| Configure Skype for Business hybrid | There are three basic steps: <br><br> 1. Configure your on-premises environment to federate with Office 365. <br> 2. Configure your on-premises environment to trust Office 365 and enable shared SIP address space with Office 365.<br> 3. Enable shared SIP address space in your Office 365 organization. <br><br> In addition, if you have Exchange on-premises, then you may want to configure OAuth between your Exchange on-premises and Skype for Business Online environments. <br> <br>For more information, see [Configure Skype for Business hybrid](configure-federation-with-skype-for-business-online.md).
|Move pilot users  <br/> |After you have completed the steps to prepare and configure your environment for Teams or Skype for Business Online, you can start moving pilot users to your online Office 365 organization. For more information, see [Move users from on premises to Skype for Business Online](move-users-from-on-premises-to-skype-for-business-online.md) and [Move users from on premises to Teams](move-users-from-on-premises-to-Teams.md).  <br/> |
