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
ms.date: 06/06/2023
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

Microsoft Teams allows developers within your organization to build, test, and distribute Teams apps for organization's internal users. Such apps are called custom apps or Line of Business (LOB) apps. Admins control the rollout of and access to custom apps using app policies and admin center settings.

:::image type="content" source="media/custom-app-orgwide-setting-trimmed.png" alt-text="Screenshot that shows how to allow custom apps in your organization in the org-wide settings panel." lightbox="media/custom-app-orgwide-setting.png":::

After you allow the use of a custom app, your users can find it by selecting **Built for your org** in the left navigation of Teams store.

:::image type="content" source="media/built-for-your-org1.png" alt-text="Screenshot of custom apps in Teams' store in the Teams' desktop app." lightbox="media/built-for-your-org2.png":::

As a Teams admin, you use custom app settings to control who in your organization can upload custom apps to Microsoft Teams. Admins decide which users can upload custom apps, and admins and team owners can determine whether specific teams in your organization allow custom apps to be added to them. After you edit the setup policy for custom apps, it takes a few hours for changes to take effect. You must be a Global Admin or Teams Administrator to manage these policies.

Developers within your organization can add a custom app to Teams by uploading an app package (in a .zip file) directly to a team or in the personal context. This method is different from how apps are added through the Teams app store. You add a custom app by uploading an app package and this method is called sideloading.

## Understand custom apps and sideloading

Your organization may commission the creation of custom apps for your org-specific requirements. Custom apps may be developed within your organization or by app developers outside the organization.

When developing custom apps and before distributing those apps to the users, developers test the apps by adding it to Teams Store. The developers can test on their own or with a specified group of users, but the app isn't available to other users in the organization via the store. This method is called sideloading of apps and applies only to custom apps.

Developers can sideload an app to make it available to the members of a specific team, typically to test an under-development app. Using an app in this way limits its usage to the app developers and doesn't require admin approval as long as admin allows sideloading in Teams.

Developers can share a sideloaded app with a specific team without submitting it to the Teams app catalog. It makes the sideloaded custom app available to a limited group of users but not available in your organization's app store for all users.

As an admin, you can disallow sideloading of app for all developers. If you disallow sideloading, the developers can still test their apps by [creating a separate test tenant](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant). Once custom app development is complete, developers request administrators to distribute their custom app to the users. For details, see [how to publish a custom app](/microsoftteams/upload-custom-apps). As an admin, you allow (or block) the use a custom app for all users or for specific users.

Sideloading is useful in the following scenarios:

* Test an app with a few specific users within your organization, before it's ready to be widely distributed.
* Provide an app to users of your organization only without publishing the app to the Teams app store.

## Allow users to upload custom apps

Microsoft Teams provides granular control over who can add custom apps to a team. To control if custom apps can be added to a team or not, admins and team owners use the following two settings. These settings don't affect the ability to block third-party apps.

* [**App setup policy**](#app-setup-policy-settings-for-custom-apps): A setting named **Upload custom apps** in the app setup policy determines which users in an organization are allowed to upload custom apps.
* [**Allow members to upload custom apps**](#team-setting-for-custom-app): This setting in each team determines if users of a team can upload custom apps or not.

| Setting in a team | Setting in app setup policy | Affects who can upload custom apps   |
|-------------------|-----------------------------|--------------------------------------|
| Off               | Off                         | No user                              |
| Off               | On                          | Only Team owners                     |
| On                | Off                         | No user                              |
| On                | On                          | Anybody                              |

### App setup policy settings for custom apps

To configure setup policy for custom apps, follow these steps:

1. Sign in to the Teams admin center and access **Teams apps** > **[Setup policies](https://admin.teams.microsoft.com/policies/app-setup)**.
1. Perform one of the following steps:

   * Select **Add** and provide a name and description for the policy. It creates a new policy.
   * Select an existing policy and select **Edit**.

1. Turn on or turn off the **Upload custom apps** option.
1. Select **Save**.
1. [Apply the policy to users](assign-policies-users-and-groups.md#assign-a-policy-to-individual-users) so that those users can upload custom apps.

To allow use of custom apps by an organization's users, see [org-wide app settings](manage-apps.md#manage-org-wide-app-settings).

### Team setting for custom app

To configure the custom apps related setting in a team, follow these steps as a team owner:

1. In Teams, go to a team, and select **More options ...** > **Manage team**.
1. Select **Settings** and expand **Member permissions**.
1. Select or clear the **Allow members to upload custom apps** check box.

   :::image type="content" source="media/teams-custom-app-policy-and-settings-team-trim.png" alt-text="Screenshot showing the team custom app setting." lightbox="media/teams-custom-app-policy-and-settings-team.png":::

## Allow your users to use custom apps

The **Allow interaction with custom apps** org-wide custom app setting in the Teams admin center applies to everyone in your organization and governs whether they can interact with custom apps or not. To configure the org-wide custom app setting, follow these steps:

1. Sign in to the Teams admin center and access **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.
1. Select **Org-wide app settings**.
1. Under **Custom apps**, turn on or turn off **Allow interaction with custom apps**.

    :::image type="content" source="media/teams-custom-app-policy-and-settings-org-wide.png" alt-text="Screenshot showing the org-wide custom app settings.":::

## Understand how all the custom app settings work together

This table summarizes the custom app settings and how the settings work together. The combined effect controls who in your organization can upload custom apps to Teams.

|Org-wide custom app setting |Team custom app setting |User custom app settings | Effect  |
|---------|---------|---------|---------|
| Off    | Off    | Off     |Interaction with all custom apps is blocked for your organization. Only a Teams Administrator or a Global Administrator can upload a custom app. You can use PowerShell to remove the custom app.   |
| Off     | Off     | On        |Interaction with all custom apps is blocked for your organization. Only a Teams Administrator or a Global Administrator can upload a custom app. You can use PowerShell to remove the custom app.         |
| Off    | On        | Off        |Interaction with all custom apps is blocked for your organization. Only a Teams Administrator or a Global Administrator can upload a custom app. You can use Windows PowerShell to delete custom apps.         |
| Off    | On      | On       |Interaction with all custom apps is blocked for your organization. Only a Teams Administrator or a Global Administrator can upload a custom app. You can use PowerShell to remove the custom app.         |
| On    | Off       | Off         |  The user can't upload custom apps.      |
| On     | Off       | On         | If the user is a team owner, they can upload custom apps to the team. If the user isn't a team owner, they can't upload custom apps to the team. The user can upload custom apps in the personal context.     |
| On     | On     | Off         | The user can't upload custom apps.       |
| On    | On        | On        | The user can upload custom apps to the team, regardless of whether the user is a team owner. The user can upload custom apps in the personal context.       |

Consider a scenario where you want to allow only team owners to upload custom apps to specific teams and users to use it. To accomplish this result, implement the following settings:

* Turn on the **Allow interaction with custom apps** setting in the Microsoft Teams admin center.
* Turn off the **Allow members to upload custom apps** for every team to which you want to restrict access.
* Create and assign a custom policy in app setup policy in admin center with the **Upload custom apps** setting turned on and assign the policy to the team owners.

## Related article

* [Assign policies to your users in Teams](assign-policies-users-and-groups.md)
