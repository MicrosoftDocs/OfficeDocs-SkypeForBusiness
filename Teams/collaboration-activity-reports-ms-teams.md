---
title: Collaboration activity feature in Microsoft Teams
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
ms.custom:
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about the Collaboration activity feature in Microsoft Teams.
---

# Collaboration activity feature in Microsoft Teams

> [!IMPORTANT]
> Advanced Collaboration Management Insights Private Preview is provided for evaluation purposes only and may not include all expected functionality.  Data provided during preview will be deleted within 180 days from a tenant deletion action.

The Collaboration activity feature in Microsoft Teams has the following objectives:

- Give Teams administrators visibility into their organization’s external collaboration habits, such that they can facilitate successful collaboration and mitigate potential risks that come with allowing external collaboration.
- Enable Teams administrators to automate their work.
  > [!NOTE]
  > This objective is currently not yet functional; we aim to make this objective functional in the future sprints.

With the help of Collaboration activity feature, you can get an insight into teams, domains, channels, external users, guest users, and users internal to your organization.

## Where to find Collaboration activity feature

The Collaboration activity feature can be found in the Teams Admin Center dashboard under the **Collaboration activity** tab, as depicted in the following screenshot:

:::image type="content" source="media/dashboard-collaboration-activity-feature.png" alt-text="The dashboard displaying the Collaboration activity feature menu item." lightbox="media/dashboard-collaboration-activity-feature.png":::

### Components

This section describes the following components of the Collaboration activity feature:

