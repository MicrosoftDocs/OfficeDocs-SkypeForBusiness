---
title: Setting your coexistence and upgrade settings
author: tonysmit
ms.author: tonysmit
manager: serdars
ms.topic: article
ms.service: msteams
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
ms.reviewer: bjwhalen
search.appverid: MET150
description: This article will help you pick the coexistence mode and set other coexistence settings.
ms.custom:
- NewAdminCenter_Update
appliesto: 
- Microsoft Teams
---

# Setting your coexistence and upgrade settings

> [!IMPORTANT]
> [!INCLUDE [new-teams-sfb-admin-center-notice](includes/new-teams-sfb-admin-center-notice.md)]

When you upgrade your Skype for Business users to use Teams, you have several options to help you make it a seamless process for your users. You have the option to make coexistence and upgrade settings for all of the users in your organization at once, or you can make settings changes for a single or set of users in your organization. Note that older versions of Skype for Business clients may not honor these settings. For more information about Skype for Business client versions, go to the [Skype for Business downloads and updates page](https://docs.microsoft.com/en-us/skypeforbusiness/software-updates). 

You can get a better understanding of the types of modes that are available to you by reading [Understand Microsoft Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md) or [Coexistence with Skype for Business](coexistence-chat-calls-presence.md).  

> [!IMPORTANT]
> [!INCLUDE [upgrade-disclaimer](includes/upgrade-disclaimer.md)]


## Set upgrade options for all users in your organization

![An icon showing the Microsoft Teams logo](media/teams-logo-30x30.png) **Using the Microsoft Teams admin center**

1. In the left navigation, go to **Org-wide settings** > **Teams upgrade**. 

2. At the top of the **Teams upgrade** page, make the following changes if they will work for you.
    - Set the **Coexistence** mode.
        - **Islands** - Use this setting if you want users to be able to use both Skype for Business and Teams simultaneously.
        - **Skype for Business only** - Use this setting if you want your users to only use Skype for Business.
        - **Teams only** (in preview for some organizations) - Use this setting if you want your users to use only Teams. Note that even with this setting, users can still join meetings hosted in Skype for Business.
    - Set **Notify Skype for Business users that Teams is available for upgrade**. If you turn this on, it will tell the Skype for Business users that they will soon be upgraded to the Teams app.
    - Set the **Preferred app for users to join Skype for Business meetings**. This setting determines which app is used for joining Skype for Business meetings and is honored regardless of the value of coexistence mode.
      - **Skype Meetings app**
      - **Skype for Business with limited features**
    - Set whether to **Download the Teams app in the background for Skype for Business users**.  This setting silently downloads the Teams app for users running Skype for Business on Windows. It is honored only if coexistence mode for the user is Teams only or if notifications of pending upgrade are enabled in Skype for Business.
3. Click **Save** after you make your changes.

## Set upgrade options for a single user in your organization

![An icon showing the Microsoft Teams logo](media/teams-logo-30x30.png) **Using the Microsoft Teams admin center**

1. In the left navigation, go to **Users**, and then select the user from the list. 
2. On the **Account** tab for the user, under **Teams upgrade**, click **Edit**.
3. You can set the **Coexistence mode**. Choose from the following options:
     - **Use Org-wide settings** - Use this setting if you want the user to use the settings in the **Org-wide** settings. 
     - **Islands** - Use this setting if you want the user to be able to use both Skype for Business and Teams. 
     - **Skype for Business only** - Use this setting if you want the user to use Skype for Business. 
     - **Teams only** - Use this setting if you want the user to use only Teams. The user will still be able to join Skype for Business meetings.
4. If you select any **Coexistence mode** other than **Use Org-wide settings**, you have the option to enable notifications in the user's Skype for Business app that upgrade to Teams is coming soon. You can enable this notification for the user by turning on the **Notify the Skype for Business user** option.
5. Click **Save** after you make your changes.

### Related topics
[Plan the journey](upgrade-plan-journey.md)

[Understand the coexistence and upgrade journey for Skype for Business and Teams](upgrade-and-coexistence-of-skypeforbusiness-and-teams.md)

[Migration and interoperability guidance for organizations using Teams together with Skype for Business](migration-interop-guidance-for-teams-with-skype.md)
