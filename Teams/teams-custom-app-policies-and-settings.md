---
title: Manage custom app policies and settings
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.tgt.pltfrm: cloud
ms.subservice: teams-apps
ms.service: msteams
audience: Admin
ms.date: 07/31/2023
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
ms.localizationpriority: high
search.appverid: MET150
description: Learn how to manage policies and settings to control who in your organization can upload custom apps.
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.apppermspolicies.orgwideapps.customapps
  - ms.teamsadmincenter.appsetuppolicies.allowsideloading
  - ms.teamsadmincenter.appsetuppolicies.tooltip.allowsideloading
  - ms.teamsadmincenter.apppermspolicies.orgwideapps.customapps
  - seo-marvel-mar2020
---

# Manage custom apps in Teams admin center

Developers associated with your organization can build, test, and distribute Teams apps for your organization's users. Such apps are called custom apps and are available only within your organization or tenant.

As a Teams Administrator or a Global Administrator, you use various settings to control the following scenarios:

* Who can upload custom apps to Microsoft Teams for their personal use
* Which custom apps you allow for all org users that developers submit for your approval
* Whether users can use custom apps or not
* Allow or disallow upload of custom apps to a particular team

:::image type="content" source="media/upload-custom-apps.png" alt-text="Overview of a custom app from development to deployment.":::

After you roll out a custom app, the permitted users can find it in the **Built for your org** section of the Teams store in their Teams client.

:::image type="content" source="media/built-for-your-org1.png" alt-text="Screenshot of custom apps in Teams store in the Teams desktop app." lightbox="media/built-for-your-org2.png":::

## Understand custom apps and the available settings

Your organization may commission the creation of custom apps for your org-specific requirements. Custom apps may be developed within your organization or by app developers outside the organization.

The following are the methods to make custom apps available in your organization's store, in a team, or for a few users.

