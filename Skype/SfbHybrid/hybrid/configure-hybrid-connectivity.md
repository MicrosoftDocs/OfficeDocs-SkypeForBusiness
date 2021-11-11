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
ms.localizationpriority: medium
ms.collection: 
- Hybrid 
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
search.appverid: MET150
description: "Instructions for implementing hybrid connectivity between Skype for Business Server and Teams."

---

# Configure hybrid connectivity between Skype for Business Server and Teams

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

**Summary:** Read this topic to learn how to configure hybrid connectivity between Skype for Business Server and Teams.  Hybrid connectivity enables you to move your on-premises users to Teams, and enables your users to take advantage of cloud services.
  
Before performing the steps in this topic, you should have read [Plan hybrid connectivity between Skype for Business Server and Teams](plan-hybrid-connectivity.md).
  
The following table lists the tasks required to configure Skype for Business hybrid connectivity and provides links to the associated articles for more information.
  
|Step|Description|
|:-----|:-----|
|Create a tenant account for Microsoft 365.   <br/> |Learn about Microsoft 365 at [Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=254980).  <br/> To make sure that your environment is ready for Microsoft 365, see the [System Requirements](https://products.office.com/office-system-requirements).  <br/> For details about setting up Microsoft 365, see [Getting Started with Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=254982).  <br/> |
|Add your domain to your Microsoft 365 organization and verify ownership.  <br/> | You must add your domain to your Microsoft 365 organization, and then follow the steps to validate the domain with Microsoft 365. This validation is to confirm that you are the owner of the domain. <br/> To add your domain to your Microsoft 365 organization, follow the steps described in [Add a domain to Microsoft 365](https://support.office.com/article/add-a-domain-to-office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611?ui=en-US&rs=en-US&ad=US). Be sure to review the guidance below regarding [DNS implications for organizations that become hybrid](#dns-implications-for-on-premises-organizations-that-become-hybrid). <br/> |
|Set up Active Directory synchronization.  <br/> |Active Directory synchronization ensures that your on-premises Active Directory is continuously synchronized with Microsoft 365 so that you create synchronized versions of each user account and group.  <br/> <br> **Important:** You need to synchronize the Active Directory accounts for all Skype for Business users in your organization between your on-premises and online deployments, even if users are not moved to Teams. If you do not synchronize all users, communication between on-premises and online users in your organization may not work as expected. For more information, see [Configure Azure AD Connect for hybrid environments](configure-azure-ad-connect.md).         |
| Configure Skype for Business hybrid. | There are three basic steps: <br><br> 1. Configure your on-premises environment to federate with Microsoft 365. <br> 2. Configure your on-premises environment to trust Microsoft 365 and enable shared SIP address space with Microsoft 365.<br> 3. Enable shared SIP address space in your Microsoft 365 organization. <br><br> In addition, if you have Exchange on-premises, then you may want to configure OAuth between your Exchange on-premises and online environments. <br> <br>For more information, see [Configure Skype for Business hybrid](configure-federation-with-skype-for-business-online.md).
|Move pilot users.  <br/> |After you have completed the steps to prepare and configure your environment for Teams, you can start moving pilot users to your online Microsoft 365 organization. For more information, see [Move users from on premises to Teams](move-users-from-on-premises-to-Teams.md).  <br/> |


## DNS implications for on-premises organizations that become hybrid

By default, tenants are created as TeamsOnly mode. Administrators cannot change this configuration. However, hybrid organizations must not be TeamsOnly mode because this would break federation for their on-premises users. Teams has a built-in mechanism to ensure the tenant-wide TeamsOnly configuration is not applied for new hybrid tenants, and also that tenant-wide TeamsOnly configuration is *removed from existing tenants that become hybrid*. This mechanism is based on the value of the LyncDiscover DNS record for any verified Microsoft 365 domain (because a Skype for Business Server on-premises deployment will in most cases have that record), as described below.

When a new Microsoft 365 subscription is first processed, the following occurs:
- If there are not yet any verified Microsoft 365 domains, the tenant is created as TeamsOnly mode. The value is set through the TeamsUpgradeOverridePolicy, which can only be set by Microsoft. If the policy value is UpgradeToTeams, it takes precedence over any value of TeamsUpgradePolicy.
- If there are verified Microsoft 365 domains, but there are no public DNS LyncDiscover records detected, or if any LyncDiscover records that are detected all point to Microsoft 365 (sipfed.online.lync.com, sipfed.online.gov.skypeforbusiness.us, etc), the tenant is created as TeamsOnly mode (via the TeamsUpgradeOverridePolicy).
- If there is at least one verified Microsoft 365 domain for which a LyncDiscover record is detected, and that record points somewhere other than Microsoft 365, the tenant is created as Islands mode.

When an existing Microsoft 365 tenant is re-provisioned (typically because of a change in verified domains or in subscription details), the following occurs:
- If a LyncDiscover record is found for one or more of the Microsoft 365 verified domains, and that record does not point to Microsoft 365, the tenant-wide TeamsOnly mode (through the TeamsUpgradeOverridePolicy) is removed. The tenant mode will revert to whatever is specified at the tenant level for TeamsUpgradePolicy, which, by default, is Islands mode.


There are some limitations for this automatic detection mechanism:
- If your organization does not have any public DNS records, the TeamsOnly mode will not be removed since Microsoft 365 will not be able to detect the records. If your organization has on-premises Skype for Business Server with no public DNS entries, you will need to contact Microsoft Support to have your tenant downgraded.
- If you add/update a public DNS record to a domain that is *already* a Microsoft 365 verified domain, this DNS change is not detected, and TeamsOnly mode won’t be removed. TeamsOnly mode is only removed if the tenant is re-provisioned, which typically happens when there is a change to Microsoft 365 verified domains or to the subscription.  
