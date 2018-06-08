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

When you are upgrading your Skype for Business users to use Teams, you have several options available to you to make it a seamless process for your users. You have the option to make coexistence and upgrade settings for all of the users in your organization or you can make setting changes for a single or set of users in your organization. You can find out more by reading [Understand coexistence and upgrade modes for Skype for Business and Teams](upgrade-and-coexistence-of-skypeforbusiness-and-teams.md) to get a better understanding of the types of modes that are available to you.

## Setting your upgrade options for all users in your organization

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
3. Click **Save** after you make your changes.

## Setting your upgrade options for a user in your organization

![teams-logo-30x30.png](media/teams-logo-30x30.png) **Using the Microsoft Teams and Skype for Business Admin Center**

1. In the left navigation, go to **Users** then select the user from the list. 
2. On the **Account** tab for the user, under **Teams upgrade** section, click **Edit**.
- You can set the **Coexistence** mode. Choose from the following options:
    - **Use Org-wide settings** Use this setting if you want the user to use the settings in the **Org-wide** settings. If you choose this, you can't select notifications for the user.
    - **Islands** - Use this setting when you have some users on Skype for Business and some users that use Teams. If you choose this, you can enable notifications for the user by turning on the **Notify the Skype for Business user** option. It will tell the Skype for Business user that they can upgrade to the Teams app.
    - **Skype for Business only** - Use this setting if you only have Skype for Business users. If you choose this, you can enable notifications for the user by turning on the **Notify the Skype for Business user** option. It will tell the Skype for Business user that they can upgrade to the Teams app.
    - **Teams only** - use this setting if you only have Teams users. If you choose this, you can enable notifications for the user by turning on the **Notify the Skype for Business user** option. It will tell the Skype for Business user that they can upgrade to the Teams app.
3. Click **Save** after you make your changes.

### Related topics
[Plan the journey](upgrade-plan-journey.md)
[Understand coexistence and upgrade modes for Skype for Business and Teams](upgrade-and-coexistence-of-skypeforbusiness-and-teams.md)