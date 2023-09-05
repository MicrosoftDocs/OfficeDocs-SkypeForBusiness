---
title: Collaboration activity reports for Microsoft Teams
ms.author: v-smandalika
author: v-smandalika
manager: dansimp
ms.reviewer: roykuntz; jens
ms.date: 08/16/2023
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
description: Learn about the Collaboration activity reports in Microsoft Teams.
---

# Collaboration activity reports for Microsoft Teams

> [!IMPORTANT]
> Advanced Collaboration Management Insights Preview is provided for evaluation purposes only and may not include all expected functionality. Data provided during preview will be deleted within 180 days from a tenant deletion action.

The Collaboration activity reports for Microsoft Teams aim to give Teams administrators visibility into their organization’s external collaboration habits, such that they can facilitate successful collaboration and mitigate potential risks that come with allowing external collaboration. In future iterations of the Collaboration activity reports, this feature will enable Teams administrators to automate their work.
  
Through Collaboration activity reports, you can surface insights about your teams, federated domains, channels, guests, and users internal to your organization.

## Where to find Collaboration activity reports

The Collaboration activity reports can be found in the Teams Admin Center dashboard under the **Collaboration activity** tab, as depicted in the following screenshot:

:::image type="content" source="media/dashboard-collaboration-activity-feature.png" alt-text="The dashboard displaying the Collaboration activity reports menu item." lightbox="media/dashboard-collaboration-activity-feature.png":::

## Components

This section describes the following components of the Collaboration activity reports:

