---
title: Execute Skype for Business Online to Teams upgrade
author: arachman
ms.author: MyAdvisor
manager: lehewe
ms.date: 05/30/2018
ms.topic: article
ms.service: msteams
ms.reviewer: lehewe
description: Execute your upgrade to Teams from Skype for Business Online. 
MS.collection: Strat_MT_TeamsAdmin
appliesto:
- Microsoft Teams
---

![Stages of the upgrade journey, with emphasis on Technical Readiness](media/upgrade-banner-deployment.png "Stages of the upgrade journey, with emphasis on Technical Readiness")

This article is part of the Deployment stage of your upgrade journey.

# Execute Skype for Business Online to Teams upgrade

Upgrading your users from Skype for Business to Teams, selectively or all-in, based on the upgrade journey that has been decided for your organization, in a wholly Skype for Business Online deployment, can be accomplished by assigning the appropriate coexistence and upgrade mode to your users.

## Assign coexistence and upgrade mode

Upgrading to Teams can be accomplished by assigning TeamsOnly upgrade policy, which can be performed using Microsoft Teams & Skype for Business Admin Center or Skype for Business remote Windows Powershell session.

For more information, see [TeamsUpgradePolicy: managing migration and coexistence](https://docs.microsoft.com/MicrosoftTeams/migration-interop-guidance-for-teams-with-skype#teamsupgradepolicy-managing-migration-and-co-existence).

## Phone System and Teams upgrade

If your Skype for Business Online deployment includes the implementation of Phone System with Calling Plans—Microsoft as your PSTN provider, upgrading your users to Teams will automatically transition inbound PSTN calling to Teams.

For Skype for Business Online deployment that includes the implementation of Phone System with Cloud Connector Edition, upgrading your users to Teams will need to include additional considerations as described in [placeholder link to Direct Routing Journeys].