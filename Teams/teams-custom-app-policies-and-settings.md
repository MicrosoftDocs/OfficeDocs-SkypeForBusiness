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
ms.date: 08/26/2024
ms.reviewer: mhayrapetyan
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

# Manage custom apps in Microsoft Teams admin center

Your organization can commission creation of Teams apps that work only within your organization. Such apps are available within your organizations or tenant but aren't available on the Teams store. Users can discover and use such apps from Teams client and admins can govern such apps from the admin centers, but such apps aren't available on [AppSource](https://appsource.microsoft.com/). Such apps are called custom apps.

As a Teams Administrator or a Global Administrator, you use various settings to control the following scenarios:

* Let users add custom apps to their Teams client for their personal use.
* Let users use specific custom apps from amongst all the custom apps available in your org.
* Disallow all users to not use custom apps.
* Allow or disallow team users to add custom apps to a particular team.

:::image type="content" source="media/upload-custom-apps.png" alt-text="Overview of a custom app from development to deployment.":::

After you roll out a custom app, the permitted users can find it in the **Built for your org** section of the Teams store in their Teams client.

:::image type="content" source="media/built-for-your-org1.png" alt-text="Screenshot of custom apps in Teams store in the Teams desktop app." lightbox="media/built-for-your-org2.png":::

## Understand custom apps and the available settings

Your organization can commission the creation of custom apps for your org-specific requirements. Custom apps can be developed within your organization or by app developers outside the organization.

The following are the methods to make custom apps available in your organization's store, in a team, or for a few users.

| Method to upload custom app | Who uploads and how | Scope of app availability | Who controls the upload option | Potential use case |
|-----------------------------|---------------------|---------------------------|--------------------------------|--------------------|
| **Custom app submission by user** | [Any user using Teams client](/microsoftteams/platform/concepts/deploy-and-publish/apps-upload) | Available to entire org after an admin approves | Submit option is available to all users and can't be turned off. Admins can disapprove any submission. | User wants to make a custom app available to their entire org, after admin approval. |
| **Custom app submission by user using API** | [Any user using Teams App Submission Graph API](submit-approve-custom-apps.md) | Available to entire org after an admin approves | Submit option is available to all users and can't be turned off. Admins can disapprove any submission. | User wants to make a custom app available to their entire org, after admin approval. |
| **Custom app upload by admin** | [Global or Teams administrators using Teams admin center](#upload-a-custom-app-using-teams-admin-center) or using Teams client | Available to entire org; no approval required | Available to all admins; can't disable. | Admins upload custom apps for entire org. Custom app is received as zip package. |
| **Custom app upload by user**  | [Any user using Teams client](/microsoftteams/platform/concepts/deploy-and-publish/apps-upload) | No admin approvals required | Admins control which users can upload. | <li>App makers test their custom app in personal context or with a few users in a team before distribution. </li> <li>A few users use an app without making the app available in the organization's app catalog. </li> |

As Teams administrator, you have the following controls on upload and use of custom apps.

| Custom app governance | Setting available to admins | Impact on users |
|-----------------------|-----------------------------|-----------------|
| Allow or disallow specific users from uploading custom apps | Use [app setup policy](#allow-users-to-upload-custom-apps) | You apply app setup policy to specific users to allow or disallow them from uploading custom app in personal context or in a team. Users can still submit custom apps for your approval. |
| Allow or disallow all users from uploading custom apps | Use [custom app setting in Org-wide app settings](manage-apps.md#manage-org-wide-app-settings) | Users can't upload custom apps even in their personal context. Users can still submit custom apps for your approval. |
| Restrict app access for a few users | Use [app permission policy](teams-app-permission-policies.md) | You granularly control which users have access to what particular custom app (also applies to third-party apps). |
| Delete a custom app | [Delete an app](#delete-custom-apps-from-your-organizations-catalog) | The deleted app isn't available in your org. Existing app users also can't use it anymore. |

If you disallow custom app upload, app developers can [create a separate test tenant to test apps](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant). Once custom app development is complete, app creators request admins to distribute their custom app. For details, see [how to publish a custom app](/microsoftteams/upload-custom-apps). As an admin, you allow or block the use of a custom app for all users or for specific users.

## Upload a custom app using Teams admin center

To make a custom app available to users in your organization's app store, follow these steps:

1. Access Teams admin center and go to **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Perform one of the following tasks depending on your UI:

   * Select **Upload new app**, select **Upload**, and select the app package that the developer provided to you.
   * Select **Actions** > **Upload new app** and upload the app.

   :::image type="content" source="media/custom-app-upload-option.png" alt-text="Screenshot showing the option for admins to upload a custom app from Teams admin center.":::

The uploaded app is available to the org users after a few hours.

## Update a custom app using Teams admin center

Just like third-party apps in the Teams store get updates, developers update custom apps. You can update a custom app in your org catalog to a newer version by uploading a new version of the app. To update, select **Upload file** from the app details page.

:::image type="content" source="media/update-custom-app-version.png" alt-text="Screenshot showing the option to upload a new version of a custom app in admin center.":::

When a new version of an app is published, the existing policies that applied to the previous version of the app continue to be in effect for the updated version.

Alternatively, an org user can submit an updated custom app for your approval. When you approve the app, the newer version is available in the org catalog.

## Allow users to upload custom apps

Microsoft Teams provides granular control over who can add custom apps to a team. To control if custom apps can be added to a team or not, admins and team owners use the following settings. These settings don't affect the ability to block third-party apps.

* [**Org-wide app settings**](manage-apps.md#manage-org-wide-app-settings) for entire organization: The setting named **Let users interact with custom apps in preview** lets you either allow or disallow all your users across the organization to upload custom apps. Users can upload custom apps only for their personal use or within their teams.

   :::image type="content" source="media/teams-custom-app-policy-and-settings-org-wide.png" alt-text="Screenshot showing the org-wide custom app settings.":::

* [**App setup policy**](#app-setup-policy-settings-for-custom-apps) for specific users: The setting named **Upload custom apps** in the app setup policy lets assigned users upload custom apps. You can use this setting to allow specific users in your org to upload custom apps.

   :::image type="content" source="media/upload-custom-app-setup-policy.png" alt-text="Screenshot showing the custom app option available in an app setup policy.":::

* [**Allow members to upload custom apps**](#team-setting-for-custom-app) at team level: This setting in each team determines if users of a team can upload custom apps or not. Team owners and Teams admins can modify this setting. Using this setting, team owners can prevent custom app upload to a specific team even if the users are allowed to upload custom apps.

If an admin uploads a custom app, it's available in the organization's catalog in the store without requiring any approval. You can allow some org users using app permission policy to use such an app. The impact of team setting and app setup policy on user's ability to upload custom apps is summarized in the following table.

| [Upload setting in a team](#team-setting-for-custom-app) | [Upload setting in app setup policy](#app-setup-policy-settings-for-custom-apps) | Who can upload for personal or team use | Who can upload for admin approval |
|----------------------------------------------------------|----------------------------------------------------------------------------------|-----------------------------------------|-----------------------------------|
| Off                                                      | Off                                                                              | No user                                 | Any user                          |
| Off                                                      | On                                                                               | Only Team owners                        | Any user                          |
| On                                                       | Off                                                                              | No user                                 | Any user                          |
| On                                                       | On                                                                               | Anybody                                 | Any user                          |

### App setup policy settings for custom apps

You can use a setting in the app setup policy to allow or disallow users from uploading custom apps. This setting is useful when you want to allow only specific users in the organization to upload custom apps. To [allow all users to upload custom apps](#allow-users-to-upload-custom-apps), use the custom app setting in Org-wide app settings.

1. Sign in to the Teams admin center and access **Teams apps** > **[Setup policies](https://admin.teams.microsoft.com/policies/app-setup)**.

1. Perform one of the following steps:

   * Select **Add** and provide a name and description to create a new policy.
   * Select an existing policy and select **Edit**.

1. Turn on or turn off the **Upload custom apps** option to allow or disallow users from uploading custom apps, respectively.

1. Select **Save**.

1. [Apply the policy to users](assign-policies-users-and-groups.md#assign-a-policy-to-individual-users) so that those users can upload custom apps.

To allow use of custom apps in a user's personal or team scope, see [org-wide app settings](manage-apps.md#manage-org-wide-app-settings).

### Team setting for custom app

To configure the custom apps related setting in a team, follow these steps as a team owner:

1. In Teams, go to a team, and select **More options ...** > **Manage team**.

   :::image type="content" source="media/manage-team-settings.png" alt-text="Screenshot showing the Manage team option to change settings of a team.":::

1. Select **Settings** and expand **Member permissions**.

1. Select or clear the **Allow members to upload custom apps** option.

   :::image type="content" source="media/teams-custom-app-policy-and-settings-team-trim.png" alt-text="Screenshot showing the team custom app setting." lightbox="media/teams-custom-app-policy-and-settings-team.png":::

## Delete custom apps from your organization's catalog

You as an admin can delete custom apps from your organization's store. On the app details page, select **More commands** > **Actions** > **Delete**.

:::image type="content" source="media/delete-custom-app.png" alt-text="Screenshot showing the option in admin center to delete or remove a custom app.":::

## Understand how all the custom app settings work together

This table summarizes the custom app settings and how the settings work together. The combined effect controls who in your organization can upload custom apps to Teams.

| Org-wide app setting for custom app upload | Team-level custom app setting | User-level custom app settings via app setup policy | Effect |
|--------------------------------------------|-------------------------------|-----------------------------------------------------|--------|
| Off | Off | Off | Upload custom apps option is unavailable in your organization. Users can submit custom apps for admin approval. |
| Off | Off | On  | Upload custom apps option is unavailable in your organization. Users can submit custom apps for admin approval. |
| Off | On  | Off | Upload custom apps option is unavailable in your organization. Users can submit custom apps for admin approval. |
| Off | On  | On  | Upload custom apps option is unavailable for your organization. Users can submit custom apps for admin approval. |
| On  | Off | Off | The user can't upload custom apps for their own use. Users can submit custom apps for admin approval. |
| On  | Off | On  | If the user is a team owner, they can upload custom apps to the team. If the user isn't a team owner, they can't upload custom apps to the team. The user can upload custom apps in the personal context. Users can submit custom apps for admin approval. |
| On  | On  | Off | The user can't upload custom apps for their own use. Users can upload custom apps for admin approval. |
| On  | On  | On  | The user can upload custom apps to the team, regardless of whether the user is a team owner. The user can upload custom apps in the personal context and submit it for admin approval. |

## Samples scenarios for custom app

To allow only a few selected users or groups to upload and use custom apps, follow these steps:

1. Turn on the **Let users interact with custom apps in preview** option in Org-wide app setting in admin center.
1. Turn off the **Upload custom apps** setting in the global [app setup policy](#app-setup-policy-settings-for-custom-apps).
1. Create a new app setup policy that allows uploading custom apps and [assign the policy to the selected users or groups](policy-assignment-overview.md#ways-to-assign-policies).

Consider a scenario where you want to allow only team owners to upload custom apps to specific teams. To accomplish this result, implement the following settings:

* Turn on the **Let users interact with custom apps in preview** option in the Org-wide app setting in admin center.
* Turn off the **Allow members to upload custom apps** for every team to which you want to restrict access.
* Create and assign a custom policy in app setup policy in admin center with the **Upload custom apps** setting turned on and assign the policy to the team owners.

## Custom apps in 21Vianet and air-gapped cloud environments

You can [upload custom apps](#upload-a-custom-app-using-teams-admin-center) in Microsoft 365 operated by 21Vianet and air-gapped cloud environments by using the Teams apps > Manage apps page. Also, you can [update your existing custom app](#update-a-custom-app-using-teams-admin-center) from the app details page.

## Related article

* [Assign policies to your users in Teams](assign-policies-users-and-groups.md)
