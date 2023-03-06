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
ms.custom: seo-marvel-mar2020
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about the Collaboration activity reports in Microsoft Teams.
---

# Collaboration activity reports in Microsoft Teams

The Collaboration activity reports in Microsoft Teams has the following objectives:

- Giving Teams administrators the visibility into their organization’s external collaboration habits, such that they can facilitate successful collaboration and mitigate potential risks that come with allowing external collaboration.
- Enabling Teams administrators automate their work.

With the help of Collaboration activity reports, you can get an insight into teams, domains, channels, external users, guest users, and users internal to your organization.

## Where to find Collaboration activity reports

The Collaboration activity reports can be found in the Teams Admin Center dashboard under the **Collaboration activity** tab, as depicted in the following screenshot:

:::image type="content" source="media/dashboard-collaboration-activity-reports.png" alt-text="The dashboard displaying the Collaboration activity reports menu item.":::

### Insight descriptions

This section describes the following insights provided by Collaboration activity reports:

- [Inactive teams](#inactive-teams)
- [External domains activity](#external-domains-activity)
- [Teams by user type](#teams-by-user-type)
- [Channels by user type](#channels-by-user-type)
- [External collaboration activity by team](#external-collaboration-activity-by-team)
- [External collaboration activity by user](#external-collaboration-activity-by-user)
- [Guest user activity](#guest-user-activity)

#### Inactive teams

The **Inactive teams** widget view displays how many teams in your organization have been inactive for the past 30 and 60 days. You can hover over each date in the time frame (30 days or 60 days) to see the exact count for that day.

:::image type="content" source="media/inactive-teams.png" alt-text="The screen displaying details of teams that are inactive.":::

You can click **View details** to see which are the teams that have been inactive for both the time frames, namely "past 30 days" and "past 60 days". For each team, you can see the privacy type, number of channels in the team, and number of users in the team. You can directly archive the details of any team for any time frame by selecting the dropdown list under **Date range** and choosing the time period you want, and by clicking **Run report**.

:::image type="content" source="media/detailed-report-view.png" alt-text="The detailed report of teams that are inactive.":::

#### External domains activity

The **External domains activity** widget view displays the total number of allowed domains; and how many of your allowed domains have been inactive and active for the time frames of "past 7 days", "past 30 days", and "past 60 days".

:::image type="content" source="media/external-domains-activity.png" alt-text="The report displaying the total number of allowed domains.":::

You can click **View details** to see which of your allowed domains have been inactive/active for the following time frames:
- Past 7 days
- Past 30 days
- Past 60 days

You can archive the detail of any domain's inactive and active teams for any 7-day, 30-day, or 60-day period by:
- Selecting the dropdown list under **Date range**
- Choosing the time period you want, and then click **Run report**

You also can archive names of inactive/active domains and the Last Activity Date for each domain.

This insight will only surface for organizations that don't have open federation enabled.

:::image type="content" source="media/detailed-report-view-external-domains-activity.png" alt-text="The detailed report view regarding the external domains activity.":::

#### Teams by user type

The **Teams by user type** widget view shows you how many of your "active" teams comprise:
- Your users only
- Your users and guests
- Your users and external users
- All user types

> [!NOTE]
> Only active teams are included in the breakdown. 

You can view the count of active teams by using the duration selector that contains the options of **7 days** and **30 days**.

You can also view the composition types for any of the active teams.

This insight doesn't tell you how many users are in a team; it shows how many teams have each composition type. For example, a team with 100 of your users, no external users, and one guest will count as one team comprised of “my users and guests.”

:::image type="content" source="media/teams-by-user-type.png" alt-text="The Teams by user type widget.":::

#### Channels by user type

The **Channels by user type** widget view tells you how many standard, private, and shared channels in your organization comprise:
- Your users (internal to your organization) only
- Your users and guests
- Your users and external users

> [!NOTE]
> To change the time frame for which you want to view the count of active channels (standard, private, or shared) and their user composition, use the duration selector that contains the options of **7 days** and **30 days**.

External users can only be in shared channels, and guests can only be in standard and private channels. As a result, you'll only see two counts per type of channel. 

For example, for standard and private channels, you’ll see:
- How many are made up of your users only
- How many are made up of your users and guests

For shared channels, you’ll see:
- How many are made up of your users only
- How many are made up of your users and external users

:::image type="content" source="media/channels-by-user-type.png" alt-text="The Channels by user type widget.":::

#### External collaboration activity by team

The **External collaboration activity by team** widget view shows you which teams in your organization have the most collaboration with guests and external users.

:::image type="content" source="media/external-collaboration-activity-by-team.png" alt-text="The External collaboration activity by team widget.":::

You can click **View details** to see the teams’ names and the "sent message count" for each team. An average message count will also be displayed.

:::image type="content" source="media/external-collaboration-activity-by-team-detailed-report.png" alt-text="The detailed report - External collaboration activity by team.":::

#### External collaboration activity by user

The **External collaboration activity by user** widget view shows you which of the users internal to your organization have the most collaboration with guests and external users.

:::image type="content" source="media/external-collaboration-activity-by-user.png" alt-text="The External collaboration activity by user widget.":::

You can click **View details** to see the users’ names and the "sent message count" for each user. An average message count will also be displayed.

:::image type="content" source="media/external-collaboration-activity-by-user-detailed-report.png" alt-text="The detailed report - External collaboration activity by user.":::

#### Guest user activity

The **Guest user activity** widget shows you which of your guests have the most collaboration with users who are internal to your organization.

:::image type="content" source="media/guest-user-activity.png" alt-text="The Guest user activity widget.":::

You can click **View details** to see the guest’s names and the "sent message count" for each guest. An average message count will also be displayed.

:::image type="content" source="media/guest-user-activity-detailed-report.png" alt-text="The detailed report - Guest user activity.":::

### Notes

1. All reports only show users and teams owned by your tenant, but the counts could include activities in cross-tenant collaborations.
    1. For channel events, only the channel’s owning tenant knows about the event. Therefore, if your tenant’s user is participating in channels owned by other tenants, these events won't accrue to any of the reports in your tenant.
    1. For chat (1:1, group, meeting) events, all participating tenants know about the events. So, your tenant’s report knows events initiated not only by users in your tenant but also by others in other tenants.
    1. These are to uphold Microsoft’s promise on privacy and compliance.
2. These reports honor Microsoft 365 level “admin report setting” about concealing or displaying team/user details. For more information, see [Show user details in the reports](/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide&preserve-view=true). When a global administrator configures “conceal team/user details”, reports show obfuscated user/team names instead of their display names.

### Known Issues

1. On time-series charts, last day’s data is empty. For example, on 2/17, time-series chart doesn’t have data for 2/17; so, the data of 2/16 is shown since the lines stop at 2/16.
1. Widget location customizations on dashboard have yet been persisted across sessions.
1. Csv download hasn’t been enabled.
1. Very large events may have a small chance of data categorization error. For example, a very large team with very few guest users may not be categorized as “with guest users”. We're making improvements to address this issue.



