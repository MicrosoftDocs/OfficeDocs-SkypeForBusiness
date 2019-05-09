---
title: Upgrade Skype for Business on-premises to Microsoft Teams | Deploy | Lync
author: arachmanGitHub
ms.author: arachman
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: dearbeen
description: Considerations for upgrading to Teams from a Skype for Business on-premises deployment.
localization_priority: Normal
search.appverid: MET150
ms.custom: Teams-upgrade-guidance
MS.collection: 
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
---

![Stages of the upgrade journey, with emphasis on the Deployment and Implementation stage](media/upgrade-banner-deployment.png "Stages of the upgrade journey, with emphasis on the Deployment and Implementation stage")

This article is part of the Deployment and Implementation stage of your upgrade journey. Before proceeding, confirm that you’ve completed the following activities:

- [Enlisted your project stakeholders](upgrade-enlist-stakeholders.md)
- [Defined your project scope](https://aka.ms/SkypetoTeams-Scope)
- [Understood coexistence and interoperability of Skype for Business and Teams](https://aka.ms/SkypeToTeams-Coexist)
- [Chosen your upgrade journey](upgrade-and-coexistence-of-skypeforbusiness-and-teams.md)
- [Prepared your environment](https://aka.ms/SkypeToTeams-TechnicalReadiness)
- [Prepared your organization](https://aka.ms/SkypeToTeams-UserReadiness)
- [Conducted a pilot](https://aka.ms/SkypeToTeams-Pilot)

# Upgrade from a Skype for Business on-premises deployment to Teams

Follow the guidance in this article if you’ve deployed Skype for Business or Microsoft Lync on-premises and your organization wants to upgrade to Microsoft Teams either selectively—by using multiple coexistence modes—or all-in. 

> [!IMPORTANT]
> [!INCLUDE [upgrade-disclaimer](includes/upgrade-disclaimer.md)]

## Step 1: Deploy hybrid connectivity

The key prerequisite for upgrading your users to Teams is to deploy hybrid connectivity.

For more information, see [Deploy hybrid connectivity between Skype for Business Server and Skype for Business Online](/skypeforbusiness/skype-for-business-hybrid-solutions/deploy-hybrid-connectivity/deploy-hybrid-connectivity)

## Step 2: Implement your chosen upgrade journey for your organization

After you’ve completed your hybrid setup, you can plan to move your users to Office 365.

Once you’ve moved your users to Skype for Business Online, you can assign them the appropriate coexistence mode based on the upgrade journey that your organization has chosen. For more information, see [Setting your coexistence and upgrade settings](setting-your-coexistence-and-upgrade-settings.md) and [TeamsUpgradePolicy: managing migration and coexistence](migration-interop-guidance-for-teams-with-skype.md#teamsupgradepolicy-managing-migration-and-co-existence).

For more information, see [Move users from on premises to Skype for Business Online](/skypeforbusiness/skype-for-business-hybrid-solutions/deploy-hybrid-connectivity/move-users-from-on-premises-to-skype-for-business-online).

## Phone System and Teams upgrade

Transitioning from on-premises phone systems to Teams will allow you to take advantage of Phone System Direct Routing (“Direct Routing”) or the Microsoft-provided Calling Plans for Office 365.

If you're not using Calling Plans in Office 365, you need to transition your enterprise voice deployment to Phone System Direct Routing. To upgrade your users to Teams, see the [additional considerations for Phone System Direct Routing](2-envision-make-my-service-decisions-direct-routing.md).