---
title: Execute Skype for Business hybrid to Teams upgrade - Microsoft Teams
author: arachmanGitHub
ms.author: arachman
manager: serdars
ms.date: 06/30/2018
ms.topic: article
ms.service: msteams
ms.reviewer: dearbeen
description: Execute your upgrade to Teams from Skype for Business hybrid.  
localization_priority: Priority
ms.custom: Teams-upgrade-guidance
MS.collection: Strat_MT_TeamsAdmin
appliesto:
- Microsoft Teams
---

![Stages of the upgrade journey, with emphasis on the Deployment and Implementation stage](media/upgrade-banner-deployment.png "Stages of the upgrade journey, with emphasis on the Deployment and Implementation stage")

This article is part of the Deployment and Implementation stage of your upgrade journey.

# Execute Skype for Business hybrid to Teams upgrade

If Skype for Business or Lync is deployed on-premises and has been configured in a hybrid deployment with your Office 365 tenant, and your organization wants to upgrade to Teams, selectively, with multiple coexistence modes, or all-in based on the upgrade journey that has been decided for your organization, you need to move your users to Skype for Business Online and then assign the appropriate coexistence and upgrade mode to your users. If the users are already homed online, they can be upgraded by assigning the appropriate coexistence and upgrade mode.

## Step 1: Move users to Skype for Business Online

Applicable to users that are currently homed on-premises, you need to move the users to be upgraded to Skype for Business Online.

For more information, see [Move users from on premises to Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/deploy-hybrid-connectivity/move-users-from-on-premises-to-skype-for-business-online)

## Step 2: Assign coexistence and upgrade mode

Once your users are migrated to Skype for Business Online, then you can apply the appropriate coexistence mode based on the journey that your organization has decided to undertake.

For more information, see [TeamsUpgradePolicy: managing migration and coexistence](https://docs.microsoft.com/MicrosoftTeams/migration-interop-guidance-for-teams-with-skype#teamsupgradepolicy-managing-migration-and-co-existence).

> [!NOTE]
> With Skype for Business Server 2019 and future cumulative update of Skype for Business Server 2015, you will be able to perform Step 2 (moving users to Skype for Business Online and Step 3 (upgrade users to Teams) in a single step. More information will be provided once Skype for Business Server 2019 is release

## Phone System and Teams upgrade

If you’re transitioning your Skype for Business hybrid deployment to Phone System with Calling Plans—Microsoft as your PSTN provider, assuming you’ve completed the phone number porting, upgrading your users to Teams will automatically transition inbound PSTN calling to Teams.

Alternatively, if Calling Plans is not available or you intend to use your existing PSTN connectivity provider, you need to transition your enterprise voice deployment or hybrid voice deployment using existing on-premises deployment or Cloud Connector to Direct Routing. Upgrading your users to Teams will need to include additional considerations as described in [placeholder link to Direct Routing Journeys].
