---
title: "Configure Direct Routing"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-voice
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
description: "Learn how to configure Microsoft Phone System Direct Routing."
---

# Configure Direct Routing

Microsoft Phone System Direct Routing enables you to connect your on-premises telephony infrastructure to Microsoft Teams. The article lists the high-level steps required for connecting a supported on-premises Session Border Controller (SBC) to Direct Routing, and how to configure Teams users to use Direct Routing to connect to the Public Switched Telephone Network (PSTN). This article links to associated articles for details.  

For information about whether Direct Routing is the right solution for your organization, see [Phone System Direct Routing](direct-routing-landing-page.md). For information about prerequisites and planning your deployment, see [Plan Direct Routing](direct-routing-plan.md).

> [!Tip]
> You can also watch the following session to learn about the benefits of Direct Routing, how to plan for it, and how to deploy it: [Direct Routing in Microsoft Teams](https://aka.ms/teams-direct-routing).

To complete the steps explained in this article, administrators need some familiarity with PowerShell cmdlets. For more information about using PowerShell, see [Set up your computer for Windows PowerShell](https://docs.microsoft.com/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell). 

Before performing the steps in these articles, Microsoft recommends that you confirm that your SBC has already been configured as recommended by your SBC vendor: 

- [AudioCodes deployment documentation](https://www.audiocodes.com/solutions-products/products/products-for-microsoft-365/direct-routing-for-microsoft-teams)
- [Oracle deployment documentation](https://www.oracle.com/industries/communications/enterprise-session-border-controller/microsoft.html)
- [Ribbon Communications deployment documentation](https://ribboncommunications.com/solutions/enterprise-solutions/microsoft-solutions/direct-routing-microsoft-teams-calling)
- [TE-Systems (anynode) deployment documentation](https://www.anynode.de/anynode-and-microsoft-teams/)

For a complete list of supported SBCs, see [List of Session Border Controllers certified for Direct Routing](direct-routing-border-controllers.md).

To configure Microsoft Phone System and enable users to use Direct Routing, follow these steps: 

- **Step 1.** [Connect the SBC with Microsoft Phone System and validate the connection](direct-routing-connect-the-sbc.md)
- **Step 2.** [Enable users for Direct Routing, voice, and voicemail](direct-routing-enable-users.md)
- **Step 3.** [Configure voice routing](direct-routing-voice-routing.md)
- **Step 4.** [Translate numbers to an alternate format](direct-routing-translate-numbers.md) 

If you are configuring an SBC for multiple tenants, you'll also want to read [Configure an SBC for multiple tenants](direct-routing-sbc-multiple-tenants.md).


## See also

[Phone System Direct Routing](direct-routing-landing-page.md)

[Plan Direct Routing](direct-routing-plan.md)

