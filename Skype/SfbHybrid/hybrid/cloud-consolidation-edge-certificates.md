---
ms.date: 11/09/2018
title: "Update the edge certificate"
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.reviewer: bjwhalen
ms.topic: article
ms.service: skype-for-business-server
search.appverid: MET150
ms.collection: 
- Hybrid 
- M365-voice
- m365initiative-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
audience: ITPro
f1.keywords:
- NOCSH
appliesto:
- Skype for Business 
- Microsoft Teams
ms.localizationpriority: medium
description: "This appendix includes detailed steps for updating the edge certificate as part of cloud consolidation for Teams and Skype for Business."
---

# Update the edge certificate

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]


Updating the edge certificate is the key step to ensuring that an on-premises environment with SipDomain1 can join a cloud environment with SipDomain2. It ensures proper routing in a shared address space environment across the two SIP domains. See step 14 in [Cloud consolidation for Teams and Skype for Business](cloud-consolidation.md) for context in which you might perform this step. In our examples, SipDomain1 is AcquiredCompany.<span>com and SipDomain2 is OriginalCompany.<span>com.

The subject alternate name (SAN) of the certificate on all edge servers in the on-premises environment must be updated to include all SIP domains that exist in the pure online tenant (excluding any onmicrosoft.<span>com domains), in the form “sip.\<domain>”. In our example, this is sip.OriginalCompany.<span>com. This step is critical to do before migrating any users to the cloud.

**Steps:**

1.	Obtain a new External Microsoft Edge certificate for the edge that has all existing entries plus other entries in the SAN for all SIP domains in the cloud environment (excluding *.onmicrosoft.com domains) in the form `sip.<DomainName>`.
2.	Install the certificate locally on each edge server and assign it to the Skype Microsoft Edge service on each of the edge service. For detailed steps, see the section “External Microsoft Edge interface certificates” in [Deploy Microsoft Edge Service in Skype for Business Server 2015](../../SfbServer/deploy/deploy-edge-server/deploy-edge-servers.md).
3.	Restart the Microsoft Edge service on each of the edge servers. You can do this for a single box with the following PowerShell commands:

    ```PowerShell
    Stop-CsWindowsService
    Start-CsWindowsService
    ```

## See also

[Cloud Consolidation for Teams and Skype for Business](cloud-consolidation.md)