- [Inactive teams](#inactive-teams)
- [Inactive external domains activity](#inactive-external-domains-activity)
- [Teams by user type](#teams-by-user-type)
- [Channels by user type](#channels-by-user-type)
- [Teams with the most external user and guest activity](#teams-with-the-most-external-user-and-guest-activity)
- [Users with the most external user and guest collaboration](#users-with-the-most-external-user-and-guest-collaboration)
- [Guests with the most external user and guest collaboration](#guests-with-the-most-external-user-and-guest-collaboration)

### Inactive teams

We recommend the removal of inactive teams to avoid the spread of confidential information when not necessary.

> [!NOTE]
> Every team has an associated site automatically created for it on Teams. An inactive team's associated site will also be inactive. To view the inactive teams whose associated sites are also inactive, you can use Site Lifecycle Management (SLM) policies. For more information about SLM and how to create policies for tracking inactive sites, see [Site Lifecycle Management (SLM)](#site-lifecycle-management-slm).

The **Inactive teams** widget view shows only inactive teams whose connected workloads are also inactive. It shows you how many teams in your organization have been inactive for the last 30 or 60 days. You can hover over each bar to see the exact counts for the specific day that falls in the last 30-60 days timeframe.

:::image type="content" source="media/inactive-teams.png" alt-text="The screen displaying details of teams that are inactive." lightbox="media/inactive-teams.png":::

Click **View details** to see which teams these are. For each team, you can see the privacy type, number of channels in the team, and number of users in the team.

:::image type="content" source="media/detailed-report-view.png" alt-text="The detailed report of teams that are inactive." lightbox="media/detailed-report-view.png":::

By default, we show you the teams that have been inactive from the last 30 days.

To change the time frame, select the range of date from the **Date range** drop-down list, and select **Run report**.

You can also archive the team directly from the report. However, archiving a team has no impact on the connected workloads, with the team only going into a read-only mode.

To archive an inactive team, scroll to the extreme right, under **Action** column, select **bin** icon. In the *Archive team?* dialog box, select **Archive**.

:::image type="content" source="media/archive-option.png" alt-text="The option to archive the details of an inactive team." lightbox="media/archive-option.png":::.

### Inactive external domains activity

The **Inactive external domains activity** widget view shows you how many domains are allowed and how many of your allowed domains have been active and inactive for the last 30 or 60 days. You can hover over each part of the pie chart representation to see exact counts for that day.

:::image type="content" source="media/external-domains-activity.png" alt-text="The report displaying the total number of allowed domains." lightbox="media/external-domains-activity.png":::

> [!NOTE]
> This insight will not surface for organizations with open federation enabled.

You can click **View details** to see which domains are inactive. For each domain, we show the last activity date. We begin calculating the last activity date from the day your tenant buys the Teams Premium licenses. 

By default, we show you the domains that have been inactive from the last 30 days.

You can change the time frame by choosing from the **Date range** dropdown list and clicking **Run report**.
 
:::image type="content" source="media/detailed-report-view-external-domains-activity.png" alt-text="The detailed report view regarding the external domains activity." lightbox="media/detailed-report-view-external-domains-activity.png":::

### Teams by user type

The **Teams by user type** widget view shows you how many active teams are there for the last 7 or 30 days, and how many teams comprise the following user compositions:
- Your users only
- Your users and guests
- Your users and external users
- All user types

:::image type="content" source="media/teams-by-user-type.png" alt-text="The Teams by user type widget." lightbox="media/teams-by-user-type.png":::

> [!NOTE]
> This insight doesn't tell you how many users are in a team; it shows how many teams have a specific user composition. For example, a team with 100 of your users and one guest counts as one team comprised of “my users and guests”.

By default, we show the breakdown for teams active for the last 7 days.

### Channels by user type

The **Channels by user type** widget view shows you how many active channels are there for the last 7 or 30 days, and how many channels comprise the following user compositions:
- Your users (internal to your organization) only
- Your users and guests
- Your users and external users

:::image type="content" source="media/channels-by-user-type.png" alt-text="The Channels by user type widget." lightbox="media/channels-by-user-type.png":::

> [!NOTE]
> The supported types of channels are standard, private, and shared.
> This insight doesn't tell you how many users are in a channel; it shows how many channels have a specific user composition.

By default, we show the breakdown for channels active for the last 7 days.

External users can only be in shared channels, and guests can only be in standard and private channels. As a result, you'll only see two counts per type of channel. 

For example, for standard and private channels, you’ll see:
- How many are made up of your users only
- How many are made up of your users and guests

For shared channels, you’ll see:
- How many are made up of your users only
- How many are made up of your users and guests

### Teams with the most external user and guest activity

The **Teams with the most external user and guest activity** widget view shows you which teams in your organization have the most collaboration with guests and external users for the last 7 or 30 days.

:::image type="content" source="media/external-collaboration-activity-by-team.png" alt-text="The External collaboration activity by team widget." lightbox="media/external-collaboration-activity-by-team.png":::

> [!NOTE]
> The data is concealed by default in this widget. To reveal the data, see [Remove data obfuscation](#remove-data-obfuscation).

You can click **View details** to see the teams’ names and the "sent message count" for each team. An average message count will also be displayed.

:::image type="content" source="media/external-collaboration-activity-by-team-detailed-report.png" alt-text="The detailed report - External collaboration activity by team." lightbox="media/external-collaboration-activity-by-team-detailed-report.png":::

By default, we show you the teams who have engaged in external collaboration in the last 7 days.

You can change the time frame by choosing from the **Date range** dropdown list and clicking **Run report**.

### Users with the most external user and guest collaboration

The **Users with the most external user and guest collaboration** widget view shows you which of the users internal to your organization have the most collaboration with guests and external users for the last 7 or 30 days.

:::image type="content" source="media/external-collaboration-activity-by-user.png" alt-text="The External collaboration activity by user widget." lightbox="media/external-collaboration-activity-by-user.png":::

> [!NOTE]
> The data is concealed by default in this widget. To reveal the data, see [Remove data obfuscation](#remove-data-obfuscation).

You can click **View details** to see the users’ names and the "sent message count" for each user. An average message count will also be displayed.

:::image type="content" source="media/external-collaboration-activity-by-user-detailed-report.png" alt-text="The detailed report - External collaboration activity by user." lightbox="media/external-collaboration-activity-by-user-detailed-report.png":::

By default, we show you details for the last 7 days.

You can change the time frame by choosing from the **Date range** dropdown list and clicking **Run report**.

### Guests with the most external user and guest collaboration

The **Guest with the most external user and guest collaboration** widget shows you which of your guests have the most collaboration with users who are internal to your organization for the last 7 or 30 days.

:::image type="content" source="media/guest-user-activity.png" alt-text="The Guest user activity widget." lightbox="media/guest-user-activity.png":::

> [!NOTE]
> This insight doesn't capture Guest<>In-tenant user activity, but only the Guest<>Guest and Guest<>External user activities. Guest<>External user activities occur in group chats but not in 1:1 chats.

> The data is concealed by default in this widget. To reveal the data, see [Remove data obfuscation](#remove-data-obfuscation).

You can click **View details** to see the guest’s names and the "sent message count" for each guest. An average message count will also be displayed.

:::image type="content" source="media/guest-user-activity-detailed-report.png" alt-text="The detailed report - Guest user activity." lightbox="media/guest-user-activity-detailed-report.png":::

By default, we show you the guest users who have engaged in external collaboration for the last 7 days.

You can change the time frame by choosing from the **Date range** dropdown list and clicking **Run report**.

#### Site Lifecycle Management (SLM)

SLM (Site Lifecycle Management) is a feature within the SharePoint admin center (SPAC). To access and use this feature, tenants must subscribe to the Microsoft Syntex - SharePoint Advanced Management (SAM) license.

An SLM policy is a mechanism by which a SharePoint administrator can manage SharePoint sites.

You can view the data of inactive teams in an SLM policy report. For more information on an SLM policy report, the data it stores, and categorization of its data, see [Manage site lifecycle policies](/sharepoint/site-lifecycle-management).

SLM provides for policies to manage inactive sites. There can be 5 inactive site policies at a given time on SPAC. The Teams admin center (TAC) administrator can search for policies of inactive sites whose associated teams are also inactive. In other words, they can search for policies whose scope includes **Teams connected sites**.

To check the scope for a policy:

1. Select a policy on the **Site lifecycle management** page. The panel containing the details of the policy appears.
1. Select the **Scope** tab.

   :::image type="content" source="media/finding-scope-of-policy.png" alt-text="Screenshot showing the scope that an SLM policy has." lightbox="media/finding-scope-of-policy.png":::

   The inactive sites connected to inactive teams in the policy are indicated by the highlighted section.

You can download the report of this policy, which returns data of inactive sites. In this report, those inactive sites which have the value **TRUE** under the **Connected to Teams** column are the inactive sites whose associated teams are also inactive.

:::image type="content" source="media/report-of-slm-policy.png" alt-text="Screenshot of the report of an SLM policy." lightbox="media/report-of-slm-policy.png":::

An SLM policy is of the following types:

- **Simulation**: A simulation policy is one that runs once based on the parameters you have provided. If this policy fails, you have to delete this policy and create a new one.
- **Active**: An active policy is one that runs monthly. When you run this policy, it leads to:
    - generation of reports
    - notifications to site owners of the inactive sites. For more information on the notifications to the owners of the inactive sites, see [Notification to site owners](#notification-to-site-owners).

##### Functionalities

An SLM policy has the following functionalities:
- [Detection of inactive sites](#detection-of-inactive-sites)
- [Notification to site owners](#notification-to-site-owners)
- [Reports](#reports)

###### Detection of inactive sites

An SLM policy when run detects sites that have been inactive for a specified period of time.

> [!NOTE]
> The value for the "specified period of time" is defined by the SharePoint administrator when creating a policy. Based on this threshold value, inactive sites are detected and an email notification to the site owner is triggered.

For example, if the specified period of time is 6 months, you select **6 months** under **How long after the last activity should a site be considered inactive?** on the **Set policy scope** page.

:::image type="content" source="media/set-policy-scope-page.png" alt-text="Screenshot showing the Set policy scope page." lightbox="media/set-policy-scope-page.png":::

###### Notification to site owners

Once inactive sites are detected after running the SLM policy, an email notification is triggered to the owners of the sites. These notifications inform the site owners that their sites have been inactive for the specified period of time. These notifications prompt the site owners to confirm if their site is "active" or "inactive".

If the site owner wants to keep the site, the site owner should respond by selecting the **Certify site** button on the notification email. 

Notifications are sent to the site owner for the first 3 months, after which no notification is sent for the next 3 months. If the site owner doesn't respond after three successive notifications, this site is listed as **No owner action** in the policy execution report. The SharePoint administrator can then choose to take action on such sites, based on discretion.

###### Reports

Once a policy has been created and run, the inactive sites are detected and email notifications are triggered for the site owner.This data is available in the form of a report which can be downloaded by clicking the **Download** link under the **Report** column on the **Site lifecycle management** page.

:::image type="content" source="media/slm-screen-download-reports.png" alt-text="Screenshot showing the Site lifecycle management page from which you can download the report." lightbox="media/slm-screen-download-reports.png":::

To know which are the inactive sites that are associated with inactive teams, you can look for the value **YES** under the **Connected to Teams** column in the report. An example of a report is shown in the following screenshot:

:::image type="content" source="media/report-of-slm-policy.png" alt-text="Screenshot showing the report of an SLM policy which can be downloaded from the Site lifecycle management page." lightbox="media/report-of-slm-policy.png":::

The inactive sites in the report which have the value **YES** under the **Connected to Teams** column are those sites which are associated with inactive teams.

##### Create a new policy for inactive sites

To create an inactive site policy, perform the following steps:

1. Go to SharePoint admin center.
1. Select **Policies > Site lifecycle management**.
1. Select **+ Create policy** and then select **Next**.
1. Enter the policy scope parameters based on which you want to retrieve data, and select **Next**.

   :::image type="content" source="media/setting-parameters-for-slm-policy.png" alt-text="Screenshot showing the page on which you can set the parameters that will determine the data of the SLM policy report." lightbox="media/setting-parameters-for-slm-policy.png":::

1. Provide a name for your policy, provide a description (optional), select a policy mode.

   :::image type="content" source="media/define-details-of-policy.png" alt-text="Screenshot on which you define the details for the SLM policy, such as name, description, and the policy mode." lightbox="media/define-details-of-policy.png":::

1. Select **Next**.
1. Select **Done**. Your policy is now created, and can be viewed and managed from the **Site lifecycle management** dashboard.

#### Notes

1. All reports only show users and teams owned by your tenant, but the counts could include activities in cross-tenant collaborations.
    1. For channel events, only the channel’s owning tenant knows about the event. Therefore, if your tenant’s user is participating in channels owned by other tenants, these events don't accrue to any of the reports in your tenant.
    1. For chat (1:1, group, meeting) events, all participating tenants know about the events. So, your tenant’s report knows events initiated not only by users in your tenant but also by others in other tenants.
    1. These are to uphold Microsoft’s promise on privacy and compliance.
2. These reports honor Microsoft 365 level “admin report setting” about concealing or displaying team/user details. For more information, see [Show user details in the reports](/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide&preserve-view=true). When a global administrator configures “conceal team/user details”, reports show obfuscated user/team names instead of their display names.

#### Known issues

1. On the time-series charts, last day’s data is empty. For example, on 2/17, time-series chart doesn’t have data for 2/17; so, the data of 2/16 is shown since the lines stop at 2/16.
1. Widget location customizations on dashboard are yet to be persisted across sessions.
1. Csv download hasn’t been enabled.
1. Very large events may have a small chance of data categorization error. For example, a very large team with very few guest users may not be categorized as “with guest users”. We're making improvements to address this issue.

#### Remove data obfuscation

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
1. Navigate back to TAC to verify whether the data is visible.