| Method to upload custom app | Who uploads and how | Scope of app availability | Who controls the upload option | Potential use case |
|-----------------------------|-------------|---------------------------|---------------------------|---------------------------|
| **Custom app submission by user** | [Any user using Teams client](/microsoftteams/platform/concepts/deploy-and-publish/apps-upload) | Available to entire org after an admin approves | Submit option is available to all users and can't be turned off. Admins can disapprove any submission. | User wants to make a custom app available to their entire org, after admin approval. |
| **Custom app submission by user using API** | [Any user using Teams App Submission Graph API](submit-approve-custom-apps.md) | Available to entire org after an admin approves | Submit option is available to all users and can't be turned off. Admins can disapprove any submission. | User wants to make a custom app available to their entire org, after admin approval. |
| **Custom app upload by admin** | [Global or Teams administrators using Teams admin center](#upload-a-custom-app-using-teams-admin-center) or using Teams client | Available to entire org immediately; no approval required | Available to all admins; can't disable. | Admins upload custom apps for entire org. Custom app is received as zip package. |
| **Custom app upload by user**  | [Any user using Teams client](/microsoftteams/platform/concepts/deploy-and-publish/apps-upload) | No admin approvals required | Admins control which users can upload. | <li>App makers test their custom app in personal context or with a few users in a team before distribution. </li> <li>A few users use an app without making the app available in the organization's app catalog. </li> |

As Teams administrator, you have the following controls on upload and use of custom apps.

| Custom app management task | Setting available to admins | Impact on users |
|----------------------------|-----------------------------|-----------------|
| Allow users to upload custom apps | Use [app setup policy](#allow-users-to-upload-custom-apps) | Users can upload custom apps in personal context or in their team if allowed by team owner. |
| Disallow users from uploading custom apps | Use [app setup policy](#allow-users-to-upload-custom-apps) | Users can't upload custom apps in personal context or in their team. Users can still submit custom apps for your approval. Until you approve, the app remains unavailable for use. |
| Disallow use from using custom apps | Use [custom app setting in org-wide settings](#allow-your-users-to-use-custom-apps) | Users can't use custom apps that anyone has uploaded. |
| Restrict access to a few users | Use [app permission policy](teams-app-permission-policies.md) | You granularly control which users have access to which particular custom app. |
| Delete a custom app | Delete an app | The deleted app isn't available in the tenant. It's removed for existing users too. |

If you disallow custom app upload, app creators must [create a separate test tenant to test apps](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant). Once custom app development is complete, app creators request admins to allow and distribute their custom app. For details, see [how to publish a custom app](/microsoftteams/upload-custom-apps). As an admin, you allow (or block) the use a custom app for all users or for specific users.

## Upload a custom app using Teams admin center

To make the app available to users in your organization's app store, follow these steps:

1. Access Teams admin center and go to **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Select **Upload new app**, select **Upload**, and select the app package that you received from the developer.

## Update a custom app using Teams admin center

To update and existing custom app, follow these steps:

1. Access Teams admin center and go to **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Select the name of the existing custom app to open its app details page.

1. On the banner of the app, select **Upload file**, and provide the updated app package.

When a new version of an app is published, the existing policies for that app remain enforced for the updated app.

## Allow users to upload custom apps

Microsoft Teams provides granular control over who can add custom apps to a team. To control if custom apps can be added to a team or not, admins and team owners use the following two settings. These settings don't affect the ability to block third-party apps.

* [**App setup policy**](#app-setup-policy-settings-for-custom-apps): A setting named **Upload custom apps** in the app setup policy determines which users in an organization are allowed to upload custom apps.
* [**Allow members to upload custom apps**](#team-setting-for-custom-app): This setting in each team determines if users of a team can upload custom apps or not. Team owners and admins can modify this setting.

| [Custom app upload setting in a team](#team-setting-for-custom-app) | [Custom app upload setting in app setup policy](#app-setup-policy-settings-for-custom-apps) | Who can upload custom apps for personal or team-level use | Who can upload custom apps for admin approval |
|-------------------|-----------------------------|--------------------------------------|--------------------------------------|
| Off               | Off                         | No user                              | Any user |
| Off               | On                          | Only Team owners                     | Any user |
| On                | Off                         | No user                              | Any user |
| On                | On                          | Anybody                              | Any user |

### App setup policy settings for custom apps

To allow users to upload custom apps, follow these steps to configure the setup policy:

1. Sign in to the Teams admin center and access **Teams apps** > **[Setup policies](https://admin.teams.microsoft.com/policies/app-setup)**.

1. Perform one of the following steps:

   * Select **Add** and provide a name and description to create a new policy.
   * Select an existing policy and select **Edit**.

1. Turn on or turn off the **Upload custom apps** option to allow or disallow users from uploading custom apps.

1. Select **Save**.

1. [Apply the policy to users](assign-policies-users-and-groups.md#assign-a-policy-to-individual-users) so that those users can upload custom apps.

To allow use of custom apps in a user's personal or team scope, see [org-wide app settings](manage-apps.md#manage-org-wide-app-settings).

### Team setting for custom app

To configure the custom apps related setting in a team, follow these steps as a team owner:

1. In Teams, go to a team, and select **More options ...** > **Manage team**.
1. Select **Settings** and expand **Member permissions**.
1. Select or clear the **Allow members to upload custom apps** check box.

   :::image type="content" source="media/teams-custom-app-policy-and-settings-team-trim.png" alt-text="Screenshot showing the team custom app setting." lightbox="media/teams-custom-app-policy-and-settings-team.png":::

## Allow your users to use custom apps

The **Interaction with custom apps** option in the org-wide setting applies to everyone in your organization and governs whether they can interact with custom apps in their personal or team context or not. To configure the org-wide custom app setting, follow these steps:

1. Sign in to the Teams admin center and access **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.
1. Select **Org-wide app settings**.
1. Under **Custom apps**, turn on or turn off **Interaction with custom apps**.

    :::image type="content" source="media/teams-custom-app-policy-and-settings-org-wide.png" alt-text="Screenshot showing the org-wide custom app settings.":::

Custom apps that are available for entire organization are the apps that an admin directly uploads or a user requests that an admin approves. Such apps aren't limited in scope to a user's personal or team scope. All permitted users can use such tenant-wide custom apps, even if interaction is turned off using the following setting.

## Understand how all the custom app settings work together

This table summarizes the custom app settings and how the settings work together. The combined effect controls who in your organization can upload custom apps to Teams.

| Org-wide setting for custom app interaction | Team-level custom app setting | User-level custom app settings via app setup policy | Effect |
|---------------------------------------------|-------------------------------|-------------------------------------------------|--------|
| Off    | Off    | Off     | Interaction with all custom apps is blocked for your organization. Users can upload custom apps for admin approval. |
| Off     | Off     | On        |Interaction with all custom apps is blocked for your organization. Users can upload custom apps for admin approval. |
| Off    | On        | Off        |Interaction with all custom apps is blocked for your organization. Users can upload custom apps for admin approval. |
| Off    | On      | On       |Interaction with all custom apps is blocked for your organization. Users can upload custom apps for admin approval. |
| On    | Off       | Off         |  The user can't upload custom apps for their own use. Users can upload custom apps for admin approval. |
| On     | Off       | On         | If the user is a team owner, they can upload custom apps to the team. If the user isn't a team owner, they can't upload custom apps to the team. The user can upload custom apps in the personal context. Users can upload custom apps for admin approval. |
| On     | On     | Off         | The user can't upload custom apps for their own use. Users can upload custom apps for admin approval. |
| On    | On        | On        | The user can upload custom apps to the team, regardless of whether the user is a team owner. The user can upload custom apps in the personal context and upload for admin approval. |

## Samples scenarios for custom app

To allow only a few selected users or groups to upload and use custom apps, follow these steps:

1. Turn on the **Interaction with custom apps** option in Org-wide app setting.
1. Turn off the **Upload custom apps** setting in the [app setup policy](#app-setup-policy-settings-for-custom-apps).
1. Create a new app setup policy that allows uploading custom apps and [assign the policy to the selected users or groups](policy-assignment-overview.md#ways-to-assign-policies).

Consider a scenario where you want to allow only team owners to upload custom apps to specific teams and users to use it. To accomplish this result, implement the following settings:

* Turn on the **Interaction with custom apps** option in the Org-wide app setting in admin center.
* Turn off the **Allow members to upload custom apps** for every team to which you want to restrict access.
* Create and assign a custom policy in app setup policy in admin center with the **Upload custom apps** setting turned on and assign the policy to the team owners.

## Considerations about custom apps and related settings

* If interaction with custom apps option in org-wide app setting is turned off, then even if users can search apps with their `botId` and they can view the app name, but the users can't interact with such bots.

## Related article

* [Assign policies to your users in Teams](assign-policies-users-and-groups.md)
