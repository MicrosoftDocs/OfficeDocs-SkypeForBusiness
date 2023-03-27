---
title: Set up avatars for Microsoft Teams 
ms.author: dstrome
author: dstrome
manager: serdars
audience: ITPro
ms.reviewer: sekerawa
ms.date: 03/18/2023
ms.topic: quickstart
ms.service: msteams
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.collection: 
  - Tier2
  - M365-collaboration
description: Learn how to set up the avatars for Microsoft Teams app.
---

# Set up avatars for Microsoft Teams

Avatars for Microsoft Teams lets your users connect with presence in Teams without having to turn on their cameras. Your users can represent themselves the way they want to show by choosing the avatar that fits their specific meeting. You can control whether avatars for Teams is available in your organization and who can use them using policies.

Setup and permissions policies allow or block the avatar for Teams app in your organization. Policies control whether an app is available to users, automatically pinned in their Teams client, or blocked from use. By default, the **Global (Org-wide default)** policy is applied to all users in your organization. However, you can create more policies for subsets of your users, such as executives, sales, manufacturing, and so on.

Setting up the avatars for Teams app involves the following steps:

1. [Allow the avatars for Teams app in your organization](#allow-the-avatars-for-teams-app-in-your-organization).
1. [Ensure essential URLs are allowed](#ensure-essential-urls-are-allowed).
1. (Optional) [Block the avatars for Teams app for specific users or groups](#block-the-avatars-for-teams-app-for-specific-users-or-groups).

After you complete these steps, the avatars for Teams app will be available to users in your organization.

## Allow the avatars for Teams app in your organization

If you want to make the avatar for Teams app available to a set of users, you need to add it to the app setup policy assigned to those users.

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

Now users will see the avatars for Teams app when they search through their apps, be able to pin it. If you add the avatar for Teams app to the **Pinned apps** list, the app will automatically be pinned for users.

:::image type="content" source="media/avatars-app-pinning.png" alt-text="Setup policy showing the user pinning toggle set to On and the installed Avatar app." lightbox="media/avatars-app-pinning-large.png":::

## Ensure essential URLs are allowed

To ensure the avatars for Teams app works properly, TCP ports 443 and 80 need to be allowed through your firewall or proxy server for the following URLs:

- `https://clients.config.office.net/user/v1.0/web/policies`
- `https://browser.events.data.microsoft.com/OneCollector/1.0/`
- `https://global.profile.prod.collab.mixedreality.microsoft.com/ms-graph-obo/accesstoken`
- `https://js.monitor.azure.com/scripts/c/ms.analytics-web-3.js`
- `global.profile.prod.collab.mixedreality.microsoft.com`
- `clients.config.office.net`
- `catalog.meshxp.net`
- `browser.events.data.microsoft.com`
- `avatars.meshxp.net`

TCP port 80 is required to allow requests to automatically redirect to TCP port 443.

## Block the avatars for Teams app for specific users or groups

Blocking users is important when you don't want certain users to access the avatars for Teams app. You can also block users if there's a report of an inappropriate avatar that violates company policy and needs to be disabled.

If you want to block the avatar for Teams app available from a set of users, you need to add it to the app permissions policy assigned to those users.

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
