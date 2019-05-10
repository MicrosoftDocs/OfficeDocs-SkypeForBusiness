---
title: Upgrade Skype for Business hybrid deployment to Microsoft Teams | PSTN
author: lanachin
ms.author: v-lanac
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: dearbeen
description: Considerations for upgrading to Teams from a Skype for Business hybrid deployment. 
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

This article is part of Deployment and Implementation stage of your upgrade journey. Before proceeding, confirm that you’ve completed the following activities:

- [Enlisted your project stakeholders](upgrade-enlist-stakeholders.md)
- [Defined your project scope](https://aka.ms/SkypetoTeams-Scope)
- [Understood coexistence and interoperability of Skype for Business and Teams](https://aka.ms/SkypeToTeams-Coexist)
- [Chosen your upgrade journey](upgrade-and-coexistence-of-skypeforbusiness-and-teams.md)
- [Prepared your environment](https://aka.ms/SkypeToTeams-TechnicalReadiness)
- [Prepared your organization](https://aka.ms/SkypeToTeams-UserReadiness)
- [Conducted a pilot](https://aka.ms/SkypeToTeams-Pilot)

# Upgrade from a Skype for Business hybrid deployment to Teams

Follow the guidance in this article if you’ve deployed Skype for Business or Microsoft Lync on-premises and configured it in a hybrid deployment with your Office 365 tenant, and your organization wants to upgrade to Teams either selectively—by using multiple coexistence modes—or all-in. For either upgrade journey, you need to move your users to Skype for Business Online (if they aren’t already homed online) and then assign them the appropriate coexistence and upgrade mode.

> [!IMPORTANT]
> [!INCLUDE [upgrade-disclaimer](includes/upgrade-disclaimer.md)]

## Step 1: Move users to Skype for Business Online

This step applies to users who are currently homed on-premises. For more information about moving these users to Skype for Business Online, see [Move users from on -premises to Skype for Business Online](/skypeforbusiness/skype-for-business-hybrid-solutions/deploy-hybrid-connectivity/move-users-from-on-premises-to-skype-for-business-online).

## Step 2: Assign a coexistence and upgrade mode

After you’ve moved your users to Skype for Business Online, you can assign them the appropriate coexistence mode based on the upgrade journey that your organization has chosen. For more information, see [Setting your coexistence and upgrade settings](https://aka.ms/SkypeToTeams-SetCoexistence) and [TeamsUpgradePolicy: managing migration and coexistence](migration-interop-guidance-for-teams-with-skype.md#teamsupgradepolicy-managing-migration-and-co-existence).

> [!NOTE]
> With Skype for Business Server 2019 and a future cumulative update of Skype for Business Server 2015, you’ll be able to perform Step 1 (moving users to Skype for Business Online) and Step 2 (upgrade users to Teams) in a single step. More information will be provided after Skype for Business Server 2019 is released.

## Phone System and Teams upgrade

If you’re transitioning your Skype for Business hybrid deployment to Phone System with Calling Plans and Microsoft will be your public switched telephone network (PSTN) provider—and assuming that you’ve completed the phone number porting—upgrading your users to Teams will automatically transition inbound PSTN calling to Teams.

If Calling Plans isn’t available or you intend to use your existing PSTN connectivity provider, you need to transition your enterprise voice deployment—or hybrid voice deployment that uses your existing on-premises deployment or Cloud Connector Edition—to Microsoft Phone System Direct Routing. To upgrade your users to Teams, see the [additional considerations for Phone System Direct Routing](2-envision-make-my-service-decisions-direct-routing.md).
