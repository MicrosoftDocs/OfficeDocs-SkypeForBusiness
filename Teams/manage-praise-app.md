---
title: Manage the Praise app in the Teams admin center
author: Lana-Chin
ms.author: v-chinlana
manager: jtremper
ms.reviewer: rjam
ms.date: 04/01/2024
audience: admin
ms.topic: how-to
ms.service: msteams
ms.localizationpriority: medium
description: Learn how to manage the Praise app in the Microsoft Teams admin center.
ms.collection: 
  - M365-collaboration
  - m365-frontline
  - teams-1p-app-admin
  - highpri
---

# Manage the Praise app in the Microsoft Teams admin center

## Overview of Praise

The Praise app in Microsoft Teams helps users show appreciation to members of your organization or classroom. The badges in Praise are designed to help recognize the effort that goes into the wide range of work that Teams users do, from educators to frontline workers. To learn more, check out [Send Praise to people in Teams](https://support.microsoft.com/office/send-praise-to-people-50f26b47-565f-40fe-8642-5ca2a5ed261e).

Admins must have a Teams license to access this feature. If you try to access this feature without a Teams license, you'll get an error message.

> [!NOTE]
> The Praise app is available for GCC or GCC High cloud environments, but not for DoD.

## Enable or disable Praise in your organization

Praise is enabled by default for all Teams users in your organization. You can turn off or turn on the app at the org level on the [Manage apps](manage-apps.md) page in the Microsoft Teams admin center.

:::image type="content" source="media/manage-praise-app-admin-center.png" alt-text="Screenshot of the Praise app details page in the Teams admin center, showing the Status toggle.":::

1. In the left pane of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps**.
2. In the list of apps, search for the Praise app, select it, and then switch the **Status** toggle to **Blocked** or **Allowed**.

Keep in mind that this setting affects both the Praise app and the Praise feature in the Viva Insights app in Teams.

If you set the status to **Blocked**, the Praise app is blocked within a few minutes for Teams. However, Praise in Viva Insights can take up to 15 days to be blocked.

## Enable or disable Praise for specific users in your organization

To allow or block specific users in your organization from using Praise, make sure Praise is turned on for your organization on the [Manage apps](manage-apps.md) page. Then create a custom policy for app permissions and assign it to those users. To learn more, see [Use app permission policies to control user access to apps](teams-app-permission-policies.md).

## Composer

Teams users in your organization can use the praise composer to recognize their peers for going above and beyond with their work. While crafting their message, they can pick from 14 titles&mdash;like **Courage**, **Optimism**, **Kind heart**, and **Creative**&mdash;to recognize their colleagues’ contributions.

:::image type="content" source="media/praise.png" alt-text="Screenshot of the praise composer.":::

## User data in Praise

Praise uses Viva Insights to process and store data. See the [Personal insights FAQ](/viva/insights/personal/overview/mya-faq) to learn more about how Viva Insights processes and stores user data.

## Give feedback or report an issue

To send feedback or report an issue, select **Settings and more** (**…**) in Teams, and then choose **Help** > **Give feedback**. Enter your feedback or details about the issue you're experiencing. Indicate at the beginning of your feedback report that you're sending feedback about Praise so we can easily identify Praise issues.

## Related articles

[Overview of app management and governance in Teams admin center](manage-apps.md)