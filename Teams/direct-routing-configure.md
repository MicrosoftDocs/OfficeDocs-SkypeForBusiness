---
title: "Configure Direct Routing"
ms.reviewer: filippse
ms.date: 09/24/2024
ms.author: crowe
author: CarolynRowe
manager: pamgreen
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
  - Tier1
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
description: Learn how to configure Microsoft Direct Routing to connect your on-premises telephony infrastructure to Teams Phone.
ms.custom: seo-marvel-apr2020
---

# Configure Direct Routing

Direct Routing lets you connect your on-premises telephony infrastructure to Microsoft Teams Phone. This article lists the high-level steps required to connect a supported on-premises Session Border Controller (SBC) to Direct Routing, and to configure Teams users to use Direct Routing to connect to the Public Switched Telephone Network (PSTN). This article links to associated articles for details.  

For information about whether Direct Routing is the right solution for your organization, see [PSTN connectivity options](pstn-connectivity.md). For information about prerequisites and planning your deployment, see [Plan Direct Routing](direct-routing-plan.md).

To complete the steps explained in this article, administrators need some familiarity with PowerShell cmdlets. For more information about using PowerShell, see [Set up your computer for Windows PowerShell](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).

Before you perform the steps in these articles, Microsoft recommends that you confirm that your SBC has already been configured as recommended by your SBC vendor. For a complete list of supported SBCs, see [Session Border Controllers certified for Direct Routing](direct-routing-border-controllers.md).

To configure Teams Phone and enable users to use Direct Routing, follow these steps:

- **Step 1.** [Connect the SBC with Teams Phone and validate the connection](direct-routing-connect-the-sbc.md)
- **Step 2.** [Enable users for Direct Routing, voice, and voicemail](direct-routing-enable-users.md)
- **Step 3.** [Configure call routing](direct-routing-voice-routing.md)
- **Step 4.** [Translate numbers to an alternate format](direct-routing-translate-numbers.md)

If you're configuring an SBC for multiple tenants, you'll also want to read [Configure an SBC for multiple tenants](direct-routing-sbc-multiple-tenants.md).

## Support Boundaries

Microsoft supports Teams Phone with Direct Routing only when used with certified devices. If there are issues, you must contact your SBC vendor's customer support first. If needed, the SBC vendor will escalate the issue to Microsoft through internal channels. Microsoft reserves the right to reject support cases where a noncertified device is connected to Teams Phone through Direct Routing. If Microsoft determines that a customer's Direct Routing issue is with a vendor's SBC device, the customer will need to re-engage the SBC vendor for support.

## Related topics

- [Plan your voice solution](cloud-voice-landing-page.md)
- [PSTN connectivity options](pstn-connectivity.md)
- [Plan Direct Routing](direct-routing-plan.md)
