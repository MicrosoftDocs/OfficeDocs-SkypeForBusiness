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

# Execute Skype for Business on-premises to Teams upgrade

If Skype for Business or Lync is deployed on-premises and your organization wants to upgrade to Teams, selectively, with multiple coexistence modes, or all-in based on the upgrade journey that has been decided for your organization, the first step that needs to be completed is to setup hybrid connectivity with your Office 365 tenant.

For more information, see [Deploy hybrid connectivity between Skype for Business Server and Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/deploy-hybrid-connectivity/deploy-hybrid-connectivity)

After hybrid setup is completed, you need to move the users to be upgraded to Skype for Business Online.

For more information, see [Move users from on premises to Skype for Business Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/deploy-hybrid-connectivity/move-users-from-on-premises-to-skype-for-business-online)

Once your users are migrated to Skype for Business Online, then you can apply the appropriate coexistence mode based on the journey that your organization has decided to undertake.

For more information, see [TeamsUpgradePolicy: managing migration and coexistence](https://docs.microsoft.com/MicrosoftTeams/migration-interop-guidance-for-teams-with-skype#teamsupgradepolicy-managing-migration-and-co-existence).

If you’re transitioning your Skype for Business on-premises deployment from enterprise voice to Phone System with Calling Plans—Microsoft as your PSTN provider, assuming you’ve completed the phone number porting, upgrading your users to Teams will automatically transition inbound PSTN calling to Teams.

Alternatively, if Calling Plans is not available, you need to transition your enterprise voice deployment to Direct Routing. Upgrading your users to Teams will need to include additional considerations as described in [placeholder link to Direct Routing Journeys].