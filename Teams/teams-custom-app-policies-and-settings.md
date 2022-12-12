---
title: Manage custom and sideloaded app policies and settings
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.tgt.pltfrm: cloud
ms.subservice: teams-apps
ms.service: msteams
audience: Admin
ms.date: 09/26/2022
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
ms.localizationpriority: high
search.appverid: MET150
description: Learn how to manage policies and settings to control who in your organization can sideload apps and upload custom apps.
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.apppermspolicies.orgwideapps.customapps
  - ms.teamsadmincenter.appsetuppolicies.allowsideloading
  - ms.teamsadmincenter.appsetuppolicies.tooltip.allowsideloading
  - ms.teamsadmincenter.apppermspolicies.orgwideapps.customapps
  - seo-marvel-mar2020
---

# Manage custom and sideloaded apps in Teams admin center

Microsoft Teams allows developers within your organization to build, test, and deploy custom apps for organization's internal users. Such apps are called custom apps or Line of Business (LOB) apps. Your organization may commission the creation of custom apps for org-specific requirements. Admins control the rollout of and permissions for custom apps using various settings and policies.

:::image type="content" source="media/custom-app-orgwide-setting-trimmed.png" alt-text="Screenshot that shows how to allow custom apps in your organization in the org-wide settings panel." lightbox="media/custom-app-orgwide-setting.png":::

After you allow the use of a custom app, your end-users can find it by selecting **Built for your org** in the left navigation of Teams store.

:::image type="content" source="media/built-for-your-org1.png" alt-text="Screenshot of custom apps in Teams' store in the Teams' desktop app." lightbox="media/built-for-your-org2.png":::

As a Teams admin, you use custom app policies and settings to control who in your organization can upload custom apps to Microsoft Teams. Admins decide which users can upload custom apps, and admins and team owners can determine whether specific teams in your organization allow custom apps to be added to them. After you edit the setup policy for custom apps, it takes a few hours for changes to take effect. You must be a Global Admin or Teams service admin to manage these policies.

Developers within your organization can add a custom app to Teams by uploading an app package (in a .zip file) directly to a team or in the personal context. This method is different from how apps are added through the Teams app store. Adding a custom app by uploading an app package, also known as sideloading, lets specific users within your organization to test an app, before it's ready to be widely distributed.

<!--- During the creation of an app, the developers create and add an app ID to the manifest file. You can view this external app ID on the Manage apps page after you enable the column `External app ID` from the column settings. You can also view it on the app details page of a custom app. The ID is applicable for custom apps only. --->

## Understand sideloading of custom apps

When developing custom apps and before distributing those apps to the end-users, developers test the apps by adding it to Teams Store to test. The developers can test on their own or with a specified group of users, but the app isn't available to other end-users in the organization via the store. This method is called sideloading of apps and applies only to custom apps.

Developers can sideload an app to make it available to the members of a specific team, typically to test an under-development app. Using an app in this way limits its usage to the app developers and doesn't require admin approval as long as admin allows sideloading in Teams.

Developers can share a sideloaded app with a specific team without submitting it to the Teams app catalog. It makes the sideloaded custom app available to a limited group of end-users but not available in your organization's app store for all end-users.

As an admin, you can disallow sideloading of app for all developers. If you disallow sideloading, the developers can still test their apps by [creating a separate test tenant](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant). Once custom app development is complete, developers request administrators to distribute their custom app to the end-users. For details, see [how to publish a custom app](/microsoftteams/upload-custom-apps). As an admin, you allow (or block) the use a custom app for all users or for specific users.

## App setup policy and settings for custom apps

Three settings determine whether a user can upload a custom app to a team. It gives admins granular control over who can add custom apps to a team and which teams custom apps can be added to. These settings don't affect the ability to block third-party apps.

