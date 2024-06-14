---
title: Manage the Avatars app for Microsoft Teams 
author: MicrosoftHeidi
ms.author: tmilligan
manager: tyadams
audience: ITPro
ms.reviewer: sekerawa
ms.date: 05/29/2024
ms.topic: quickstart
ms.service: msteams
search.appverid: MET150
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - teams-1p-app-admin
description: Learn how to set up the avatars for Microsoft Teams app.
---

# Manage the Avatars app in Microsoft Teams

The Avatars app is enabled by default for all organizations.

As an admin, you can control whether avatars for Teams is available in your organization and who can use Avatars using [Teams Admin Center](manage-apps.md) policies, Microsoft 365 service plans, or [App centric management](app-centric-management.md) of Teams apps.

To set up avatars in Teams, you should:

1. [Allow endpoints](#allow-endpoints).
1. Manage user access to the Avatars app using one of the following options:
    1. [Use app centric management for Avatars in Teams](#use-app-centric-management-for-avatars-in-teams)
    1. [Manage Avatars in the Teams admin center](#manage-avatars-in-the-teams-admin-center)
    1. [Use service plans in the Microsoft 365 Admin Center to allow the Avatars app](#use-service-plans-in-the-microsoft-365-admin-center-to-allow-the-avatars-app)
1. (Optional) [Block Avatars app in the Teams Admin Center](#block-avatars-app-in-the-teams-admin-center)

> [!NOTE]
> Users currently need to manually install and pin the Avatars app. For more information, see [Use app setup policies to pin and auto-install apps for users](/microsoftteams/teams-app-setup-policies).

> [!NOTE]
> The Avatars for Teams app has minimum and recommended hardware requirements. For more information, see [Hardware requirements for Microsoft Teams](hardware-requirements-for-the-teams-app.md).
>
> Teams users can access this feature if they have one of the following licenses: Teams Essentials, Microsoft 365 Business Basic, Microsoft 365 Business Standard, Microsoft 365 Business Premium, Microsoft 365 E3/E5, and Office 365 E1/E3/E5.

## What is the Avatars app?

The Avatars for Microsoft Teams app lets your users connect with presence in Teams without having to turn on their cameras. Your users can represent themselves the way they want to show by choosing the avatar that fits their specific meeting. To learn more about using avatars in Microsoft Teams, see how to [Join a meeting as an avatar](https://support.microsoft.com/office/5384e7b7-30c7-4bcb-8065-0c9e830cc8ad).

## Allow endpoints

To ensure the avatars for Teams app works properly, access to the following endpoints must be allowed through your firewall or proxy server. All endpoints need to allow traffic on TCP ports 80 and 443.

- `*.microsoft.com`
- `*.office.com`
- `*.office.net`

If these endpoints aren't properly allowed, you will run into issues when running the Avatars for Teams app.

## Use app centric management for Avatars in Teams

> [!IMPORTANT]
> App centric management of Teams apps is a new feature. For more info on this rollout see [Use app centric management to manage apps | Microsoft Learn](app-centric-management.md).

## Manage Avatars in the Teams admin center

> [!NOTE]
> It may be more complicated if the tenant already has different app permission policies for users or groups.

### Allow the Avatars app

1. In the [Teams admin center](https://admin.teams.microsoft.com/policies/manage-apps), in the left-navigation bar, go to **Teams apps** > **Manage apps**.
1. In the **Search by name** text box, search for and select **Avatars** and then select **Allowed**.

  :::image type="content" source="media/avatars-allowed.png" alt-text="Toggle showing the Avatars app stateset to Allowed.":::

### Create or edit a setup policy to preinstall the Avatars app for users

1. In the [Teams admin center](https://admin.teams.microsoft.com/policies/manage-apps), go to **Teams apps** > **Setup policies**.
1. Select the policy you want to edit, such as **Global (Org-wide default)** or **Add** a policy. If you add a new policy, make sure to give it a descriptive name.
1. Under **Installed apps**, select **Add apps**.
1. Under **Search based on this app permission policy**, select **Global**.
1. Search for, and select, **Avatars**, and then select **Add**.
  :::image type="content" source="media/avatars-add-app.png" alt-text="Menu showing the Avatars app select from an app search box." lightbox="media/avatars-add-app-large.png":::
1. Confirm by selecting **Add** at the bottom.
1. Select **Save** to save the changes to your app setup policy.

If you created a new app setup policy, remember to assign it the users you want it to apply to. For more information, see [Ways to assign policies](policy-assignment-overview.md#ways-to-assign-policies).

### Enable user pinning or pin app for users

1. In the [Teams admin center](https://admin.teams.microsoft.com/policies/manage-apps), go to **Teams apps** > **Setup policies**.
1. Select the policy you want to edit, such as **Global (Org-wide default)**.
1. Set **User pinning** to **On**.
1. **[Optional]** In the **Setup** policy page, go to **Pinned apps**, and **Add** the avatars for Teams app.

Now users can see the Avatars app when they search through their apps, be able to pin it. If you add the avatars for Teams app to the **Pinned apps** list, the app will be pinned for users.

:::image type="content" source="media/avatars-app-pinning.png" alt-text="Setup policy showing the user pinning toggle set to On and the installed Avatar app." lightbox="media/avatars-app-pinning-large.png":::

### Block Avatars app in the Teams Admin Center

Blocking users is important when you don't want certain users to access the avatars for Teams app. You can also block users if there's a report of an inappropriate avatar that violates company policy and needs to be disabled.

If you want to block the avatars for Teams app available from a set of users, you need to add it to the app permissions policy assigned to those users.

### Create a policy to block the Avatars app for specific users

1. In the [Teams admin center](https://admin.teams.microsoft.com/policies/manage-apps), go to **Teams apps** > **Permission policies**.
1. In **App permissions policies**, select **Add**.
1. Provide a name and description for the policy.
1. Under **Microsoft apps**, select **Block specific apps and allow all others**, and then select **Block apps**.
1. Search for and select the **Avatars** app, then select **Block**.
1. Enter a policy name and description and then **Save.**

### Add users to policy to block them from the Avatars app

> [!IMPORTANT]
> Users need to restart their Teams client for new policies or policy updates to take effect.

1. In the left navigation of the Microsoft Teams admin center, go to the **Permission policy** page.
1. Select the policy you created and then select **Assign users** to assign this policy to the users you want to block.
1. In the **Manage users** pane, search for the user using their display name or username.
1. Select the user you want to block and then select **Add**.
1. Repeat steps 2 and 3 for each user that you want to block.
1. When you're finished adding users that you want to block, select **Apply**.

### Manage avatars for user profiles in the Teams Admin Center

Global or User admins can view, export, or remove a user's avatar profile from within the Teams Admin Center. This is useful if an incident of an offensive avatar is reported and needs to be removed or investigated for further action.

1. Select **Manage users** in the left nav.
1. Search for and select a user.
1. At the bottom of their user profile, you'll see their avatar(s).
1. Select **Export profiles** to generate a JSON file of the user's avatar configurations (up-to three).
1. Select **Remove profile** for a specific avatar profile you wish to remove entirely. The avatar profile you removed won't be visible to the user.

## Use service plans in the Microsoft 365 Admin Center to allow the Avatars app

1. Sign into [Microsoft 365 Admin Center](https://admin.microsoft.com/) with an admin account with at least Global, License, or User level permissions and open the left navigation panel to the Users section.

1. Select the user or user group and go to **Licenses and apps** to manage the active licenses and service plans.

1. Ensure that you enabled the appropriate licenses for Avatars for Teams.

For more guidance for assigning licenses in Microsoft 365, see:

[Assign or unassign licenses for users in the Microsoft 365 admin center - Microsoft 365 admin | Microsoft Learn](/microsoft-365/admin/manage/assign-licenses-to-users).

For more complex and larger group license management, you can do [Assign licenses to a group - Microsoft Entra ID | Microsoft Learn](/entra/identity/users/licensing-groups-assign).

## Where avatars can be used

Avatars for Teams can be used in any Teams meeting that includes the option to use a real-world camera.

Guests invited to meetings can only to use avatars for Teams if the app is enabled on their tenant for their account.

If you're invited to a meeting outside your tenant, you'll be able to use avatars for Teams if enabled on your tenant for your account.

To learn how to use avatars in Teams, see [Join a meeting as an avatar in Microsoft Teams](https://support.microsoft.com/office/5384e7b7-30c7-4bcb-8065-0c9e830cc8ad).
