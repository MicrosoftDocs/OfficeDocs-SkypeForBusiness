---
title: "Update the edge certificate"
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
description: "This appendix includes detailed steps for updating the edge certificate as part of cloud consolidation for Teams and Skype for Business."
---

# Update the edge certificate

Updating the edge certificate is the key step to ensuring that an on-prem environment with SipDomain1 can join a cloud environment with SipDomain2 and ensure proper routing in a shared address space environment across the two SIP domains. See step 14 in [Cloud consolidation for Teams and Skype for Business](cloud-consolidation.md) for context in which you might perform this step. In our examples, SipDomain1 is AcquiredCompany.<span>com and SipDomain2 is OriginalCompany.<span>com.

The subject alternate name (SAN) of the certificate on all edge servers in the on-premises environment must be updated to include all SIP domains that exist in the pure online tenant (excluding any onmicrosoft.<span>com domains), in the form “sip.\<domain>”.  In our example, this is sip.OriginalCompany.<span>com. This step is critical to do before migrating any users to the cloud.

**Steps:**

1.	Obtain a new External Edge certificate for the edge that has all existing entries plus additional entries in the SAN for all SIP domains in the cloud environment (excluding *.onmicrosoft.com domains) in the form “sip.<DomainName>”.
2.	Install the certificate locally on each edge server and assign it to the Skype Edge service on each of the edge service.  For detailed steps, see the section “External Edge interface certificates” in [Deploy Edge Service in Skype for Business Server 2015](https://technet.microsoft.com/en-us/library/dn951368.aspx).
3.	Restart the Edge service on each of the edge servers. You can do this for a single box with the following PowerShell commands:

    ```
    Stop-CsWindowsService
    Start-CsWindowsService
    ```

## See also

[Cloud Consolidation for Teams and Skype for Business](cloud-consolidation.md)