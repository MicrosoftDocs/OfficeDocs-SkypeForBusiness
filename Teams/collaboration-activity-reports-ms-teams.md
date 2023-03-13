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
> Advanced Collaboration Management Insights Preview is provided for evaluation purposes only and may not include all expected functionality.  Data provided during preview will be deleted within 180 days from a tenant deletion action.

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

You can click **View details** to see:

- Names of the inactive teams
- For each of the displayed inactive teams, details such as privacy type, number of channels in the team, and number of users in the team

These details displayed are for the time frame **Last 30 days** which is the default **Date range** value.

:::image type="content" source="media/detailed-report-view.png" alt-text="The detailed report of teams that are inactive." lightbox="media/detailed-report-view.png":::

You can also view the names and similar details of inactive teams for another time frame, you can do it by choosing the **Last 60 days** time frame from the **Date range** dropdown list, and then clicking **Run report**.

You can archive the names and details of the time frame-specific inactive teams. To do this task, you can scroll to the extreme right of the **Inactive teams** widget and click the **bin** icon under the **Action** column, and then select Archive from the **Archive team?** dialog box.

:::image type="content" source="media/archive-option.png" alt-text="The option to archive the details of an inactive team." lightbox="media/archive-option.png":::

#### External domains activity

The **External domains activity** widget view displays the total number of allowed domains; and how many of your allowed domains have been inactive and active. These details of the domains are displayed in the form of a pie-chart representation for the **30 days** or **60 days** time frame, whichever you choose.

> [!NOTE]
> By default, the 30 days time frame is chosen.

:::image type="content" source="media/external-domains-activity.png" alt-text="The report displaying the total number of allowed domains." lightbox="media/external-domains-activity.png":::

You can hover over the pie-chart representation to see the exact count of active and inactive domains for the chosen time frame.

You can click **View details** to view details such as the names of the inactive domains and the last activity date for each of these domains. You can view these details for any of the two time frames, namely **30 days** and **60 days**.

By default, the **30 days** time frame is chosen.
 
:::image type="content" source="media/default-time-frame-external-domains-activity.png" alt-text="The default time frame for the External domains activity widget." lightbox="media/default-time-frame-external-domains-activity.png":::

Therefore, on clicking **View details** when the **30 days** time frame is chosen by default, names of the inactive domains for the last 30 days are displayed. Along with these names, the last activity date of these last-30-days-inactive domains is also displayed.

To view the names of inactive domains for the last 60 days, choose **Last 60 days** from the **Date range** dropdown list on the **Usage reports** page.

This insight surfaces only for organizations that don't have open federation enabled.

:::image type="content" source="media/detailed-report-view-external-domains-activity.png" alt-text="The detailed report view regarding the external domains activity." lightbox="media/detailed-report-view-external-domains-activity.png":::

#### Teams by user type

The **Teams by user type** widget view shows you how many of your teams comprise:
- Your users only
- Your users and guests
- Your users and external users
- All user types

> [!NOTE]
> Only active teams are included in the breakdown.

:::image type="content" source="media/teams-by-user-type.png" alt-text="The Teams by user type widget." lightbox="media/teams-by-user-type.png":::

You can view the count of active teams and the user-composition type for any of the two time frames, namely **7 days** and **30 days**.

By default, the **7 days** time frame is chosen.

:::image type="content" source="media/default-time-frame-teams-by-user-type.png" alt-text="The default time frame for the Teams by user type widget." lightbox="media/default-time-frame-teams-by-user-type.png":::

You can view the count of active teams and the user-composition type for the last 30 days. To do this task, you can click **30 days** on the **Teams by user type** widget.

:::image type="content" source="media/thirty-days-time-frame-teams-by-user-type.png" alt-text="The 30-days time frame in the Teams by user type widget." lightbox="media/thirty-days-time-frame-teams-by-user-type.png":::

This insight doesn't tell you how many users are in a team; it shows how many teams have each composition type. For example, a team with 100 of your users, no external users, and one guest counts as one team comprised of “my users and guests.”

#### Channels by user type

The **Channels by user type** widget view tells you how many channels in your organization comprise:
- Your users (internal to your organization) only
- Your users and guests
- Your users and external users

> [!NOTE]
> Only active channels are included in the breakdown.
> The supported types of channels are standard, private, and shared.

You can view the count and user-composition type for each active channel type for the two time frames, namely **7 days** and **30 days**.

By default, the **7 days** time frame is chosen.

:::image type="content" source="media/default-time-frame-channels-by-user-type.png" alt-text="The default time frame in the Channels by user type widget." lightbox="media/default-time-frame-channels-by-user-type.png":::

You can view the count and user-composition type for each active channel type for the last 30 days. To do this task, you can click **30 days** on the **Channels by user type** widget.

:::image type="content" source="media/thirty-days-time-frame-channels-by-user-type.png" alt-text="The 30-days time frame in the Channels by user type widget." lightbox="media/thirty-days-time-frame-channels-by-user-type.png":::

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

> [!NOTE]
> The data is concealed by default in this widget. To unconceal the data, see [Remove data obfuscation](#remove-data-obfuscation).

You can click **View details** to see the teams’ names and the "sent message count" for each team. An average message count will also be displayed.

:::image type="content" source="media/external-collaboration-activity-by-team-detailed-report.png" alt-text="The detailed report - External collaboration activity by team." lightbox="media/external-collaboration-activity-by-team-detailed-report.png":::

#### External collaboration activity by user

The **External collaboration activity by user** widget view shows you which of the users internal to your organization have the most collaboration with guests and external users.

:::image type="content" source="media/external-collaboration-activity-by-user.png" alt-text="The External collaboration activity by user widget." lightbox="media/external-collaboration-activity-by-user.png":::

> [!NOTE]
> The data is concealed by default in this widget. To unconceal the data, see [Remove data obfuscation](#remove-data-obfuscation).

You can click **View details** to see the users’ names and the "sent message count" for each user. An average message count will also be displayed.

:::image type="content" source="media/external-collaboration-activity-by-user-detailed-report.png" alt-text="The detailed report - External collaboration activity by user." lightbox="media/external-collaboration-activity-by-user-detailed-report.png":::

#### Guest user activity

The **Guest user activity** widget shows you which of your guests have the most collaboration with users who are internal to your organization.

:::image type="content" source="media/guest-user-activity.png" alt-text="The Guest user activity widget." lightbox="media/guest-user-activity.png":::

> [!NOTE]
> The data is concealed by default in this widget. To unconceal the data, see [Remove data obfuscation](#remove-data-obfuscation).

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

### Remove data obfuscation

Three widgets - External collaboration activity by team, External collaboration activity by user, and Guest user activity - use data obfuscation (in other words, concealing the data). To reveal the data, perform the following steps.

1. Launch the URL [https://admin.microsoft.com/](https://admin.microsoft.com/Adminportal/Home).
1. Select **ShowAll < Settings < Org settings**.
   The **Reports** page is displayed.
1. Check the **Display concealed user, group, and site names in all reports** checkbox.
   :::image type="content" source="media/unconcealing-data.png" alt-text="The option to unconceal the data." lightbox="media/unconcealing-data.png":::

   The data obfuscation is removed.

   > [!NOTE]
   > Unchecking the **Display concealed user, group, and site names in all reports** checkbox will conceal the data.

1. Save the policy.
1. Naviate back to TAC to verify whether the data is visible.
