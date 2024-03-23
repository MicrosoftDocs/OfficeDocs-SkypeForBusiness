---
title: Set up avatars for Microsoft Teams 
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
audience: ITPro
ms.reviewer: sekerawa
ms.date: 06/26/2023
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

# Set up avatars for Microsoft Teams

Avatars for Microsoft Teams lets your users connect with presence in Teams without having to turn on their cameras. Your users can represent themselves the way they want to show by choosing the avatar that fits their specific meeting. To learn more about avatars in Microsoft Teams, see how to [Join a meeting as an avatar](https://support.microsoft.com/office/5384e7b7-30c7-4bcb-8065-0c9e830cc8ad).
> [!NOTE]
> The Avatars for Teams app has minimum and recommended hardware requirements. For more information, see [Hardware requirements for Microsoft Teams](hardware-requirements-for-the-teams-app.md).
>
> Teams users can access this feature if they have one of the following licenses: Teams Essentials, Microsoft 365 Business Basic, Microsoft 365 Business Standard, Microsoft 365 Business Premium, Microsoft 365 E3/E5, and Office 365 E1/E3/E5.

As an admin, you can control whether Avatars for Teams is available in your organization and who can use them using policies. Setup and permissions policies allow or block the avatars for Teams app in your organization. Policies control whether an app is available to users, automatically pinned in their Teams client, or blocked from use. By default, the **Global (Org-wide default)** policy is applied to all users in your organization. However, you can create more policies for subsets of your users, such as executives, sales, manufacturing, and so on.

Setting up the avatars for Teams app involves the following steps:

1. [Allow the avatars for Teams app in your organization](#allow-the-avatars-for-teams-app-in-your-organization).
1. [Ensure endpoints are allowed](#allow-endpoints).
1. (Optional) [Block the avatars for Teams app for specific users or groups](#block-the-avatars-for-teams-app-for-specific-users-or-groups).

After you complete these steps, the avatars for Teams app will be available to users in your organization.

> [!NOTE]
>Users currently need to manually install and pin the avatars for Teams app. For more information, see [Use app setup policies to pin and auto-install apps for users](/microsoftteams/teams-app-setup-policies).

## Allow the avatars for Teams app in your organization

If you want to make the avatars for Teams app available to a set of users, you need to add it to the app setup policy assigned to those users.

### Allow the avatars for Teams app

1. In the Teams admin center, in the left-navigation bar, go to **Teams apps** > **Manage apps**.
1. In the **Search by name** text box, search for and select **Avatars** and then select **Allowed**.
  :::image type="content" source="media/avatars-allowed.png" alt-text="Toggle showing the Avatars app state set to Allowed.":::

### Create or edit a setup policy to pre-install the avatars for Teams app for users

1. In the Teams admin center, go to **Teams apps** > **Setup policies**.
1. Select the policy you want to edit, such as **Global (Org-wide default)** or **Add** a policy. If you add a new policy, make sure to give it a descriptive name.
1. Under **Installed apps**, select **Add apps**.
1. Under **Search based on this app permission policy**, select **Global**.
1. Search for, and select, **Avatars**, and then select **Add**.
  :::image type="content" source="media/avatars-add-app.png" alt-text="Menu showing the Avatars app select from an app search box." lightbox="media/avatars-add-app-large.png":::
1. Confirm by selecting **Add** at the bottom.
1. Select **Save** to save the changes to your app setup policy.

If you created a new app setup policy, remember to assign it the users you want it to apply to. For more information, see [Ways to assign policies](policy-assignment-overview.md#ways-to-assign-policies).

### Enable user pinning or pin app for users

1. In the Teams admin center, go to **Teams apps** > **Setup policies**.
1. Select the policy you want to edit, such as **Global (Org-wide default)**.
1. Set **User pinning** to **On**.
1. **[Optional]** In the **Setup** policy page, go to **Pinned apps**, and **Add** the avatars for Teams app.

Now users will see the avatars for Teams app when they search through their apps, be able to pin it. If you add the avatars for Teams app to the **Pinned apps** list, the app will automatically be pinned for users.

:::image type="content" source="media/avatars-app-pinning.png" alt-text="Setup policy showing the user pinning toggle set to On and the installed Avatar app." lightbox="media/avatars-app-pinning-large.png":::

## Allow endpoints

To ensure the avatars for Teams app works properly, access to the following endpoints must be allowed by your firewall or proxy server. All endpoints need to allow traffic on TCP ports 80 and 443.

- `*.microsoft.com`
- `*.office.com`
- `*.office.net`

If these endpoints aren't properly allowed, you may run into issues when running the avatars for Teams app. 

## Block the avatars for Teams app for specific users or groups

Blocking users is important when you don't want certain users to access the avatars for Teams app. You can also block users if there's a report of an inappropriate avatar that violates company policy and needs to be disabled.

If you want to block the avatars for Teams app available from a set of users, you need to add it to the app permissions policy assigned to those users.

### Create a policy to block the avatars for Teams app for specific users

1. In the left panel, go to **Teams apps** > **Permission policies**.
1. In **App permissions policies**, select **Add**.
1. Provide a name and description for the policy.
1. Under **Microsoft apps**, select **Block specific apps and allow all others**, and then select **Block apps**.
1. Search for and select the **Avatars** app, then select **Block**.
1. Enter a policy name and description and then **Save.**

### Add users to policy to block them from the Avatars app

In the left navigation of the Microsoft Teams admin center, go to the **Permission policy** page.

> [!IMPORTANT]
> Users need to restart their Teams client for new policies or policy updates to take effect.

1. Select the policy you created and then select **Assign users** to assign this policy to the users you want to block.
1. In the **Manage users** pane, search for the user using their display name or username.
1. Select the user you want to block and then select **Add**.
1. Repeat steps 2 and 3 for each user that you want to block.
1. When you're finished adding users that you want to block, select **Apply**.

## Manage avatars for user profiles

Global or User admins can view, export, or remove a user's avatar profile from within the Teams Admin Center. This is useful if an incident of an offensive avatar is reported and needs to be removed or investigated for further action. 
1. Select **Manage users** in the left nav.
1. Search for and select a user.
1. At the bottom of their user profile, you will see their avatar(s).
1. Select **Export profiles** to generate a JSON file of the user's avatar configurations (up-to three).
1. Select **Remove profile** for a specific avatar profile you wish to remove entirely. The avatar profile you removed will not be visible to the user.

## Where avatars can be used

Avatars for Teams can be used in any Teams meeting that includes the option to use a real-world camera.

Guests invited to meetings will only be able to use avatars for Teams if the app is enabled on their tenant for their account.

If you are invited to a meeting outside your tenant, you will be able to use avatars for Teams if it's enabled on your tenant for your account.

To learn how to use avatars in Teams, see [Join a meeting as an avatar in Microsoft Teams](https://support.microsoft.com/office/5384e7b7-30c7-4bcb-8065-0c9e830cc8ad).
