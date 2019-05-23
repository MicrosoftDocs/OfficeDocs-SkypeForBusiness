---
title: "Disable hybrid to complete migration to the cloud"
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
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
description: "This appendix includes detailed steps for disabling hybrid as part of cloud consolidation for Teams and Skype for Business."
---

# Disable hybrid to complete migration to the cloud

After you have moved all users from on-premises to the cloud, you can decommission the on-premises Skype for Business deployment. Aside from removing any hardware, a critical step is to logically separate that on-premises deployment from Office 365 by disabling hybrid. Disabling hybrid consists of 3 steps:

1. Update DNS records to point to Office 365.
2. Disable split domain in the Office 365 tenant.
3. Disable ability in on-prem to communicate with Office 365.


These steps should be done together as a unit. Details are provided below.

> [!Note] 
> In rare cases, changing DNS from pointing on premises to Office 365 for your organization may cause federation with some other organizations to stop working until that other organization updates their federation configuration:<ul><li>
Any federated organizations that are using the older Direct Federation model (also known as Allowed Partner Server) will need to update their allowed domain entries for their organization to remove the proxy FQDN. This legacy federation model is not based on DNS SRV records, so such a configuration will become out of date once your organization moves to the cloud. </li><li>Any federated organization that does not have an enabled hosting provider for sipfed.online.lync.<span>com will need to update their configuration to enable that. This situation is only possible if the federated organization is purely on premises and has never federated with any hybrid or online tenant. In such a case, federation with these organizations will not work until they enable their hosting provider.</li></ul>If you suspect that any of your federated partners may be using Direct Federation or have federated with any online or hybrid organization, we suggest you send them a communication about this as you prepare to complete your migration to the cloud.

1.	*Update DNS to point to Office 365.*
The organization’s external DNS for the on-premises organization needs to be updated so that Skype for Business records point to Office 365 instead of the on-premises deployment. Specifically:

    |Record type|Name|TTL|Value|
    |---|---|---|---|
    |SRV|_sipfederationtls._tcp|3600|100 1 5061 sipfed.online.lync.<span>com|
    |SRV|_sip._tls|3600|100 1 443 sipdir.online.lync.<span>com|
    |CNAME|	lyncdiscover|	3600|	webdir.online.lync.<span>com|
    |CNAME|	sip|	3600|	sipdir.online.lync.<span>com|
    |CNAME|	meet|	3600|	webdir.online.lync.<span>com|
    |CNAME|	dialin	|3600|	webdir.online.lync.<span>com|

2.	*Disable shared SIP address space in Office 365 tenant.*
The command below needs to be done from a Skype for Business Online PowerShell window.

    `Set-CsTenantFederationConfiguration -SharedSipAddressSpace $false`
 
3.	*Disable ability in on-prem to communicate with Office 365.*  
The command below needs to be done from an on-premises PowerShell window.  If you have previously imported a Skype for Business Online session, start a new Skype for Business PowerShell session.

    `Get-CsHostingProvider|Set-CsHostingProvider -Enabled $false`

## See also

[Cloud Consolidation for Teams and Skype for Business](cloud-consolidation.md)