---
title: Advanced collaboration analytics for Microsoft Teams
ms.author: jtremper
author: jacktremper
manager: pamgreen
ms.reviewer: izzychun, charup
ms.date: 11/10/2023
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
f1.keywords:
- NOCSH
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

Reports only show users and teams owned by your organization, but the counts could include activities in cross-tenant collaborations. Reports include chat events (1:1, group, and meeting) initiated by your users and by people outside your organization. Reports include channel events from Teams channels in your organization, but not channel events that your users participate in that are hosted by other organizations.

Advanced collaboration analytics requires a Teams Premium license for each user you want to receive insights about. Note that it takes 30 days after licenses are purchased for the data to be available. 

## View the collaboration activity dashboard

Advanced collaboration analytics can be found in the Teams admin center dashboard on the **Collaboration activity** tab.

:::image type="content" source="media/collaborative-activity-dashboard.png" alt-text="Screenshot that shows the Collaboration activity reports menu item." lightbox="media/collaborative-activity-dashboard.png":::

## Inactive teams

The **Inactive teams** card shows inactive teams whose connected workloads are also inactive. It shows you how many teams in your organization have been inactive for the last 30 or 60 days. You can hover over each bar to see the exact counts for the specific day.

Note that you can set inactive teams to expire automatically by using [expiration policies for Microsoft 365 groups](/microsoft-365/solutions/microsoft-365-groups-expiration-policy). You can also [archive or delete a team in the Teams admin center](archive-or-delete-a-team.md).

:::image type="content" source="media/inactive-teams.png" alt-text="Screenshot that shows details of teams that are inactive.":::

Select **View details** to see which teams these are. For each team, you can see the privacy type, number of channels, number of users, and the last activity date.

:::image type="content" source="media/detailed-report-view.png" alt-text="Screenshot that shows the detailed report of teams that are inactive." lightbox="media/detailed-report-view.png":::

To change the time frame, select the range of date from the **Date range** drop-down, and select **Run report**.

You can also archive the team directly from the report. However, archiving a team has no impact on the connected workloads. Only the team itself will become read-only.

To archive an inactive team, under the **Action** column, select the **bin** icon. In the *Archive team?* dialog box, select **Archive**.

> [!NOTE]
> SharePoint Administrators with a [Microsoft Syntex - SharePoint Advanced Management](/sharepoint/advanced-management) license can use [site lifecycle policies](/sharepoint/site-lifecycle-management) in the SharePoint admin center to detect inactive sites, including team-connected sites.

## Inactive external domains activity

The **Inactive external domains activity** card shows how many domains are allowed and how many of your allowed domains have been active and inactive for the last 30 or 60 days. You can hover over each part of the pie chart to see exact counts.

This card is only available if you've configured an allowlist in [external access](trusted-organizations-external-meetings-chat.md).

:::image type="content" source="media/inactive-external-domains.png" alt-text="Screenshot that shows the total number of allowed domains.":::

Select **View details** to see which domains are inactive, including the last activity date. A value for **Last activity date (UTC)** is displayed only if domain activity has taken place after the purchase of Teams Premium.

You can change the time frame by choosing a date range from the **Date range** dropdown and selecting **Run report**.

:::image type="content" source="media/detailed-report-view-inactive-external-domains.png" alt-text="Screenshot that shows the detailed report view regarding the external domains activity.":::

## Teams by user type

The **Teams by user type** card shows how many active teams have a particular user composition:

- Your users only
- Your users and guests
- Your users and external shared channel users
- All user types

:::image type="content" source="media/teams-by-user-type.png" alt-text="Screenshot that shows the Teams by user type card.":::

## Channels by user type

The **Channels by user type** card shows you how many active channels have a particular user composition:

Standard and private channels
- Only your users
- Your users and guests

Shared channels
- Only your users
- Your users and external channel participants

:::image type="content" source="media/channels-by-user-type.png" alt-text="Screenshot showing the Channels by user type card.":::

## Teams with the most external user and guest activity

The **Teams with the most external user and guest activity** card shows you which teams in your organization have the most collaboration with guests and external shared channel users for the last 7 or 30 days.

You can select **View details** to see the team names and the sent message count for each team. An average message count is also displayed.

By default, we show you these details for the last 7 days. You can change the time frame by choosing **30 days** or **60 days** from the **Date range** drop-down and selecting **Run report**.

Note that for privacy reasons the data is hidden by default in this card. To reveal the data, see [Show user details in the reports](/microsoft-365/admin/activity-reports/activity-reports#show-user-details-in-the-reports).

## Users with the most external user and guest collaboration

The **Users with the most external user and guest collaboration** card shows you which of your users have the most collaboration with guests and external userss for the last 7 or 30 days.

You can select **View details** to see the users' names and the sent message count for each user. An average message count is also displayed.

By default, we show you these details for the last 7 days. You can change the time frame by choosing **30 days** or **60 days** from the **Date range** drop-down list and selecting **Run report**.

Note that for privacy reasons the data is hidden by default in this card. To reveal the data, see [Show user details in the reports](/microsoft-365/admin/activity-reports/activity-reports#show-user-details-in-the-reports).

## Guests with the most external user and guest collaboration

The **Guest with the most external user and guest collaboration** card shows you which guests have the most collaboration with other guests or external users over the last 7 or 30 days.

Note that for privacy reasons the data is hidden by default in this card. To reveal the data, see [Show user details in the reports](/microsoft-365/admin/activity-reports/activity-reports#show-user-details-in-the-reports).

## Known issues

1. Card location customizations on dashboard aren't saved across sessions.
1. CSV download hasn't been enabled.
1. Large events have a small chance of data categorization error. For example, a large team with few guests might not be categorized as "with guest users."

## Related articles

[Microsoft Teams analytics and reporting](/microsoftteams/teams-analytics-and-reports/teams-reporting-reference)
