---
title: Upgrade Skype for Business on-premises to Teams
author: SerdarSoysal
ms.author: serdars
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.reviewer: landerl
description: Learn how to transition your organization to Microsoft Teams from a Skype for Business on-premises deployment.
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- CSH
ms.custom:
- Teams-upgrade-guidance
- seo-marvel-apr2020
ms.collection: 
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Upgrade from a Skype for Business on-premises deployment to Teams

![Stages of the upgrade journey, with emphasis on the Deployment and Implementation stage.](media/upgrade-banner-deployment.png "Stages of the upgrade journey, with emphasis on the Deployment and Implementation stage")

This article is part of the Deployment and Implementation stage of your upgrade journey. Before proceeding, confirm that you've completed the following activities:

- [Enlisted your project stakeholders](upgrade-enlist-stakeholders.md)
- [Defined your project scope](./upgrade-define-project-scope.md)
- [Understood coexistence and interoperability of Skype for Business and Teams](./teams-and-skypeforbusiness-coexistence-and-interoperability.md)
- [Chosen your upgrade journey](upgrade-and-coexistence-of-skypeforbusiness-and-teams.md)
- [Prepared your environment](./upgrade-prepare-environment.md)
- [Prepared your organization](./upgrade-prepare-organization.md)
- [Conducted a pilot](./pilot-essentials.md)

Follow the guidance in this article if you've deployed Skype for Business or Microsoft Lync on-premises and your organization wants to upgrade to Microsoft Teams either selectively—by using multiple coexistence modes—or all-in. 

> [!IMPORTANT]
> [!INCLUDE [upgrade-disclaimer](includes/upgrade-disclaimer.md)]

## Step 1: Deploy hybrid connectivity

The key prerequisite for upgrading your users to Teams is to deploy hybrid connectivity.

For more information, see [Deploy hybrid connectivity between Skype for Business Server and Skype for Business Online](/skypeforbusiness/skype-for-business-hybrid-solutions/deploy-hybrid-connectivity/deploy-hybrid-connectivity)

## Step 2: Implement your chosen upgrade journey for your organization

After you've completed your hybrid setup, you can plan to move your users to Microsoft 365 or Office 365.

For more information, see:

- [TeamsUpgradePolicy: managing migration and coexistence](upgrade-to-teams-on-prem-tools.md).

- [Move users from on premises to Skype for Business Online](/skypeforbusiness/skype-for-business-hybrid-solutions/deploy-hybrid-connectivity/move-users-from-on-premises-to-skype-for-business-online).

## Phone System and Teams upgrade

Transitioning from on-premises phone systems to Teams will allow you to take advantage of Phone System Direct Routing ("Direct Routing") or the Microsoft-provided Calling Plans for Microsoft 365 or Office 365.

If you're not using Calling Plans, you need to transition your enterprise voice deployment to Phone System Direct Routing as part of your upgrade to Teams.

For more information, see [additional considerations for Phone System Direct Routing](./direct-routing-landing-page.md). If you are planning to use Calling Plans, please refer to our guidance for [transferring your phone numbers to Teams](phone-number-calling-plans/transfer-phone-numbers-to-teams.md).