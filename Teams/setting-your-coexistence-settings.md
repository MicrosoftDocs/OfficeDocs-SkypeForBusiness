---
title: Setting your coexistence settings
author: tonysmit
ms.author: tonysmit
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: bjwhalen
description: This will help you pick the coexistence mode and set other coexistence settings.
ms.custom:
- NewAdminCenter_Update
appliesto: 
- Microsoft Teams
---


# Setting your coexistence settings


> [!IMPORTANT]
> [!INCLUDE [new-teams-sfb-admin-center-notice](includes/new-teams-sfb-admin-center-notice.md)]

<Intro text here>

[Understand coexistence and upgrade modes for Skype for Business and Teams](upgrade-and-coexistence-of-skypeforbusiness-and-teams.md)

## Setting your upgrade options for your users

![teams-logo-30x30.png](media/teams-logo-30x30.png) **Using the Microsoft Teams and Skype for Business Admin Center**

1. In the left navigation, go to **Org-wide settings** > **Teams upgrade**. 

2. At the top of the **Teams upgrade page** page, make the following changes if they will work for you.
- Set the **Coexistence** mode
    - **Islands** - use this setting when you have some users on Skype for Business and some users that use Teams.
    - **Skype for Business only** - use this setting if you only have Skype for Business users.
    - **Teams only** - use this setting if you only have Teams users.
- Set **Notify Skype for Business users that Teams is available for upgrade.**
    - If you turn this on, it will tell the Skype for Business users that they can upgrade to the Teams app.
- Set the **Preferred app for users to join Skype for Business meetings**  This setting determines which app is used for joining Skype for Business meetings and is honored regardless of the value of coexistence mode.
    - **Skype Meetings app (default)**
    - **Skype for Business with limited features**
- Set whether to **Download the Teams app in the background for Skype for Business users**  This setting silently downloads the Teams app for users running Skype for Business on Windows. It is honored only if coexistence mode for the user is Teams Only, or if notifications of pending upgrade are enabled in Skype for Business.
1. Click **Save** after you make your changes.


### Related topics
[[Teams known issues](Known-issues.md)](Teams-overview.md)
[Plan the journey](upgrade-plan-journey.md)