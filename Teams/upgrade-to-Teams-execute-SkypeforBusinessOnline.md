---
title: Upgrade Skype for Business Online to Microsoft Teams | Deploy
author: lanachin
ms.author: v-lanac
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: dearbeen
description: Considerations for upgrading to Teams from Skype for Business Online 
localization_priority: Normal
search.appverid: MET150
ms.custom: Teams-upgrade-guidance
MS.collection: 
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
---

![Upgrade journey diagram, emphasizing Deployment and Implementation](media/upgrade-banner-deployment.png "Stages of the upgrade journey, with emphasis on the Deployment and Implementation stage")

This article is part of Deployment and Implementation stage of your upgrade journey. Before proceeding, confirm that you’ve completed the following activities:

- [Enlisted your project stakeholders](upgrade-enlist-stakeholders.md)
- [Defined your project scope](https://aka.ms/SkypetoTeams-Scope)
- [Understood coexistence and interoperability of Skype for Business and Teams](https://aka.ms/SkypeToTeams-Coexist)
- [Chosen your upgrade journey](upgrade-and-coexistence-of-skypeforbusiness-and-teams.md)
- [Prepared your environment](https://aka.ms/SkypeToTeams-TechnicalReadiness)
- [Prepared your organization](https://aka.ms/SkypeToTeams-UserReadiness)
- [Conducted a pilot](https://aka.ms/SkypeToTeams-Pilot)

# Upgrade from Skype for Business Online to Teams

Follow the guidance in this article if you have wholly deployed Skype for Business Online and want to upgrade your users from Skype for Business to Teams. You can upgrade users selectively or all-in, based on the upgrade journey that your organization has chosen, by assigning the appropriate coexistence and upgrade mode to your users.

> [!IMPORTANT]
> Skype for Business Online will be retired on July 31, 2021, after which it will no longer be accessible or supported. To maximize benefit realization and ensure your organization has proper time to implement your upgrade, we encourage you to begin your journey to Microsoft Teams today. Remember that a successful upgrade aligns technical and user readiness, so be sure to leverage the guidance herein as you navigate your journey to Microsoft Teams.

## Assign the coexistence and upgrade mode

You can upgrade your users to TeamsOnly mode by assigning the UpgradeToTeams instance of TeamsUpgradePolicy, which can be performed by using the Microsoft Teams admin center or a Skype for Business remote Windows Powershell session. You can do this either on a per user basis, or on a tenant-wide basis if you want to upgrade the entire tenant in one step. 

For more information, see [Setting your coexistence and upgrade settings](https://aka.ms/SkypeToTeams-SetCoexistence) and [TeamsUpgradePolicy: managing migration and coexistence](migration-interop-guidance-for-teams-with-skype.md#teamsupgradepolicy-managing-migration-and-co-existence).

## Upgrade all users to Teams at one time

Follow these steps to upgrade all of your users to Teams at one time.

### Step 1: Notify the users of the change (optional)

1. In the Microsoft Teams admin center, select **Org-wide settings** > **Teams upgrade**.
2. Under **Coexistence mode**, change the **Notify Skype for Business users that an upgrade to Teams is available** switch to **On**.

### Step 2: Set the coexistence mode to TeamsOnly for the organization

1. In the Microsoft Teams admin center, select **Org-wide settings**.
2. Select **Teams Only** mode from the **Coexistence mode** drop-down list.

## Upgrade users in stages

Follow these steps if you want to gradually upgrade your users to TeamsOnly.

### Step 1: Identify groups of users for upgrade

Often organizations may choose to upgrade their organizations in success waves of users.  You'll want to identify these users first so you can easily search for them in the Microsoft Teams admin center. Alternatively, you may want to use PowerShell to more efficiently do this. Once you have identified the set of users for a given upgrade wave, continue with the remaining steps.

### Step 2: Set notification for the users in the current upgrade wave (optional)

If using the Microsoft Teams admin center, you can configure TeamsUpgradePolicy for up to 20 user at once:
1. In the Microsoft Teams admin center, select **Users**, and find and multi-select the checkbox for up to 20 users who should be upgraded. 
2. Select **Edit settings** in the upper left corner of the listview. 
3. In the **Edit settings** pane on the right, under **Teams upgrade**, change **Notify the Skype for Business user** switch to **On**. Note: If the value of coexistence mode is "Use Org-wide settings", you won't see this switch, so you'll need to first explicitly set the Coexistence mode for these users to whatever the default value is for the org.

Alternatively, you may find it easier to enable notifications for groups of users at once using PowerShell. 

### Step 3: Set the coexistence mode for users to Teams Only

When you are ready to upgrade the users in the current wave to use Teams as their only application, set the Coexistence mode for the users to Teams Only.

If using the Microsoft Teams admin center, you can configure TeamsUpgradePolicy for up to 20 user at once:
1. In the Microsoft Teams admin center, select **Users**, and then select the checkbox for up to 20 users.
2. Select **Edit settings** in the upper left corner of the listview.
3. In the **Edit settings** pane on the right, under **Teams upgrade** section, set the coexistence mode to **Teams Only** in the drop-down list.

Alternatively, you may find it easier to upgrade groups of users at once using PowerShell. 

### Step 4: Repeat steps 1-3 for successive waves of users

As you validate your upgrade to Teams Only mode and are ready to expand, repeat the previous steps to apply TeamsOnly to  more users.  


## Phone System and Teams upgrade

If your Skype for Business Online deployment includes Phone System with Calling Plans and Microsoft is your public switched telephone network (PSTN) provider, upgrading your users to Teams will automatically transition inbound PSTN calling to Teams.

If your Skype for Business Online deployment includes Phone System with Cloud Connector Edition, see the [additional considerations for Phone System Direct Routing](2-envision-make-my-service-decisions-direct-routing.md).
