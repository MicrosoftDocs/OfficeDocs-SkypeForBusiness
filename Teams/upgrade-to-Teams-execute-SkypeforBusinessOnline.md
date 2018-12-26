---
title: Upgrade from Skype for Business Online to Teams - Microsoft Teams
author: arachmanGitHub
ms.author: arachman
manager: serdars
ms.date: 12/26/2018
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

You can upgrade your users by Teams by assigning the TeamsOnly mode of TeamsUpgradePolicy, which can be performed by using the Microsoft Teams & Skype for Business Admin Center or a Skype for Business remote Windows Powershell session.

For more information, see [Setting your coexistence and upgrade settings](https://aka.ms/SkypeToTeams-SetCoexistence) and [TeamsUpgradePolicy: managing migration and coexistence](migration-interop-guidance-for-teams-with-skype.md#teamsupgradepolicy-managing-migration-and-co-existence).

## Upgrade all users to Teams at one time

Follow these steps to upgrade all of your users to Teams at one time.

### Step 1: Notify the users of the change 

1. In the Microsoft Teams & Skype for Business Admin Center, select **Org-wide settings** > **Teams upgrade**. 
2. Under **Coexistence mode**, change the **Notify Skype for Business users that an upgrade to Teams is available** switch to **On**.

### Step 2: Set the coexistence mode for the users 

1. In the Microsoft Teams & Skype for Business Admin Center, select **Org-wide settings**. 
2. Select **Teams Only** mode from the **Coexistence mode** drop-down list.
 
## Upgrade users in stages

Follow these steps if you want to gradually upgrade your users to Teams.

### Step 1: Create your user cohorts for the upgrade 

User cohorts are groups of users who will be moved to Teams Only mode at the same time.  

To create your user cohorts (Add link to user selection page)
 
### Step 2: Set the user mode to Islands 

1. In the Microsoft Teams & Skype for Business Admin Center, select **Users** and select a user cohort.
2. Next to **Teams upgrade**, select **Edit**.
3. In the **Teams Upgrade** pane, under **Coexistence mode**, select **Islands** from the drop-down list. 

### Step 3: Set notification for the user (optional) 

1. In the Microsoft Teams & Skype for Business Admin Center, select **Users**, and select a user cohort.
2. Next to **Teams upgrade**, select **Edit**.
3. In the **Teams Upgrade** pane, under Coexistence mode, change **Notify the Skype for Business user** switch to **On**.

### Step 4: Set the user mode to Teams Only 

When you are ready to upgrade the users to use Teams as their only application, set the Coexistence mode for the user to Teams Only.  

1. In the Microsoft Teams & Skype for Business Admin Center, select **Users**.
2. Next to **Teams upgrade**, select **Edit**.
3. In the **Teams Upgrade** pane, under **Coexistence mode**, select **Teams Only** from the drop-down list. 

## Phone System and Teams upgrade

If your Skype for Business Online deployment includes Phone System with Calling Plans and Microsoft is your public switched telephone network (PSTN) provider, upgrading your users to Teams will automatically transition inbound PSTN calling to Teams.

If your Skype for Business Online deployment includes Phone System with Cloud Connector Edition, see the [additional considerations for Phone System Direct Routing](2-envision-make-my-service-decisions-direct-routing.md).