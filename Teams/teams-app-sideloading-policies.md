---
title: Manage custom app policies and settings in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.date: 03/15/2019
ms.reviewer: akino
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.audience: Admin
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
appliesto: 
- Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn how to manage custom app policies and settings in Microsoft Teams. 
ROBOTS: NOINDEX, NOFOLLOW
---

# Manage custom app policies and settings in Microsoft Teams

> [!INCLUDE [Preview customer token](includes/preview-feature.md)]

As an admin, you can use custom app policies and settings to determine who in your organization can upload custom apps to Microsoft Teams. Admins decide which users can upload custom apps, and admins and team owners can determine whether specific teams in the organization allow custom apps to be added to them.  

## Overview of custom apps

Users can add a custom app to Teams by uploading an app package (in a .zip file) directly to a team or in the personal context. Uploading a custom app is different from how apps are added through the Store. This scenario, previously called sideloading, is primarily to let you to test an app as it's being developed, before it's ready to be widely distributed. It also lets you build an app for internal use only and share it with your team without submitting it to the Teams app catalog in the Store.

## Custom app policy and settings
Three components determine whether a user can upload a custom app to a team, giving admins extremely granular control on who can add custom apps to a team and which teams custom apps can be added to. These settings no longer have any effect on the ability to block third-party apps.  

### User custom app policy

First, is the user custom app policy. As part of the new app setup policies, admins can now determine whether a user has the capacity to upload custom apps to Teams.  
If this setting is false:
- Under no circumstance can that user upload a custom app into any Team within the tenant 
- The user can interact with custom apps, depending on the org-wide custom app setting 
If this setting is true:
- The user can upload custom apps to teams that allow it, and to teams for which they are owners, depending on the org-wide custom app setting 
- The user can interact with custom apps, depending on the org-wide custom app setting 

You can edit the settings in the global policy to include the apps that you want. If you want to customize Teams for different groups of users in your organization, create and assign one or more custom policies.

#### Set user custom app policy in the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **App setup policies**.
2. Select **New policy**.
3. Turn on or turn off **User can upload custom apps**.
4. Choose the other settings that you want to for the policy. 
5. Click **Save**.

### Team custom app setting

The second component is a Team setting. Admins and team owners can determine whether that specific team allows for custom apps to be added to it. This setting combined with a user's custom app policy determines who has the ability to add custom apps to a particular team. 
 
If this setting is false: 
- Team owners can add custom apps, if their custom app policy allows for it 
- Non-team owners cannot add custom apps to the team. 

If this setting is true: 
- Team owners can add custom apps, if their custom app policy allows for it. 
- Non owners can add custom apps, if their custom app policy allows for it. 

1. In Teams, go to the team, click **More options ˙˙˙** > **Manage team**..
2. Click **Settings**, and then expand **Member permissions**. 
3. Select or clear the **Allow members to upload custom apps** check box.  

## Org-wide custom app setting

The last custom app related setting is org-wide and governs if anyone in the organization can upload or interact with custom apps, and it applies to everyone. This is intended to serve as a master on/off switch during security events. You can find this setting in the “Org-wide app settings” portion of the Permission policies section of the portal

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Permission policies**.
2. Click **Org-wide app settings**.
3. Under **Custom apps**, turn on or turn off **Allow interaction with custom apps**.

 ## Related topics
- [Manage app setup policies in Microsoft Teams](teams-app-setup-policies.md)
- [Manage app permission policies in Microsoft Teams](teams-app-permission-policies.md)
