---
title: Manage the Praise app in the Teams admin center
author: mkbond007
ms.author: mabond
manager: serdars
ms.reviewer: rjam
audience: admin 
ms.topic: article 
ms.service: msteams
ms.localizationpriority: high 
description: Learn how to manage the Praise app in the Microsoft Teams admin center.

---

# Manage the Praise app in the Microsoft Teams admin center

The Praise app in Microsoft Teams helps users show appreciation to members of your organization or classroom. The badges in Praise are designed to help recognize the effort that goes into the wide range of work that Teams users do, from educators to frontline workers. To learn more, check out [Send Praise to people](https://support.microsoft.com/office/send-praise-to-people-50f26b47-565f-40fe-8642-5ca2a5ed261e).

Admins must have a Teams license to access this feature. If you try to access this feature without a Teams license, you'll get an error message.

> [!NOTE]
> The Praise app is available for GCC cloud environment, but not for GCC High or DoD.

## Enable or disable Praise in your organization

Praise is enabled by default for all Teams users in your organization. You can turn off or turn on the app at the org level on the [Manage apps](manage-apps.md) page in the Microsoft Teams admin center.

:::image type="content" source="media/manage-praise-app-admin-center.png" alt-text="Screenshot of the Praise app details page in the Teams admin center, showing the Status toggle.":::

1. In the left pane of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps**.
2. In the list of apps, search for the Praise app, select it, and then switch the **Status** toggle to **Blocked** or **Allowed**.

Keep in mind that this setting affects both the Praise app and the Praise feature in the Viva Insights app in Teams.

If you set the Status to Blocked, the Praise app is blocked within a few minutes for Teams. However, praise in Viva Insights can take 7-9 days to be blocked.

## Enable or disable Praise for specific users in your organization

To allow or block specific users in your organization from using Praise, make sure Praise is turned on for your organization on the [Manage apps](manage-apps.md) page. Then create a custom app permission policy and assign it to those users. To learn more, see [Manage app permission policies in Teams](teams-app-permission-policies.md).

## Badges

Here's the default set of badges in Praise. Teams users in your organization can use these badges to recognize their peers for going above and beyond with their work.

:::image type="content" source="media/default-set-praise.png" alt-text="Image of badges in the default badge set.":::

> [!NOTE]
> Starting February 2022, people can only send and receive default badges. Custom badges are no longer available and options for custom badges have been removed from the Teams admin center.

## Related articles

[Manage your apps in the Microsoft Teams admin center](manage-apps.md)
