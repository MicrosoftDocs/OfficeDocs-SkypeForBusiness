---
title: "Disable hybrid to complete migration to Teams Only"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: bjwhalen
ms.topic: article
ms.prod: skype-for-business-itpro
search.appverid: MET150
ms.collection: 
- Hybrid 
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
audience: ITPro
f1.keywords:
- NOCSH
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
description: "This article includes detailed steps for disabling hybrid as part of cloud consolidation for Teams and Skype for Business."
---

# Disable your hybrid configuration to complete migration to Teams Only 

This article describes how to disable your hybrid configuration before decommissioning your on-premises Skype for Business environment. This is step 2 of the following steps to decommission your on-premises environment:

- Step 1. [Move all required users from on-premises to online](decommission-move-on-prem-users.md).

- **Step 2. Disable your hybrid configuration.** (This article)

- Step 3. [Migrate hybrid application endpoints from on-premises to online](decommission-move-on-prem-endpoints.md).

- Step 4. [Remove your on-premises Skype for Business deployment](decommission-remove-on-prem.md).

> [!NOTE]
> Steps 2 and 3 should be done in the same maintenance window because any existing hybrid application endpoints will not be discoverable between steps 2 and completion of step 3.


## Summary

After you have upgraded all users from Skype for Business on-premises to Teams Only in Microsoft 365, you can decommission the on-premises Skype for Business deployment.

Before you decommission the on-premises Skype for Business deployment and remove any hardware, you must logically separate the on-premises deployment from Microsoft 365 by disabling hybrid. Disabling hybrid consists of the following four steps:

1. [Update DNS records to point to Microsoft 365](#update-dns-to-point-to-microsoft-365).

2. [Change the coexistence mode for your organization to Teams Only](#change-the-coexistence-mode-for-your-organization-to-teams-only).

3. [Disable shared sip address space (also known as "split domain") in the Microsoft 365 organization](#disable-shared-sip-address-space-in-microsoft-365-organization).

4. [Disable communication between on-premises and Microsoft 365](#disable-communication-between-on-premises-and-microsoft-365)

Disable communication between on-premises and Microsoft 365

These steps logically separate your on-premises deployment of Skype for Business Server from Microsoft 365 and ensure your organization is fully Teams Only. After you've completed these steps, you can decommission your on-premises Skype for Business deployment by using one of two methods referenced in [Manage attributes](cloud-consolidation-managing-attributes.md).

> [!Important] 
> Once this logical separation is complete, msRTCSIP attributes from your on-premises Active Directory still have values and will continue to sync via Azure AD Connect into Azure AD. How you decommission the on-premises environment depends on whether you intend to leave these attributes in place, or first clear them from your on-premises Active Directory. Be aware that clearing the on-premises msRTCSIP attributes after you have migrated from on-premises could result in loss of service for users! Details and tradeoffs of the two decommissioning approaches are described in [Manage attributes](cloud-consolidation-managing-attributes.md).

## Update DNS to point to Microsoft 365

The organization’s external DNS for the on-premises organization needs to be updated so that Skype for Business records point to Microsoft 365 instead of the on-premises deployment. 

In addition, CNAME records for meet or dialin (if present) can be deleted. Finally, any DNS records for Skype for Business in your internal network should be removed.

For details about updating DNS records, see [Update DNS entries to enable your organization to be all Teams Only](decommission-manage-dns-entries.md).

## Change the coexistence mode for your organization to Teams Only

This step ensures that any new user in your organization is always created as a Teams Only user. 

Attempting to change the tenant mode to Teams Only will automatically check for existence of any on-premises DNS records that may have been missed in step 1 and identify these records in the output. Changing the tenant mode to Teams Only will not succeed until all DNS records for your organization are updated. 

To change the tenant mode to Teams Only run the following command from a Teams PowerShell window.

```PowerShell
Grant-CsTeamsUpgradePolicy -PolicyName UpgradeToTeams -Global
```

Alternatively, you can use the Teams Admin Center to change the tenant coexistence mode to TeamsOnly, under "Org-wide settings" -> "Teams Upgrade."    

## Disable shared sip address space in Microsoft 365 organization
    
To disable shared sip address space, run the following command from a Teams PowerShell window.

```PowerShell
Set-CsTenantFederationConfiguration -SharedSipAddressSpace $false
```
 
## Disable communication between on-premises and Microsoft 365

To disable communication between the on-premises environment and Microsoft 365, run the following command from an on-premises PowerShell window:

```PowerShell
Get-CsHostingProvider|Set-CsHostingProvider -Enabled $false
```


## See also

- [Cloud Consolidation for Teams and Skype for Business](cloud-consolidation.md)

- [Decommission your on-premises Skype for Business environment](decommission-on-prem-overview.md)

