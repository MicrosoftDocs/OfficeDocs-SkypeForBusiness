---
title: "Configure Direct Routing"
ms.reviewer: filippse
ms.author: crowe
author: CarolynRowe
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - m365solution-voice
  - m365solution-scenario
  - highpri
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
description: Learn how to configure Microsoft Direct Routing to connect your on-premises telephony infrastructure to Teams Phone System.
ms.custom: seo-marvel-apr2020
---

# Configure Direct Routing

Direct Routing enables you to connect your on-premises telephony infrastructure to Microsoft Teams. The article lists the high-level steps required for connecting a supported on-premises Session Border Controller (SBC) to Direct Routing, and how to configure Teams users to use Direct Routing to connect to the Public Switched Telephone Network (PSTN). This article links to associated articles for details.  

For information about whether Direct Routing is the right solution for your organization, see [PSTN connectivity options](pstn-connectivity.md). For information about prerequisites and planning your deployment, see [Plan Direct Routing](direct-routing-plan.md).

To complete the steps explained in this article, administrators need some familiarity with PowerShell cmdlets. For more information about using PowerShell, see [Set up your computer for Windows PowerShell](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell). 

Before performing the steps in these articles, Microsoft recommends that you confirm that your SBC has already been configured as recommended by your SBC vendor: 

- [AudioCodes deployment documentation](https://www.audiocodes.com/solutions-products/products/products-for-microsoft-365/direct-routing-for-microsoft-teams)
- [Oracle deployment documentation](https://www.oracle.com/industries/communications/enterprise-session-border-controller/microsoft.html)
- [Ribbon Communications deployment documentation](https://ribboncommunications.com/solutions/enterprise-solutions/microsoft-solutions/direct-routing-microsoft-teams-calling)
- [TE-Systems (anynode) deployment documentation](https://www.anynode.de/anynode-and-microsoft-teams/)
- [Metaswitch deployment documentation](https://www.metaswitch.com/products/core-network/perimeta-sbc)

For a complete list of supported SBCs, see [Session Border Controllers certified for Direct Routing](direct-routing-border-controllers.md).

To configure Phone System and enable users to use Direct Routing, follow these steps: 

- **Step 1.** [Connect the SBC with Phone System and validate the connection](direct-routing-connect-the-sbc.md)
- **Step 2.** [Enable users for Direct Routing, voice, and voicemail](direct-routing-enable-users.md)
- **Step 3.** [Configure call routing](direct-routing-voice-routing.md)
- **Step 4.** [Translate numbers to an alternate format](direct-routing-translate-numbers.md) 

If you're configuring an SBC for multiple tenants, you'll also want to read [Configure an SBC for multiple tenants](direct-routing-sbc-multiple-tenants.md).

## Support Boundaries
Microsoft only supports Phone System with Direct Routing when used with certified devices. If there are issues, you must contact your SBC vendor's customer support first. If needed, the SBC vendor will escalate the issue to Microsoft via internal channels. Microsoft reserves the right to reject support cases where a non-certified device is connected to Phone System through Direct Routing. If Microsoft determines that a customer's Direct Routing issue is with a vendor's SBC device, the customer will need to re-engage the SBC vendor for support.

## Related topics

[Plan your voice solution](cloud-voice-landing-page.md)

[PSTN connectivity options](pstn-connectivity.md)

[Plan Direct Routing](direct-routing-plan.md)
