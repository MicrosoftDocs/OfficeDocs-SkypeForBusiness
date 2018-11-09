---
title: "Disabling hybrid to complete migration to the cloud"
ms.author: crowe
author: crowe
manager: serdars
ms.reviewer: bjwhalen
ms.topic: article
ms.service: 
- skype-for-business-online
- msteams
search.appverid: MET150
ms.collection:  
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
ms.audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
description: "This appendix includes detailed steps for disabling hybrid as part of cloud consolidation for Teams and Skype for Business."
---

# Disabling hybrid to complete migration to the cloud

After you have moved all users from on-premises to the cloud, you can decommission the on-premises Skype for Business deployment. Aside from removing any hardware, a critical step is to logically separate that on-premises deployment from Office 365 by disabling hybrid. Disabling hybrid consists of 3 steps:

1.	Disable split domain in the Office 365 tenant.
2.	Disable ability in on-prem to communicate with Office 365.
3.	Update DNS records to point to Office 365.

These steps should be done together as a unit. Details are provided below.

> [!Note] 
> Any federated organizations that have an allowed domain entry for your sip domain(s) will need to update their allowed domain entries to remove the proxy FQDN. We recommend that you send all your federated partners a communication about this as you prepare to complete your migration to the cloud.

1.	*Disable shared SIP address space in Office 365 tenant.*
The command below needs to be done from a Skype for Business Online PowerShell window.

    `Set-CsTenantFederationConfiguration -SharedSipAddressSpace $false`
 
2.	*Disable ability in on-prem to communicate with Office 365.*  
The command below needs to be done from an on-premises PowerShell window.  If you have previously imported a Skype for Business Online session, start a new Skype for Business PowerShell session.

    `Get-CsHostingProvider|Set-CsHostingProvider -Enabled $false`

3.	*Update DNS to point to Office 365.*
The organization’s external DNS for the on-premises organization needs to be updated so that Skype for Business records point to Office 365 instead of the on-premises deployment. Specifically:

    |Record type|Name|TTL|Value|
    |---|---|---|---|
    |SRV|_sipfederationtls._tcp|3600|100 1 5061 sipfed.online.lync.<span>com|
    |SRV|_sip._tls|3600|100 1 443 sipdir.online.lync.<span>com|
    |CNAME|	lyncdiscover|	3600|	webdir.online.lync.<span>com|
    |CNAME|	sip|	3600|	sipdir.online.lync.<span>com|
    |CNAME|	meet|	3600|	webdir.online.lync.<span>com|
    |CNAME|	dialin	|3600|	webdir.online.lync.<span>com|


## See also

[Cloud Consolidation for Teams and Skype for Business](cloud-consolidation.md)