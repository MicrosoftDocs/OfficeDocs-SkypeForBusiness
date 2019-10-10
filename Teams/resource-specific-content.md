---
title: Resource-specific consent in Microsoft Teams
author: LanaChin
ms.author: v-lanac
ms.reviewer: nkramer
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to move your Microsoft StaffHub teams and schedule data to Shifts in Microsoft Teams.
localization_priority: Normal
ms.collection: Strat_MT_TeamsAdmin
appliesto: 
- Microsoft Teams
---

# Resource-specific consent in Microsoft Teams

Resource-specific consent in Microsoft Teams lets team owners give consent to apps that access team data. Such access can include the ability to read channel messages, create and delete channels, and create and remove channel tabs. Previously, team owners could install apps in Teams, but had limited ability to read data from a team. Resource-specific consent doesn't change apps that are already installed and that were granted consent.

---
Your Teams app can now call Teams Graph APIs without requiring an admin to give consent. These include APIs to create, rename, and delete channels, read channel messages, create tabs, and add and remove members from teams.
 
Previously, apps that call Teams Graph APIs required a global admin to approve the app before it could be run, and required very high levels of permissions that admins were reluctant to grant. Resource-specific consent eliminates this friction by allowing team owners to give consent to an app to use only their team's data, without the need for a global admin to approve the app org-wide. To the team owner, it will look just like any other Teams app, only with more powerful permissions.

## Requirements for developers

- Get a Graph AppId
- Remove unnecessary permissions
- Update your Teams app manifest to link to your Graph AppId
- Get a token
- Make a Graph call

To learn more, see TBD. 

## Set whether team owners can give consent to apps
 
As an admin, you can control whether team owners in your organization can give consent to apps. You can do this in the Azure AD portal and the Microsoft Teams admin center.

### Using the Azure AD portal

This has administrative controls to enable and disable. This feature is on by default in tenants where "Users can consent to apps accessing company data on their behalf" is set to Yes.

### Using the Microsoft Teams admin center

Org-wide app settings and the settings in the app permission policy assigned to the team owner determine whether a team owner can give consent to apps. To learn more, see [Manage app permission policies in Teams](teams-app-permission-policies.md).

#### Step 1: Turn on the "Allow third-party or custom apps" in org-wide app settings

This setting controls whether users in your organization can use third-party and custom apps. To enable team owners to give consent to apps, this setting must be on. Changing this setting doesn't affect apps that are already granted consent.

To turn on this setting, do the following:

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Permission policies**, and then click **Org-wide settings**.
2. Under **Third-party apps**, turn on **Allow third-party or custom apps in Teams**.

#### Step 2: Check blocked apps in org-wide app settings

When an app is blocked in org-wide app settings, it's blocked for all users in your organization. Team owners can only give consent to an app if the app isn't blocked.

To view and manage the apps that are blocked across your organization, do the following:

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Permission policies**, and then click **Org-wide settings**.
2. Under **Blocked apps**, view the list of blocked apps.  You can remove and add apps to the blocked app list.

#### Step 3: Check the app permission policy assigned to the team owner

Team owners can only give consent to apps that their app permission policy allows them to run. Changing app permission policy doesn't affect apps that are already granted consent.

To view and manage the app permission policy that's assigned to a team owner, do the following:

1. In the left navigation of the Microsoft Teams admin center, go to **Users**.
2. Double-click the display name of the team owner, and then click **Policies**.
3. The policy assigned to the team owner is listed under **App permission policy**.
    - To assign a different policy, click **Edit**, and then select the policy that you want to assign.
    - To edit the settings of the policy that's assigned to the team owner, click the policy name, and then make the changes that you want.  

> [!NOTE]
> Org-wide app settings override the global app permission policy and any custom app permission policies that you create and assign to users.

## Related topics
