---
title: Upgrade from Skype for Business Online to Teams - Microsoft Teams
author: arachmanGitHub
ms.author: arachman
manager: serdars
ms.date: 07/16/2018
ms.topic: article
ms.service: msteams
ms.reviewer: dearbeen
description: Considerations for upgrading to Teams from Skype for Business Online 
localization_priority: Normal
search.appverid: MET150
ms.custom: Teams-upgrade-guidance
MS.collection: Teams_ITAdmin_JourneyFromSfB
appliesto:
- Microsoft Teams
---

![Stages of the upgrade journey, with emphasis on the Deployment and Implementation stage](media/upgrade-banner-deployment.png "Stages of the upgrade journey, with emphasis on the Deployment and Implementation stage")

This article is part of Deployment and Implementation stage of your upgrade journey. Before proceeding, confirm that you’ve completed the following activities:

-   [Enlisted your project stakeholders](upgrade-enlist-stakeholders.md)
-   [Defined your project scope](https://aka.ms/SkypetoTeams-Scope)
-   [Understood coexistence and interoperability of Skype for Business and Teams](https://aka.ms/SkypeToTeams-Coexist)
-   [Chosen your upgrade journey](upgrade-and-coexistence-of-skypeforbusiness-and-teams.md)
-   [Prepared your environment](https://aka.ms/SkypeToTeams-TechnicalReadiness)
-   [Prepared your organization](https://aka.ms/SkypeToTeams-UserReadiness)
-   [Conducted a pilot](https://aka.ms/SkypeToTeams-Pilot)


# Upgrade from Skype for Business Online to Teams

Follow the guidance in this article if you have wholly deployed Skype for Business Online and want to upgrade your users from Skype for Business to Teams. You can upgrade users selectively or all-in, based on the upgrade journey that your organization has chosen, by assigning the appropriate coexistence and upgrade mode to your users.

> [!IMPORTANT]
> [!INCLUDE [upgrade-disclaimer](includes/upgrade-disclaimer.md)]

## Assign the coexistence and upgrade mode

Upgrading to Teams can be accomplished by assigning the TeamsOnly mode of TeamsUpgradePolicy, which can be performed by using Microsoft Teams & Skype for Business Admin Center or a Skype for Business remote Windows Powershell session.

For more information, see [Setting your coexistence and upgrade settings](https://aka.ms/SkypeToTeams-SetCoexistence) and [TeamsUpgradePolicy: managing migration and coexistence](migration-interop-guidance-for-teams-with-skype.md#teamsupgradepolicy-managing-migration-and-co-existence).

## Phone System and Teams upgrade

If your Skype for Business Online deployment includes Phone System with Calling Plans and Microsoft is your public switched telephone network (PSTN) provider, upgrading your users to Teams will automatically transition inbound PSTN calling to Teams.

If your Skype for Business Online deployment includes Phone System with Cloud Connector Edition, see the [additional considerations for Phone System Direct Routing](2-envision-make-my-service-decisions-direct-routing.md).