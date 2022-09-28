---
title: Manage app permission policies in Microsoft Teams
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-apps
audience: Admin
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
ms.localizationpriority: high
search.appverid: MET150
description: Learn about app permission policies in Microsoft Teams and how to control apps availability for your end-users.
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.apppermspolicies.overview
  - ms.teamsadmincenter.appsetuppolicies.addpinnedapp.permissions
  - ms.teamsadmincenter.apppermspolicies.orgwideapps.customapps
  - ms.teamsadmincenter.appsetuppolicies.overview
---

# Manage access to Teams apps using app permission policies

As an admin, you can use app permission policies to control the apps that are available to each user in your organization. The permissions you set to allow or block all apps or specific apps are applicable to all [types of apps in Teams](deploy-apps-microsoft-teams-landing-page.md). You must be a Global Admin or Teams service admin to manage these policies.

To allow an app, you must allow it in [Org-wide app settings](manage-apps.md#manage-org-wide-app-settings), [individual app's setting](manage-apps.md#allow-and-block-apps), and app permission policy. While the other two methods just allow an app for use in your organization, the permission policies allow you to control which users can use a specific app. You control access on a per-user and per-app basis by creating and applying the policy to specific users.

Teams admin center lets you create the following two types of permissions policy:

* `Global (Org-wide default)` policy exists by default and applies to all users. Any changes made to this policy impact all users as this policy is applied to all users by default.
* An admin-created policy applies only to the users that it is applied to. Create a new policy to allow apps for specific users or group of users.

   :::image type="content" source="media/app-permission-policy-trimmed.png" alt-text="Screenshot showing a new app permission policy being created." lightbox="media/app-permission-policy.png":::

If your organization is already on Teams, the app settings you configured in **Tenant-wide settings** in the Microsoft 365 admin center are reflected in org-wide app settings on the [Manage apps](https://admin.teams.microsoft.com/policies/manage-apps) page in Teams admin center. If you're new to Teams and just getting started, by default, all apps are allowed in the org-wide global setting. It includes apps published by Microsoft, third-party software providers, and your organization.

> [!NOTE]
> To know about third-party app settings in Microsoft 365 Government Community Cloud High (GCCH) and Department of Defense (DoD) environment, see [Manage org-wide app settings for Microsoft 365 Government](#manage-org-wide-app-settings-for-microsoft-365-government).

## Create an app permission policy

Use one or more custom app permission policies, if you want to control the apps that are available for different groups of users. You can create and assign separate custom policies based on whether apps are published by Microsoft, third-parties, or your organization. After you create a custom policy, you can't change it if third-party apps are disabled in org-wide app settings.

1. Sign in to Teams admin center and access **Teams apps** > **[Permission policies](https://admin.teams.microsoft.com/policies/app-permission)**.
1. Select **Add**.
1. Provide a name and description for the policy.
1. Under **Microsoft apps**, **Third-party apps**, and **Custom apps**, select one of the following options:

    * `Allow all apps`
    * `Allow specific apps and block all others`
    * `Block specific apps and allow all others`
    * `Block all apps`

1. If you selected **Allow specific apps and block all others**, add the apps that you want to allow:

    1. Select **Allow apps**.
    1. Search for the apps that you want to allow, and then select **Add**. The search results are filtered to the app developer (**Microsoft apps**, **Third-party apps**, or **Custom apps**).
    1. After choosing one or more apps, select **Allow**.

1. If you selected **Block specific apps and allow all others**, similarly search for and choose the apps that you want to block, and then select **Block**.

1. Select **Save**.

## Edit an app permission policy

You can use the Teams admin center to edit the global policy or any custom policies that you've created.

1. Sign in to the Teams admin center and access **Teams apps** > **[Permission policies](https://admin.teams.microsoft.com/policies/app-permission)**.
1. Select the policy by clicking to the left of the policy name, and then select **Edit**.
1. Make the changes to allow or block specific apps in each of the three categories.
1. Select **Save**.

## Assign a custom app permission policy to users

App permission policies take effect only when you apply a policy to a user or a group of users. See the different ways to [assign the policy to users](policy-assignment-overview.md#ways-to-assign-policies).

## Manage org-wide app settings for Microsoft 365 Government  

In a Microsoft 365 Government - GCC, GCCH and DoD deployment of Teams, all third-party apps are blocked by default. In GCCH and DOD clouds, the third-party apps aren't available. Additionally, in GCC, you see the following note about managing third-party apps on the app permission policies page in the Microsoft Teams admin center.

:::image type="content" source="media/app-permission-policies-gcc.png" alt-text="Screenshot of app permission policy in GCCH and DoD.":::

Use org-wide app settings to control whether users can install third-party apps. Org-wide app settings govern the behavior for all users and override any other app permission policies assigned to users.

<!---1. On the **Permission policies** page, select **Org-wide app settings**. You can then configure the settings you want in the panel. 
--->

### For GCC clouds

1. On the **Teams Apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)** page, select **Org-wide app settings**. You can then configure the settings you want in the panel.

   :::image type="content" source="media/app-permission-policies-gcc-org-wide.png" alt-text="Screenshot of org-wide app settings in GCC.":::

1. Under **Third-party apps**, turn off or turn on these settings to control access to third-party apps:

    * **Allow third-party apps**: This option controls whether users can use third-party apps. If you turn off this setting, your users won't be able to install or use any third-party apps. In a Microsoft 365 Government - GCCH and DoD deployment of Teams, this setting is off by default.
    * **Allow any new third-party apps published to the store by default**: This option controls whether new third-party apps that are published to the Teams app store become automatically available in Teams. You can only set this option if you allow third-party apps.

1. Under **Blocked apps**, add the apps you want to block across your organization. In a Microsoft 365 Government - GCCH and DoD deployment of Teams, all third-party apps are added to this list by default. For any third-party app you want to allow in your organization, remove the app from this blocked apps list. When you block an app org-wide, the app is automatically blocked for all your users, regardless of whether it's allowed in any app permission policies.

1. Select **Save** for org-wide app settings to take effect.

To allow third-party apps, either edit and use the global (Org-wide default) policy or create and assign custom policies.

### For GCCH and DoD clouds

1. Sign in to the Teams admin center and access **Teams Apps** > **[Permission policies](https://admin.teams.microsoft.com/policies/app-permission)**.

1. Select **Org-wide app settings**. Under **Blocked apps**, add the apps you want to block across your organization. In a Microsoft 365 Government - GCCH and DoD deployment of Teams, all third-party apps are added to this list by default. When you block an app org-wide, the app is automatically blocked for all your users, regardless of whether it's allowed in any app permission policies.

   :::image type="content" source="media/app-permission-policies-gcch-dod-org-wide.png" alt-text="Screenshot of org-wide app settings in GCCH and DoD.":::

1. Select **Save** for org-wide app settings to take effect.

## Considerations when using app permission policies

The following are a few considerations when using app permissions policies to grant access or to disallow access to apps:

* App permission policies take effect only when you apply a policy to a user or a group of users.

* After you edit or assign a policy, it can take a few hours for changes to take effect.

* An end-user cannot interact with any functionality of an app that the user is not allowed to use.

* Users can search for blocked apps and request admin approval. Admins retain complete control to [approve or ignore user requests](user-requests-approve-apps.md).

* You can use app setup policies together with app permission policies. Pre-pinned apps are selected from the set of enabled apps for a user. Additionally, if a user has an app permission policy that blocks an app in their app setup policy, that app won't appear in Teams.

* App policies apply to users using any Teams on web, mobile, or desktop.

## Related articles

* [Admin settings for apps in Teams](admin-settings.md)
* [Assign policies to your users in Teams](policy-assignment-overview.md)
* [Teams feature availability comparison](/office365/servicedescriptions/teams-service-description#feature-availability)
