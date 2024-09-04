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
ms.date: 09/03/2024
ms.reviewer: mhayrapetyan
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
ms.localizationpriority: high
search.appverid: MET150
description: Learn how to control availability of Teams apps for users by using permission policies and how to create, edit, assign, and unassign the policies.
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.apppermspolicies.overview
  - ms.teamsadmincenter.appsetuppolicies.addpinnedapp.permissions
  - ms.teamsadmincenter.apppermspolicies.orgwideapps.customapps
  - ms.teamsadmincenter.appsetuppolicies.overview
---

# Use app permission policies to control user access to apps

> [!IMPORTANT]
> If your organization is moved to app centric management feature to manage access to apps, see [Manage access to Teams apps using app centric management](app-centric-management.md). Permission policies will no longer apply and you may see this message on the policy page. If policies are available, you can continue to use those. We will soon let you migrate to app centric management on your own.
> 
> :::image type="content" source="media/acm-policy-page.png" alt-text="Screenshot showing the permissions policy change for organization that are using app centric management.":::

As an admin, you can use app permission policies to control the apps that are available to each user in your organization. The permissions you set to allow or block all apps or specific apps are applicable to all [types of apps in Teams](apps-in-teams.md). To understand policies, see [app permission policies](app-policies.md). You must be a Teams Administrator or have a higher role to manage these policies.

