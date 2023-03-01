---
title: Collaboration activity reports in Microsoft Teams
ms.author: v-smandalika
author: v-smandalika
manager: dansimp
ms.reviewer: roykuntz; jens
ms.date: 02/24/2023
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-voice
f1.keywords:
- CSH
ms.custom: ms.teamsadmincenter.voice.callinglineid.overview
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about the Collaboration activity reports in Microsoft Teams.
---

# Collaboration activity reports in Microsoft Teams

The Collaboration activity reports is a feature in Microsoft Teams that has the following objectives:

- Giving Teams administrators the visibility into their organization’s external collaboration habits, such that they can facilitate successful collaboration and mitigate potential risks that come with allowing external collaboration.
- Enabling Teams administrators automate their work

Collaboration activity reports in Microsoft Teams includes insights regarding teams, domains, channels, external users, guest users, and users internal to your organization.

## Where to find Collaboration activity reports

The Collaboration activity reports feature is found in Teams Admin Center dashboard under the **Collaboration activity** tab, described as follows.

:::image type="content" source="media/dashboard-collaboration-activity-reports.png" alt-text="The dashboard displaying the Collaboration activity reports menu item.":::

### Insight descriptions

The components of Collaboration activity reports are:

- [Inactive teams](#inactive-teams)
- [External domain activity](#external-domain-activity)
- [Teams by user type](#teams-by-user-type)
- [Channels by user type](#channels-by-user-type)
- [External collaboration activity by team](#external-collaboration-activity-by-team)
- [External collaboration activity by user](#external-collaboration-activity-by-user)
- [Guest user activity](#guest-user-activity)

#### Inactive teams

The widget view of inactive teams displays how many teams in your organization have been inactive for the past 30 days and 60 days. You can hover over each date to see the exact counts for that day.

:::image type="content" source="media/inactive-teams.png" alt-text="The screen displaying details of teams that are inactive.":::

You can click **View details** to see which are the teams that have been inactive for 30 days and 60 days. For each team, you can see the privacy type, number of channels in the team, and number of users in the team. You can also archive the team directly from this view. You can change the time frame by selecting the dropdown list under **Date range** and clicking **Run report**.

:::image type="content" source="media/detailed-report-view.png" alt-text="The detailed report of teams that are inactive.":::

#### External domain activity

The widget view of inactive domains displays the total number of allowed domains; how many of your allowed domains have been inactive in the past 7 days, 30 days, and 60 days; and how many of your allowed domains have been active in the past 7 days, 30 days, and 60 days. You can hover over each date to see the exact counts for that day.

:::image type="content" source="media/external-domains-activity.png" alt-text="The report displaying the total number of allowed domains.":::

You can click **View details** to see which of your allowed domains have been inactive for the past 7 days, 30 days, and 60 days. You can archive domain names and the Last Activity Date for each. You can change the time frame by selecting the dropdown list under **Date range** and clicking **Run report**.

This insight will only surface for organizations that don't have open federation enabled.

:::image type="content" source="media/detailed-report-view-external-domains-activity.png" alt-text="The detailed report view regarding the external domains activity.":::

#### Teams by user type

The **Teams by user type** widget shows you how many of your [ACTIVE] teams are comprised of your users only; how many of your teams are comprised of your users and guests; how many of your teams are comprised of your users and external users; and how many of your teams include all user types. 

> [!NOTE]
> Only active teams are included in the breakdown. To change the period for which you want to view the active teams count, use the duration selector that contains the options of **7 days** and **30 days**.

This insight doesn't tell you how many users are in a team; it shows how many teams have each composition type. For example, a team with 100 of your users, no external users, and one guest will count as one team comprised of “my users and guests.”

:::image type="content" source="media/teams-by-user-type.png" alt-text="The Teams by user type widget.":::

#### Channels by user type

The **Channels by user type** widget tells you how many standard, private, and shared channels in your organization are comprised of your users (internal to your organization) only, your users and guests, and your users and external users.

> [!NOTE]
> Only active channels are included in the breakdown. To change the period for which you want to view the active channels count, use the duration selector that contains the options of **7 days** and **30 days**.

External users can only be in shared channels, and guests can only be in standard and private channels. As a result, you'll only see two counts per type of channel. For example, for standard and private channels, you’ll see how many are made up of your users only how many are made up of your users and guests. For shared channels, you’ll see how many are made up of your users only and how many are made up of your users and external users.

:::image type="content" source="media/channels-by-user-type.png" alt-text="The Channels by user type widget.":::

#### External collaboration activity by team

The **External collaboration activity by team** widget shows you which teams in your organization have the most collaboration with guests and external users.

:::image type="content" source="media/external-collaboration-activity-by-team.png" alt-text="The External collaboration activity by team widget.":::

You can click **View details** to see the teams’ names and the sent message count for each team. An average message count will also be displayed.

:::image type="content" source="media/external-collaboration-activity-by-team-detailed-report.png" alt-text="The detailed report - External collaboration activity by team.":::

#### External collaboration activity by user

The **External collaboration activity by user** widget shows you which of the users internal to your organization have the most collaboration with guests and external users.

:::image type="content" source="media/external-collaboration-activity-by-user.png" alt-text="The External collaboration activity by user widget.":::

You can click **View details** to see the users’ names and the sent message count for each user. An average message count will also be displayed.

:::image type="content" source="media/external-collaboration-activity-by-user-detailed-report.png" alt-text="The detailed report - External collaboration activity by user.":::

#### Guest user activity

The **Guest user activity** widget shows you which of your guests have the most collaboration with users who are internal to your organization.

:::image type="content" source="media/guest-user-activity.png" alt-text="The Guest user activity widget.":::

You can click **View details** to see the guest’s names and the sent message count for each guest. An average message count will also be displayed.

:::image type="content" source="media/guest-user-activity-detailed-report.png" alt-text="The detailed report - Guest user activity.":::

### Notes

1. All reports only show users and teams owned by your tenant but the counts could include activities in cross-tenant collaborations.
    1. For channel events, only the channel’s owning tenant knows about the event. Therefore, if your tenant’s user is participating in channels owned by other tenants, these events won't accrue to any of the reports in your tenant.
    1. For chat (1:1, group, meeting) events, all participating tenants know about the events. So, your tenant’s report knows events initiated not only by users in your tenant but also by others in other tenants.
    1. These are to uphold Microsoft’s promise on privacy and compliance.
2. These reports honor Microsoft 365 level “admin report setting” about concealing or displaying team/user details. For more information, see [Show user details in the reports](/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide&preserve-view=true). When a global administrator configures “conceal team/user details”, reports show obfuscated user/team names instead of their display names.

### Known Issues

1. On time-series charts, last day’s data may be empty. For example, on 2/17, time-series chart doesn’t have data for 2/17; so, the lines stop at 2/16.
1. Widget location customizations on dashboard have yet been persisted across sessions.
1. Csv download hasn’t been enabled.
1. Very large events may have a small chance of data categorization error. For example, a very large team with very few guest users may not be categorized as “with guest users”. We're making improvements to address this issue.



