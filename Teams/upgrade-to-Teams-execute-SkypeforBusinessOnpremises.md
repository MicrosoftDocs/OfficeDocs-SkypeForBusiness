---
title: Execute Skype for Business On-premises to Teams upgrade
author: arachman
ms.author: MyAdvisor
manager: lehewe
ms.date: 05/30/2018
ms.topic: article
ms.service: msteams
ms.reviewer: lehewe
description: Execute your upgrade to Teams from Skype for Business on-premises. 
MS.collection: Strat_MT_TeamsAdmin
appliesto:
- Microsoft Teams
---

![Stages of the upgrade journey, with emphasis on Technical Readiness](media/upgrade-banner-deployment.png "Stages of the upgrade journey, with emphasis on Technical Readiness")

This article is part of the Deployment stage of your upgrade journey.

# Execute Skype for Business on-premises to Teams upgrade

If Skype for Business or Lync is deployed on-premises and your organization wants to upgrade to Teams, selectively, with multiple coexistence modes, or all-in based on the upgrade journey that has been decided for your organization, the first step that needs to be completed is to setup hybrid connectivity with your Office 365 tenant. Subsequently, you need to move your users to Skype for Business Online and then assign the appropriate coexistence and upgrade mode to your users.

## Step 1: Deploy hybrid connectivity

Deploying hybrid connectivity is the key prerequisite before you can upgrade your users to Teams. This may involve new deployment of external connectivity of your existing Skype for Business or Lync deployment, or just a matter of configuring the hybrid relationship with your Office 365 tenant.

For more information, see [Deploy hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/deploy-hybrid-connectivity/deploy-hybrid-connectivity)

## Step 2: Move users to Skype for Business Online

After hybrid setup is completed, you need to move the users to be upgraded to Skype for Business Online.

For more information, see [Move users from on premises to Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/deploy-hybrid-connectivity/move-users-from-on-premises-to-skype-for-business-online)

## Step 3: Assign coexistence and upgrade mode

Once your users are migrated to Skype for Business Online, you can apply the appropriate coexistence mode based on the journey that your organization has decided to undertake.

For more information, see [TeamsUpgradePolicy: managing migration and coexistence](https://docs.microsoft.com/MicrosoftTeams/migration-interop-guidance-for-teams-with-skype#teamsupgradepolicy-managing-migration-and-co-existence).

> [!NOTE]
> With Skype for Business Server 2019 and future cumulative update of Skype for Business Server 2015, you will be able to perform Step 2 (moving users to Skype for Business Online and Step 3 (upgrade users to Teams) in a single step. More information will be provided once Skype for Business Server 2019 is released.

## Phone System and Teams upgrade

If you’re transitioning your Skype for Business on-premises deployment from enterprise voice to Phone System with Calling Plans—Microsoft as your PSTN provider, assuming you’ve completed the phone number porting, upgrading your users to Teams will automatically transition inbound PSTN calling to Teams.

Alternatively, if Calling Plans is not available, you need to transition your enterprise voice deployment to Direct Routing. Upgrading your users to Teams will need to include additional considerations as described in [placeholder link to Direct Routing Journeys].