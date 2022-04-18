---
title: Set your coexistence and upgrade settings
author: dstrome
ms.author: dstrome
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
ms.reviewer: bjwhalen
search.appverid: MET150
description: Learn about how to set coexistence and upgrade settings for all users in your organization at once, or for a single or set of users in your organization.
f1.keywords:
- CSH
ms.custom: 
  - NewAdminCenter_Update
  - seo-marvel-apr2020
appliesto: 
  - Microsoft Teams
---

# Set your coexistence and upgrade settings


When you upgrade your Skype for Business users to use Teams, you have several options to help you make it a seamless process for your users. You have the option to make coexistence and upgrade settings for all of the users in your organization at once, or you can make settings changes for a single or set of users in your organization. Note that older versions of Skype for Business clients may not honor these settings. For more information about Skype for Business client versions, go to the [Skype for Business downloads and updates page](/skypeforbusiness/software-updates). 

You can get a better understanding of the modes that are available to you by reading [Understand Microsoft Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md) or [Coexistence with Skype for Business](coexistence-chat-calls-presence.md).  

> [!IMPORTANT]
> [!INCLUDE [upgrade-disclaimer](includes/upgrade-disclaimer.md)]


## Set upgrade options for all users in your organization

 **Using the Microsoft Teams admin center**

1. In the [Microsoft Teams admin center](https://admin.teams.microsoft.com/), in the left navigation, go to **Teams** > **Teams upgrade settings**. 

2. At the top of the **Teams upgrade** page, modify the following options as desired.

    - Set the **Coexistence** mode.
        - **Islands** - Use this setting if you want users to be able to use both Skype for Business and Teams simultaneously.
        - **Skype for Business only** - Use this setting if you want your users to only use Skype for Business.
        - **Skype for Business with Teams collaboration** - Use this setting if you want your users to use Skype for Business in addition to using Teams for group collaboration (channels).
        - **Skype for Business with Teams collaboration and meetings** - Use this setting if you want your users to use Skype for Business in addition to using Teams for group collaboration (channels) and Teams meetings.
        - **Teams only** - Use this setting if you want your users to use only Teams. Note that even with this setting, users can still join meetings hosted in Skype for Business.

          > [!IMPORTANT]
          > You can only assign TeamsOnly mode to the entire tenant after both of the following steps have been completed:
          >  - All on-premises users have been moved to Teams Only using Move-CsUser in the Skype for Business Server on-premises toolset.
          >  - You have updated any Skype for Business DNS records to point to Microsoft 365. 
          >
          > For more detail, see [Disable your hybrid configuration to complete migration to Teams Only](/skypeforbusiness/hybrid/cloud-consolidation-disabling-hybrid).
        
    - Set **Notify Skype for Business users that Teams is available for upgrade**. If you turn this on, it will tell the Skype for Business users that they will soon be upgraded to the Teams app.

    - Set the **Preferred app for users to join Skype for Business meetings**. This setting determines which app is used for joining Skype for Business meetings and is honored regardless of the value of coexistence mode.
      - **Skype Meetings app**
      - **Skype for Business with limited features**

    - Set whether to **Download the Teams app in the background for Skype for Business users**. This setting silently downloads the Teams app for users running Skype for Business on Windows. It is honored only if coexistence mode for the user is Teams only or if notifications of pending upgrade are enabled in Skype for Business.

3. Click **Save** after you make your changes.

## Set upgrade options for a single user in your organization

 **Using the Microsoft Teams admin center**

1. In the left navigation, go to **Users** > **Manage users**, and then select the user from the list. 
2. On the **Account** tab for the user, under **Teams upgrade**, click **Edit**.
3. You can set the **Coexistence mode**. Modes other than Teams Only can only be applied to users homed in Skype for Business Server on-premises, and conversely only users homed in the cloud can have TeamsOnly mode.  Choose from the following options:
     - **Use Org-wide settings** - Use this setting if you want the user to use the settings in the **Org-wide** settings. 
     - **Islands** - Use this setting if you want the user to be able to use both Skype for Business and Teams. 
     - **Skype for Business only** - Use this setting if you want the user to use Skype for Business.
     - **Skype for Business with Teams collaboration** - Use this setting if you want the user to use Skype for Business in addition to using Teams for group collaboration (channels).
      - **Skype for Business with Teams collaboration and meetings** - Use this setting if you want the user to use Skype for Business in addition to using Teams for group collaboration (channels) and Teams meetings.
     - **Teams only** - Use this setting if you want the user to use only Teams. The user will still be able to join Skype for Business meetings.
4. If you select any **Coexistence mode** other than **Use Org-wide settings**, you have the option to enable notifications in the user's Skype for Business app that upgrade to Teams is coming soon. You can enable this notification for the user by turning on the **Notify the Skype for Business user** option.
5. Click **Save** after you make your changes.

### Related topics
[Plan the journey](upgrade-plan-journey.md)

[Understand the coexistence and upgrade journey for Skype for Business and Teams](upgrade-and-coexistence-of-skypeforbusiness-and-teams.md)

[Migration and interoperability guidance for organizations using Teams together with Skype for Business](migration-interop-guidance-for-teams-with-skype.md)

[Decommission your on-premises Skype for Business environment](/skypeforbusiness/hybrid/decommission-on-prem-overview)
