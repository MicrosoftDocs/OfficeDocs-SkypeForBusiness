---
title: Upgrade from Skype for Business Online to Microsoft Teams
author: dstrome
ms.author: dstrome
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.reviewer: landerl
description: Learn how to upgrade your organization to Microsoft Teams from a Skype for Business Online deployment. 
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

# Upgrade from Skype for Business Online to Teams

![Upgrade journey diagram, emphasizing Deployment and Implementation.](media/upgrade-banner-deployment.png "Stages of the upgrade journey, with emphasis on the Deployment and Implementation stage")

This article is part of Deployment and Implementation stage of your upgrade journey. Before proceeding, confirm that you've completed the following activities:

- [Enlisted your project stakeholders](upgrade-enlist-stakeholders.md)
- [Defined your project scope](./upgrade-define-project-scope.md)
- [Understood coexistence and interoperability of Skype for Business and Teams](./teams-and-skypeforbusiness-coexistence-and-interoperability.md)
- [Chosen your upgrade journey](upgrade-and-coexistence-of-skypeforbusiness-and-teams.md)
- [Prepared your environment](./upgrade-prepare-environment.md)
- [Prepared your organization](./upgrade-prepare-organization.md)
- [Conducted a pilot](./pilot-essentials.md)

Follow the guidance in this article if you have wholly deployed Skype for Business Online and want to upgrade your users from Skype for Business to Teams. You can upgrade users selectively or all-in, based on the upgrade journey that your organization has chosen, by assigning the appropriate coexistence and upgrade mode to your users.

> [!IMPORTANT]
> Skype for Business Online was retired on July 31, 2021. To maximize benefit realization and ensure your organization has proper time to implement your upgrade, we encourage you to begin your journey to Microsoft Teams today. Remember that a successful upgrade aligns technical and user readiness, so be sure to leverage the guidance herein as you navigate your journey to Microsoft Teams.

## Assign the coexistence and upgrade mode

You can upgrade your users to TeamsOnly mode by assigning the UpgradeToTeams instance of TeamsUpgradePolicy, which can be performed by using the Microsoft Teams admin center or a Skype for Business remote Windows PowerShell session. You can do this either on a per user basis, or on a tenant-wide basis if you want to upgrade the entire tenant in one step. 

For more information, see [Setting your coexistence and upgrade settings](./setting-your-coexistence-and-upgrade-settings.md) and [TeamsUpgradePolicy: managing migration and coexistence](upgrade-to-teams-on-prem-tools.md).

## Upgrade all users to Teams at one time

Follow these steps to upgrade all of your users to Teams at one time.

### Step 1: Notify the users of the change (optional)

1. In the Microsoft Teams admin center, select **Teams** > **Teams upgrade settings**.
2. Under **Coexistence mode**, change the **Notify Skype for Business users that an upgrade to Teams is available** switch to **On**.

### Step 2: Set the coexistence mode to TeamsOnly for the organization

1. In the Microsoft Teams admin center, select **Teams** > **Teams upgrade settings**.
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

Alternatively, you may find it easier to enable notifications for groups of users at once using PowerShell. For more information, see [Grant-CsTeamsUpgradePolicy](/powershell/module/skype/grant-csteamsupgradepolicy).

### Step 3: Set the coexistence mode for users to Teams Only

When you are ready to upgrade the users in the current wave to use Teams as their only application, set the Coexistence mode for the users to Teams Only.

If using the Microsoft Teams admin center, you can configure TeamsUpgradePolicy for up to 20 user at once:
1. In the Microsoft Teams admin center, select **Users**, and then select the checkbox for up to 20 users.
2. Select **Edit settings** in the upper left corner of the listview.
3. In the **Edit settings** pane on the right, under **Teams upgrade** section, set the coexistence mode to **Teams Only** in the drop-down list.

Alternatively, you may find it easier to upgrade groups of users at once using PowerShell. For more information, see [Grant-CsTeamsUpgradePolicy](/powershell/module/skype/grant-csteamsupgradepolicy).

### Step 4: Repeat steps 1-3 for successive waves of users

As you validate your upgrade to Teams Only mode and are ready to expand, repeat the previous steps to apply TeamsOnly to  more users.  


## Phone System and PSTN connectivity options

Phone System with Teams is supported after the user is in TeamsOnly mode. (If the user is in Islands mode, Phone System is only supported with Skype for Business.)  

### PSTN connectivity options

When considering Public Switched Telephone Network (PSTN) connectivity options, there are two possible scenarios when moving from Skype for Business Online to TeamsOnly mode:

- A user in Skype for Business Online, with a Microsoft Calling Plan. Upon upgrade, this user will continue to have a Microsoft Calling plan. This is the simplest scenario requiring only a couple of steps. For more information, see [From Skype for Business Online with Microsoft Calling Plans](upgrade-to-teams-on-prem-pstn-considerations.md#from-skype-for-business-online-with-microsoft-calling-plans).

- A user in Skype for Business Online, with on-premises voice functionality through Skype for Business on-premises or Cloud Connector Edition. The user’s upgrade to Teams needs to be coordinated with migration of the user to Direct Routing to ensure the TeamsOnly user has PSTN functionality.  For more information see, [From Skype for Business Online with on-premises voice](upgrade-to-teams-on-prem-pstn-considerations.md#from-skype-for-business-online-with-on-premises-voice).
