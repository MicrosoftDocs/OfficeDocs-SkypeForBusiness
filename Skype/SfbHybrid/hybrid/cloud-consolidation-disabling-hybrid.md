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

For information about managing attributes after moving users from on-premises to the cloud, see [Manage attributes](cloud-consolidation-managing attributes.md).

## Overview

After you have upgraded all users from Skype for Business on-premises to Teams Only in Microsoft 365, you can decommission the on-premises Skype for Business deployment. Before you decommission the on-premises Skype for Business deployment and remove any hardware, you must logically separate the on-premises deployment from Microsoft 365 by disabling hybrid. Disabling hybrid consists of the following four steps:

1. [Update DNS records to point to Microsoft 365](#update-dns-to-point-to-microsoft-365).

2. [Change the coexistence mode for your organization to Teams Only](#change-the-coexistence-mode-for-your-organization-to-teams-only).

3. [Disable shared sip address space (also known as "split domain") in the Microsoft 365 organization](#disable-shared-sip-address-space-in-microsoft-365-organization).

4. [Disable the ability in on-premises to communicate with Microsoft 365](#disable-the-ability-in-on-premises-to-communicate-with-microsoft-365).

These steps logically separate your on-premises deployment of Skype for Business Server from Microsoft 365 and ensure your organization is fully Teams Only. Details for each step are provided in this article. Once that is complete, you can decommission your on-premises Skype for Business deployment by using one of two methods referenced below.

> [!Important] 
> Once this logical separation is complete, msRTCSIP attributes from your on-premises Active Directory still have values and will continue to sync via Azure AD Connect into Azure AD. How you decommission the on-premises environment depends on whether you intend to leave these attributes in place, or first clear them from your on-premises Active Directory. Be aware that clearing the on-premises msRTCSIP attributes after you have migrated from on-premises could result in loss of service for users! Details and tradeoffs of the two decommissioning approaches are described later.

## Update DNS to point to Microsoft 365

The organization’s external DNS for the on-premises organization needs to be updated so that Skype for Business records point to Microsoft 365 instead of the on-premises deployment. Specifically:

|Record type|Name|TTL|Priority|Weight|Port|Value|
|---|---|---|---|---|---|---|
|SRV|_sipfederationtls._tcp|3600|100|1|5061|sipfed.online.lync.<span>com|
|SRV|_sip._tls|3600|100|1|443|sipdir.online.lync.<span>com|
|CNAME|	lyncdiscover|	3600| | | |webdir.online.lync.<span>com|
|CNAME|	sip|	3600| | | |	sipdir.online.lync.<span>com|

In addition, CNAME records for meet or dialin (if present) can be deleted. Finally, any DNS records for Skype for Business in your internal network should be removed.

> [!Note] 
> In rare cases, changing DNS from pointing on premises to Microsoft 365 for your organization may cause federation with some other organizations to stop working until that other organization updates their federation configuration:
>
> - Any federated organizations that are using the older Direct Federation model (also known as Allowed Partner Server) will need to update their allowed domain entries for their organization to remove the proxy FQDN. This legacy federation model is not based on DNS SRV records, so such a configuration will become out of date once your organization moves to the cloud.
> 
> - Any federated organization that does not have an enabled hosting provider for sipfed.online.lync.<span>com will need to update their configuration to enable that. This situation is only possible if the federated organization is purely on-premises and has never federated with any hybrid or online tenant. In such a case, federation with these organizations will not work until they enable their hosting provider.
>
> If you suspect that any of your federated partners may be using Direct Federation or have not federated with any online or hybrid organization, we suggest you send them a communication about this as you prepare to complete your migration to the cloud.

For more information about updating DNS records, see [Update DNS entries to enable your organization to be all Teams Only](decommission-manage-dns-entries.md).

## Change the coexistence mode for your organization to Teams Only

This step ensures that any new user in your organization is always created as a Teams Only user. In addition, attempting to change the tenant mode to Teams Only will automatically check for existence of any on-premises DNS records that may have been missed in step 1 and identify these records in the output.  Changing the tenant mode to Teams Only will not succeed until all DNS records for your organizaiton are updated. To change the tenant mode to Teams Only run the following command from a Teams PowerShell window.

```PowerShell
Grant-CsTeamsUpgradePolicy -PolicyName UpgradeToTeams -Global
```

Alternatively, you can use the Teams Admin Center to change the tenant coexistence mode to TeamsOnly, under "Org-wide settings" -> "Teams Upgrade."    

## Disable shared sip address space in Microsoft 365 organization
    
The command below needs to be done from a Teams PowerShell window.

```PowerShell
Set-CsTenantFederationConfiguration -SharedSipAddressSpace $false
```
 
## Disable the ability in on-premises to communicate with Microsoft 365

The command below needs to be done from an on-premises PowerShell window:

```PowerShell
Get-CsHostingProvider|Set-CsHostingProvider -Enabled $false
```


## See also

- [Cloud Consolidation for Teams and Skype for Business](cloud-consolidation.md)

- [Decommission your on-premises Skype for Business environment](decommission-on-prem-overview.md)

