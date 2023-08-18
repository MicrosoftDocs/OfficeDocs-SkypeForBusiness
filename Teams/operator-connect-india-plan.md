---
title: Plan for Operator Connect for India
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 08/15/2023
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - Tier1
ms.reviewer: roykuntz
search.appverid: MET150
f1.keywords:
- NOCSH
- ms.teamsadmincenter.directrouting.overview
description: Learn more about Operator Connect for India, such as requirements and planning for deployment.
ms.custom: 
 - seo-marvel-apr2020
 - seo-marvel-jun2020
appliesto: 
  - Microsoft Teams
---

# Plan Operator Connect for India

Operator Connect for India is another option for providing Public Switched Telephone Network (PSTN) connectivity with Teams Phone. Operator Connect for India addresses the telephony regulatory issues specific to India.  

This article describes benefits and requirements. For a list of operators participating in the Microsoft Operator Connect Program and the countries or regions where their service is available, see the [Operator Connect directory](https://cloudpartners.transform.microsoft.com/practices/microsoft-365-for-operators/directory).

With Operator Connect for India:

- **You'll need to acquire the appropriate license from your operator in India.** Whether you have an existing Teams Phone license or not--for example, a phone license included with an E5 license--you'll still need to purchase a license from your India operator.  For more information, see **ADD LINKS TO OC DIRECTORY OPERATOR PAGES.**

- **ADD NOTE ABOUT CALL CENTER SUPPORT.**

- If you decide Operator Connect for India is the right solution for your organization, after reading this article, see [Configure Operator Connect for India](operator-connect-india-configure.md). The configuration article describes how to collaborate with your operator, and how to use the Teams admin center and PowerShell to deploy and configure Operator Connect for India.

For more information about Teams voice solutions and PSTN connectivity options, see [Plan your Teams voice solution](cloud-voice-landing-page.md) and [PSTN connectivity options](pstn-connectivity.md).

## Benefits

With Operator Connect for India, if your existing operator is a participant in the [Microsoft Operator Connect Program](https://cloudpartners.transform.microsoft.com/practices/microsoft-365-for-operators/directory), they can manage the service for bringing PSTN calling to Teams. The Operator Connect program provides the following benefits:

- **Leverage existing contracts, or find a new operator.** You keep your preferred operator and contracts, or choose a new one from a selection of participating operators to meet your business needs.

- **Operator-managed infrastructure.** Your operator manages the PSTN calling services and Session Border Controllers (SBCs), allowing you to save on hardware purchase and management.

- **Faster, easier deployment.** You can quickly connect to your operator and assign phone numbers to users-–all from the Teams admin center.

- **Enhanced support and reliability.** Operators provide technical support and shared service level agreements to improve support service, while direct peering powered by Azure creates a one-to-one network connection for enhanced reliability. 

- **Ability to assign wired numbers to Teams users.** For more information, see Plan and Configure Location-Based Routing for India.


## Licensing and requirements

To enable phone number assignments with Operator Connect for India, make sure your users are:

- **Assigned the appropriate license.** You'll acquire the appropriate license from your operator in India. To learn more, see [What is Teams Phone?](what-is-phone-system-in-office-365.md) and [Assign Teams add-on licenses to users](teams-add-on-licensing/assign-teams-add-on-licenses.md).

- **In TeamsOnly mode.** Note that the user needs to be in TeamsOnly mode, but your entire organization does not. To learn more, see [Understand Microsoft Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md).


## Support boundaries

For technical support, please contact the customer support of your Operator Connect operator first. If needed, Operator Connect operators can escalate your support case directly to Microsoft engineering through shared support channels. 

## Related topics

-  [Configure Operator Connect for India](operator-connect-india-configure.md)