To allow an app, you must allow it in [Org-wide app settings](manage-apps.md#manage-org-wide-app-settings), [individual app's setting](manage-apps.md#allow-or-block-apps), and app permission policy. While the first two settings just allow an app for use in your organization, the permission policies allow you to control which users can use a specific app. You control the access on a per-user and per-app basis by creating and applying the policy to specific users.

Teams admin center lets you create two types of permissions policies:

* **Global (Org-wide default)** policy exists by default and applies to all users. Any changes made to this policy affect all users as this policy is applied to all users by default.
* An admin-created policy applies only to the users that it's applied to. Create a new policy to allow apps for specific users.

   :::image type="content" source="media/app-permission-policy-trimmed.png" alt-text="Screenshot showing a new app permission policy being created.":::

If your organization is already on Teams, the app settings you configured in **Tenant-wide settings** in the Microsoft 365 admin center are reflected in **Org-wide app settings** on the [Manage apps](https://admin.teams.microsoft.com/policies/manage-apps) page in Teams admin center. If you're new to Teams and just getting started, by default, all apps are allowed in the org-wide global setting. It includes apps published by Microsoft, third-party software providers, and your organization.

Alternately, you can use [app centric management](app-centric-management.md) to configure the access to apps on a per-app basis. It offers an easier method to configure access to apps. The app centric management functionality replaces app permissions policies by making it easier for admins to specify the users and group in their organization who can add or install Teams apps on a per-app basis. You can use only one method to define access to apps in your organization. If you choose to, you can migrate from app permission policies to app centric management using our migration UI.

> [!NOTE]
> To know about third-party app settings in Microsoft 365 Government Community Cloud High (GCCH) and Department of Defense (DoD) environment, see [Manage org-wide app settings for Microsoft 365 Government](manage-apps.md#manage-org-wide-app-settings-for-microsoft-365-government).

## Create an app permission policy

Use one or more custom app permission policies, if you want to control the apps that are available to different users. You can create and assign separate custom policies based on whether apps are published by Microsoft, third parties, or your organization. After you create a custom policy, you can't change it if third-party apps are disabled in org-wide app settings. To create an app permission policy, follow these steps:

1. Sign in to the Teams admin center and go to **Teams apps** > **[Permission policies](https://admin.teams.microsoft.com/policies/app-permission)**.
1. Select **Add**.
1. Provide a name and description for the policy.
1. Under **Microsoft apps**, **Third-party apps**, and **Custom apps**, select one of the following options:

    * Allow all apps
    * Allow specific apps and block all others
    * Block specific apps and allow all others
    * Block all apps

1. If you selected **Allow specific apps and block all others**, add the apps that you want to allow:

    1. Select **Allow apps**.
    1. Search for the apps that you want to allow, and then select **Add**. The search results are filtered to the app developer (**Microsoft apps**, **Third-party apps**, or **Custom apps**).
    1. After choosing one or more apps, select **Allow**.

1. If you selected **Block specific apps and allow all others**, similarly, search and choose the apps that you want to block, and then select **Block**.

1. Select **Save**.

## Edit an app permission policy

You can use the Teams admin center to edit the global policy or any custom policies that you've created. To edit, follow these steps:

1. Sign in to the Teams admin center and access **Teams apps** > **[Permission policies](https://admin.teams.microsoft.com/policies/app-permission)**.
1. Select the policy by clicking to the left of the policy name, and then select **Edit**.
1. Make the changes to allow or block specific apps in each of the three categories.
1. Select **Save**.

## Assign a custom policy for app permissions to users

App permission policies take effect only when you apply a policy to a user. See the different ways to [assign the policy to users](policy-assignment-overview.md#ways-to-assign-policies).

Teams doesn't support group policy assignments for app permission policies.

## View the policies already applied to a user

You can use the Teams admin center to check the policies that are assigned to a user. To view the policies, follow these steps:

1. Sign in to the Teams admin center and go to **Users** > **[Manage users](https://admin.teams.microsoft.com/users)**.
1. Search for and select the user by clicking the user name.
1. Select **View policies** under the **Policies assigned** column.

    :::image type="content" source="media/manage-users-view-policies.png" alt-text="Screenshot that shows the option to view the existing policies applied to the user.":::

## Change the existing policies for an individual user

To change existing policies, follow these steps:

1. Sign in to the Teams admin center and go to **Users** >  **[Manage users](https://admin.teams.microsoft.com/users)**.
1. Search for and select the user by clicking to the left of the user name and then select **Edit settings**.
1. Select the policy you want to change, and then select **Apply**.

    :::image type="content" source="media/manage-users-edit-settings.png" alt-text="Screenshot that shows the options to change the existing policies.":::

> [!NOTE]
> To unassign a custom policy from a user, you can set each policy to **Global (Org-wide default)**.

You can also change existing policies for an individual user using PowerShell. For more information, see [assign policies to users](assign-policies-users-and-groups.md).

## Unassign app permission policies in bulk

When you unassign policies in bulk, you're removing policy assignments that were assigned to individual users through direct assignment. To unassign permission policies in bulk, follow these steps:

1. Sign in to the Teams admin center and go to **Teams apps** > **[Permission policies](https://admin.teams.microsoft.com/policies/app-permission)**.
1. Click on the policy's name and then select **Bulk unassign users** from the **Manage users** menu.

    :::image type="content" source="media/app-permission-policy-manage-users.png" alt-text="Screenshot that shows the bulk unassign users option from the manage user dropdown menu.":::

1. Choose the policy that you want to unassign and select **Load data** to get the number of users who are currently assigned to that policy.

    :::image type="content" source="media/unassign-policies-load-data.png" alt-text="Screenshot of the bulk unassign policies page with the load data option.":::

1. Select **Unassign**, and then select **Confirm**.

After you unassign policies, you can review operation details in the [Activity log](https://admin.teams.microsoft.com/activity-log).

## Considerations when using app permission policies

The following are a few considerations when using app permissions policies to grant access or to disallow access to apps:

* Teams doesn't support group policy assignments for app permission policies.

* App permission policies take effect only when you apply a policy to a user.

* After you edit or assign a policy, it can take a few hours for changes to take effect.

* A user can't interact with any functionality of an app that the user isn't allowed to use.

* Users can search for blocked apps and request admin approval. Admins retain complete control to [approve or ignore user requests](user-requests-approve-apps.md).

* App setup policies work together with app permission policies. You select apps to pin in setup policy from a set of allowed apps. However, if a user has an app permission policy that blocks the use of a pinned app, then the user can't use the app.

* App policies apply to users using Teams on web, mobile, or desktop clients.

## Related articles

* [Assign policies to your users in Teams](policy-assignment-overview.md)
* [Teams feature availability comparison](/office365/servicedescriptions/teams-service-description#feature-availability)
