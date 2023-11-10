---
title: Advanced collaboration analytics for Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.reviewer: izzychun
ms.date: 11/10/2023
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-voice
f1.keywords:
- CSH
ms.custom:
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about the collaboration activity reports in Microsoft Teams.
---

# Advanced collaboration analytics for Microsoft Teams

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

Advanced collaboration analytics gives you visibility into your organization’s external collaboration habits. These reports include information about your teams, trusted domains, channels, guests, and internal users. You can use this information to facilitate successful collaboration and mitigate potential risks that come with allowing external collaboration.

Advanced collaboration analytics requires Teams Premium.

## View the collaboration activity dashboard

Advanced collaboration analytics can be found in the Teams admin center dashboard on the **Collaboration activity** tab.

:::image type="content" source="media/collaborative-activity-dashboard.png" alt-text="Screenshot that shows the Collaboration activity reports menu item." lightbox="media/collaborative-activity-dashboard.png":::

## Inactive teams

The **Inactive teams** card shows inactive teams whose connected workloads are also inactive. It shows you how many teams in your organization have been inactive for the last 30 or 60 days. You can hover over each bar to see the exact counts for the specific day.

Note that you can set inactive teams to expire automatically by using [expiration policies for Microsoft 365 groups](/microsoft-365/solutions/microsoft-365-groups-expiration-policy).

:::image type="content" source="media/inactive-teams.png" alt-text="Screenshot that shows details of teams that are inactive." lightbox="media/inactive-teams.png":::

Select **View details** to see which teams these are. For each team, you can see the privacy type, number of channels, number of users, and the last activity date.

:::image type="content" source="media/detailed-report-view.png" alt-text="Screenshot that shows the detailed report of teams that are inactive." lightbox="media/detailed-report-view.png":::

To change the time frame, select the range of date from the **Date range** drop-down, and select **Run report**.

You can also archive the team directly from the report. However, archiving a team has no impact on the connected workloads. Only the team itself will become read-only.

To archive an inactive team, under the **Action** column, select the **bin** icon. In the *Archive team?* dialog box, select **Archive**. For more information about archiving teams, see [Archive or delete a team in Microsoft Teams](archive-or-delete-a-team.md).

> [!NOTE]
> SharePoint Administrators with a [Microsoft Syntex - SharePoint Advanced Management](/sharepoint/advanced-management) license can use [site lifecycle policies](/sharepoint/site-lifecycle-management) in the SharePoint admin center to detect inactive sites, including team-connected sites.

## Inactive external domains activity

The **Inactive external domains activity** card shows how many domains are allowed and how many of your allowed domains have been active and inactive for the last 30 or 60 days. You can hover over each part of the pie chart to see exact counts.

This card is only available if you've configured an allowlist in [external access](trusted-organizations-external-meetings-chat.md).

:::image type="content" source="media/inactive-external-domains.png" alt-text="Screenshot that shows the total number of allowed domains." lightbox="media/inactive-external-domains.png":::

Select **View details** to see which domains are inactive, including the last activity date. A value for **Last activity date (UTC)** is displayed only if domain activity has taken place after the purchase of Teams Premium.

You can change the time frame by choosing a date range from the **Date range** dropdown and selecting **Run report**.

:::image type="content" source="media/detailed-report-view-inactive-external-domains.png" alt-text="Screenshot that shows the detailed report view regarding the external domains activity." lightbox="media/detailed-report-view-inactive-external-domains.png":::

## Teams by user type

The **Teams by user type** card shows how many active teams have a particular user composition:

- Your users only
- Your users and guests
- Your users and external users
- All user types

:::image type="content" source="media/teams-by-user-type.png" alt-text="Screenshot that shows the Teams by user type card." lightbox="media/teams-by-user-type.png":::

## Channels by user type

The **Channels by user type** card shows you how many active channels have a particular user composition:

Standard and private channels
- Only your users
- Your users and guests

Shared channels
- Only your users
- Your users and external channel participants

:::image type="content" source="media/channels-by-user-type.png" alt-text="Screenshot showing the Channels by user type card." lightbox="media/channels-by-user-type.png":::

## Teams with the most external user and guest activity

The **Teams with the most external user and guest activity** card view shows you which teams in your organization have the most collaboration with guests and external users for the last 7 or 30 days.

> [!NOTE]
> The data is concealed by default in this card. To reveal the data, see [Remove data obfuscation](#remove-data-obfuscation).

You can select **View details** to see the teams’ names and the "sent message count" for each team. An average message count is also displayed. By default, we show you these details for the **last 7 days** time frame.

You can change the time frame by choosing **30 days** or **60 days** from the **Date range** drop-down list and selecting **Run report**.

## Users with the most external user and guest collaboration

The **Users with the most external user and guest collaboration** card view shows you which of the users internal to your organization have the most collaboration with guests and external users for the last 7 or 30 days.

> [!NOTE]
> The data is concealed by default in this card. To reveal the data, see [Remove data obfuscation](#remove-data-obfuscation).

You can select **View details** to see the users’ names and the "sent message count" for each user. An average message count is also displayed. By default, we show you these details for the **last 7 days** time frame.

You can change the time frame by choosing **30 days** or **60 days** from the **Date range** drop-down list and selecting **Run report**.

You can change the time frame by selecting the **30 days** option, which provides details of those internal users who have collaborated the most with guests and external users for the last 30 days.

## Guests with the most external user and guest collaboration

The **Guest with the most external user and guest collaboration** card shows you which of your guests have the most collaboration with users who are internal to your organization for the last 7 or 30 days.

> [!NOTE]
> The data is concealed by default in this card. To reveal the data, see [Remove data obfuscation](#remove-data-obfuscation).

> [!NOTE]
> This insight doesn't capture Guest<>In-tenant user activity, but only the Guest<>Guest and Guest<>External user activities. Guest<>External user activities occur in group chats but not in 1:1 chats.

By default, we show you the guest users who have engaged in external collaboration for the last 7 days.

You can change the time frame by selecting the **30 days** option, which provides details of those guests who have collaborated the most with guests and external users for the last 30 days.


#### Notes

1. All reports only show users and teams owned by your tenant, but the counts could include activities in cross-tenant collaborations.
    1. For channel events, only the channel’s owning tenant knows about the event. Therefore, if your tenant’s user is participating in channels owned by other tenants, these events don't accrue to any of the reports in your tenant.
    1. For chat (1:1, group, meeting) events, all participating tenants know about the events. So, your tenant’s report knows events initiated not only by users in your tenant but also by others in other tenants.
    1. These are to uphold Microsoft’s promise on privacy and compliance.
2. These reports honor Microsoft 365 level “admin report setting” about concealing or displaying team/user details. For more information, see [Show user details in the reports](/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide&preserve-view=true). When a global administrator configures “conceal team/user details”, reports show obfuscated user/team names instead of their display names.

#### Known issues

1. On the time-series charts, last day’s data is empty. For example, on 2/17, a time-series chart doesn’t have data for 2/17; so, the data of 2/16 is shown since the lines stop at 2/16.
1. card location customizations on dashboard are yet to be persisted across sessions.
1. Csv download hasn’t been enabled.
1. Large events may have a small chance of data categorization error. For example, a large team with few guest users may not be categorized as “with guest users”. We're making improvements to address this issue.

#### Remove data obfuscation

Three cards - External collaboration activity by team, External collaboration activity by user, and Guest user activity - use data obfuscation (in other words, concealing the data). To reveal the data, perform the following steps.

[Show user details in the reports](/microsoft-365/admin/activity-reports/activity-reports#show-user-details-in-the-reports)