* [User app setup policy settings for custom apps](#user-app-setup-policy-settings-for-custom-apps)
* [Team custom app setting](#team-custom-app-setting)
* [Org-wide custom app setting](#org-wide-custom-app-setting)

### User app setup policy settings for custom apps

As part of [app setup policies](teams-app-setup-policies.md), admins can use the setting **Upload custom apps**, to control whether a user can upload custom apps to Teams.

If this setting is turned off:

* The user can't upload a custom app to any team in your organization or in the personal context.
* The user can interact with custom apps, depending on the org-wide custom app setting.

If this setting is turned on:

* The user can upload custom apps to teams that allow it and to teams for which they are owners, depending on the org-wide custom app setting.
* The user can upload custom apps to the personal context.
* The user can interact with custom apps, depending on the org-wide custom app setting.

You can edit the settings in the global app setup policy to include the apps that you want. If you want to customize Teams for different groups of users in your organization, create and assign one or more custom app setup policies.

#### Set an app setup policy settings for custom apps

1. Sign in to the Teams admin center and access **Teams apps** > **[Setup policies](https://admin.teams.microsoft.com/policies/app-setup)**.
1. Select **Add**.
1. Provide a name and description for the policy.
1. Turn on or turn off **Upload custom apps** setting.
1. Choose any other settings that you want to for the policy.
1. Select **Save**.
1. [Apply the policy to users](assign-policies-users-and-groups.md#assign-a-policy-to-individual-users) who develop custom apps and are allowed to upload those apps.

> [!NOTE]
> To change this setting, allow custom apps in the [org-wide app settings](manage-apps.md#manage-org-wide-app-settings).

### Team custom app setting

Admins and team owners can control whether a team allows for custom apps to be added to it. The setting **Allow members to upload custom apps**, along with a user's custom app setting, determines who can add custom apps to a particular team.

If this setting is turned off:

* Team owners can add custom apps, if their app setup policy settings for custom apps allows it.
* Team members who aren't team owners can't add custom apps to the team.

If this setting is turned on:

* Team owners can add custom apps, if their settings for custom apps allows for it.
* Team members who aren't team owners can add custom apps, if their settings for custom apps allows for it.

#### Configure the team custom app setting

1. In Teams, go to a team, and select **More options ...** > **Manage team**.
1. Select **Settings** and expand **Member permissions**.
1. Select or clear the **Allow members to upload custom apps** check box.

   :::image type="content" source="media/teams-custom-app-policy-and-settings-team-trim.png" alt-text="Screenshot showing the team custom app setting." lightbox="media/teams-custom-app-policy-and-settings-team.png":::

### Org-wide custom app setting

The **Allow interaction with custom apps** org-wide custom app setting on the [Manage apps](manage-apps.md) page applies to everyone in your organization and governs whether they can upload or interact with custom apps. This setting acts as a master on or off switch for the user and team for settings related to custom apps. It's intended to serve as a master on/off switch during security events. User and team custom app settings take effect only after you enable the org-wide custom app setting.

#### Configure the org-wide custom app setting

1. Sign in to the Teams admin center and access **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.
1. Select **Org-wide app settings**.
1. Under **Custom apps**, turn on or turn off **Allow interaction with custom apps**.

    :::image type="content" source="media/teams-custom-app-policy-and-settings-org-wide.png" alt-text="Screenshot showing the org-wide custom app settings.":::

## How custom app policies and settings work together

This table summarizes the custom app settings, how they work together, and their combined effect on controlling who in your organization can upload custom apps to Teams.

Say, for example, you want to allow only team owners to upload custom apps to specific teams. You would set the following:

* Turn on the **Allow interaction with custom apps** setting in the Microsoft Teams admin center.
* Turn off the **Allow members to upload custom apps** for every team to which you want to restrict access.
* Create and assign a custom policy in app setup policy in the Microsoft Teams admin center with the **Upload custom apps** setting turned on, and assign it to the team owners.

|Org-wide custom app setting |Team custom app setting |User custom app settings | Effect  |
|---------|---------|---------|---------|
| Off    | Off    | Off     |Interaction with all custom apps is blocked for your organization. Custom apps can't be uploaded by anyone except a Teams Service Admin or a Global admin. You can use PowerShell to remove the custom app.   |
| Off     | Off     | On        |Interaction with all custom apps is blocked for your organization. Custom apps can't be uploaded by anyone except a Teams Service Admin or a Global admin. You can use PowerShell to remove the custom app.         |
| Off    | On        | Off        |Interaction with all custom apps is blocked for your organization. Custom apps can't be uploaded by anyone except a Teams Service Admin or a Global admin. You can use Windows PowerShell to delete custom apps.         |
| Off    | On      | On       |Interaction with all custom apps is blocked for your organization. Custom apps can't be uploaded by anyone except a Teams Service Admin or a Global admin. You can use PowerShell to remove the custom app.         |
| On    | Off       | Off         |  The user can't upload custom apps.      |
| On     | Off       | On         | If the user is a team owner, they can upload custom apps to the team. If the user isn't a team owner, they can't upload custom apps to the team. The user can upload custom apps in the personal context.     |
| On     | On     | Off         | The user can't upload custom apps.       |
| On    | On        | On        | The user can upload custom apps to the team, regardless of whether the user is a team owner. The user can upload custom apps in the personal context.       |

## Related articles

* [Admin settings for apps in Teams](admin-settings.md).
* [Assign policies to your users in Teams](assign-policies-users-and-groups.md).