- [Inactive teams](#inactive-teams)
- [External domains activity](#external-domains-activity)
- [Teams by user type](#teams-by-user-type)
- [Channels by user type](#channels-by-user-type)
- [External collaboration activity by team](#external-collaboration-activity-by-team)
- [External collaboration activity by user](#external-collaboration-activity-by-user)
- [Guest user activity](#guest-user-activity)

#### Inactive teams

The **Inactive teams** widget view displays how many teams in your organization have been inactive for the past 30 and 60 days. You can hover over each date in either of the time frames (30 days or 60 days, whichever you've chosen) to see the exact count for that day.

:::image type="content" source="media/inactive-teams.png" alt-text="The screen displaying details of teams that are inactive." lightbox="media/inactive-teams.png":::

You can click **View details** to see which are the teams that have been inactive for both the time frames, namely "past 30 days" and "past 60 days". For each team, you can see the privacy type, number of channels in the team, and number of users in the team. You can archive these details for any inactive team of any time frame. That is, you can select a time frame of choice from the **Date range** dropdown list, and then from the list of inactive teams for that period, you can select any team and click **Run report**.

:::image type="content" source="media/detailed-report-view.png" alt-text="The detailed report of teams that are inactive." lightbox="media/detailed-report-view.png":::

#### External domains activity

The **External domains activity** widget view displays the total number of allowed domains; and how many of your allowed domains have been inactive and active for the time frames of "past 30 days" and "past 60 days". You can hover over to see the exact count of active and inactive domains for the chosen time frame.

:::image type="content" source="media/external-domains-activity.png" alt-text="The report displaying the total number of allowed domains." lightbox="media/external-domains-activity.png":::

You can click **View details** to view the names of your allowed domains that have been inactive for the past 30 days and 60 days, and the last activity date of these domains.

You can choose the specific date range for which you want to view the details such as names of the inactive domains and the last activity date for each of these domains. To do this task, choose a date range from the **Date range** dropdown list and click **Run report**.

This insight surfaces only for organizations that don't have open federation enabled.

:::image type="content" source="media/detailed-report-view-external-domains-activity.png" alt-text="The detailed report view regarding the external domains activity." lightbox="media/detailed-report-view-external-domains-activity.png":::

#### Teams by user type

The **Teams by user type** widget view shows you how many of your "active" teams comprise:
- Your users only
- Your users and guests
- Your users and external users
- All user types

> [!NOTE]
> Only active teams are included in the breakdown. 

There's a duration selector with the time-frame options **7 days** and **30 days**. You can view the count of active teams and the user-composition type for either of these two time frames. To do this task, you can click the duration selector option (**7 days**/**30 days**), and hover over the pie-chart representation. You'll then be able to view the count of active teams for each user-composition type.

This insight doesn't tell you how many users are in a team; it shows how many teams have each composition type. For example, a team with 100 of your users, no external users, and one guest counts as one team comprised of “my users and guests.”

:::image type="content" source="media/teams-by-user-type.png" alt-text="The Teams by user type widget." lightbox="media/teams-by-user-type.png":::

#### Channels by user type

The **Channels by user type** widget view tells you how many standard, private, and shared channels in your organization comprise:
- Your users (internal to your organization) only
- Your users and guests
- Your users and external users

> [!NOTE]
> Only active standard, private, and shared channels are included in the breakdown.

There's a duration selector with the time-frame options **7 days** and **30 days**. You can view the count of active channels (standard, private, and shared) and their user-composition type for either of these two time frames. To do this task, you can click the duration selector option (**7 days**/**30 days**), and hover over the graphical representation. You'll then be able to view the count of active channels for each user-composition type.

External users can only be in shared channels, and guests can only be in standard and private channels. As a result, you'll only see two counts per type of channel. 

For example, for standard and private channels, you’ll see:
- How many are made up of your users only
- How many are made up of your users and guests

For shared channels, you’ll see:
- How many are made up of your users only
- How many are made up of your users and external users

:::image type="content" source="media/channels-by-user-type.png" alt-text="The Channels by user type widget." lightbox="media/channels-by-user-type.png":::

#### External collaboration activity by team

The **External collaboration activity by team** widget view shows you which teams in your organization have the most collaboration with guests and external users.

:::image type="content" source="media/external-collaboration-activity-by-team.png" alt-text="The External collaboration activity by team widget." lightbox="media/external-collaboration-activity-by-team.png":::

You can click **View details** to see the teams’ names and the "sent message count" for each team. An average message count will also be displayed.

:::image type="content" source="media/external-collaboration-activity-by-team-detailed-report.png" alt-text="The detailed report - External collaboration activity by team." lightbox="media/external-collaboration-activity-by-team-detailed-report.png":::

#### External collaboration activity by user

The **External collaboration activity by user** widget view shows you which of the users internal to your organization have the most collaboration with guests and external users.

:::image type="content" source="media/external-collaboration-activity-by-user.png" alt-text="The External collaboration activity by user widget." lightbox="media/external-collaboration-activity-by-user.png":::

You can click **View details** to see the users’ names and the "sent message count" for each user. An average message count will also be displayed.

:::image type="content" source="media/external-collaboration-activity-by-user-detailed-report.png" alt-text="The detailed report - External collaboration activity by user." lightbox="media/external-collaboration-activity-by-user-detailed-report.png":::

#### Guest user activity

The **Guest user activity** widget shows you which of your guests have the most collaboration with users who are internal to your organization.

:::image type="content" source="media/guest-user-activity.png" alt-text="The Guest user activity widget." lightbox="media/guest-user-activity.png":::

You can click **View details** to see the guest’s names and the "sent message count" for each guest. An average message count will also be displayed.

:::image type="content" source="media/guest-user-activity-detailed-report.png" alt-text="The detailed report - Guest user activity." lightbox="media/guest-user-activity-detailed-report.png":::

This insight doesn't capture Guest<>In-tenant user activity.

### Notes

1. All reports only show users and teams owned by your tenant, but the counts could include activities in cross-tenant collaborations.
    1. For channel events, only the channel’s owning tenant knows about the event. Therefore, if your tenant’s user is participating in channels owned by other tenants, these events don't accrue to any of the reports in your tenant.
    1. For chat (1:1, group, meeting) events, all participating tenants know about the events. So, your tenant’s report knows events initiated not only by users in your tenant but also by others in other tenants.
    1. These are to uphold Microsoft’s promise on privacy and compliance.
2. These reports honor Microsoft 365 level “admin report setting” about concealing or displaying team/user details. For more information, see [Show user details in the reports](/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide&preserve-view=true). When a global administrator configures “conceal team/user details”, reports show obfuscated user/team names instead of their display names.

### Known Issues

1. On time-series charts, last day’s data is empty. For example, on 2/17, time-series chart doesn’t have data for 2/17; so, the data of 2/16 is shown since the lines stop at 2/16.
1. Widget location customizations on dashboard have yet been persisted across sessions.
1. Csv download hasn’t been enabled.
1. Very large events may have a small chance of data categorization error. For example, a very large team with very few guest users may not be categorized as “with guest users”. We're making improvements to address this issue.
