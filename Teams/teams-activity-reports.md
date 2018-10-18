---
title: Use activity reports for Microsoft Teams
author: ChuckEdmonson
ms.author: chucked
manager: lolaj
ms.date: 04/17/2018
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: chenle
localization_priority: Normal
search.appverid: MET150
MS.collection: Teams_ITAdmin_Help
description: Learn how to use activity reports to see how users in your organization are using Microsoft Teams.
appliesto: 
- Microsoft Teams
---

Use activity reports for Microsoft Teams 
========================================

You can use activity reports to see how users in your organization are using Microsoft Teams. For example, if some don’t use Teams yet, they might not know how to get started or understand how they can use Teams to be more productive and collaborative. Your organization can use the activity reports to decide where to prioritize training and communication efforts.

## How to get to the Reports dashboard

1. In the [Office 365 admin center](https://portal.office.com/adminportal/home), select **Reports** > **Usage**.
 
2. On the **Usage** page, choose **Select a report** to select from a list of the available reports. 

## Teams activity reports that are available

There are currently two activity reports you can view:

- Microsoft Teams user activity report 
- Microsoft Teams device usage report 

### Microsoft Teams user activity report

The Microsoft Teams user activity report gives you a view of the most common activities that your users perform in Microsoft Teams. This includes how many people engage in a chat in a channel, how many communicate via private chat message, and how many participate in calls or meetings. You can see this information both at the tenant level, as well as for each individual user.

![Screenshot of the Teams user activity report in the Office 365 admin center.](media/teams-user-activity-report.png)

#### Interpret the Microsoft Teams user activity report

You can get a view into Microsoft Teams user activity by looking at the **Activity** and **Users** charts.

![Screenshot of the Teams user activity report in the Office 365 admin center with numbered callouts.](media/teams-user-activity-report-with-callouts.png)

|Callout |Description  |
|--------|-------------|
|**1**   |The Microsoft Teams user activity report can be viewed for trends over the last 7 days, 30 days, 90 days, or 180 days. However, if you click into a particular day in the report, the table (7) will show data for 30 days, up to the date (2) for when the report was generated. |
|**2**   |Each report has a date for when this report was generated. The reports usually reflect a 24 to 48 hour latency from time of activity. |
|**3**   |The **Activity** view shows you the number of Microsoft Teams activities by activity type. The activity types are number of teams chat messages, private chat messages, calls, or meetings. |
|**4**   |The **Users** view shows you the number of users by activity type. The activity types are number of teams chat messages, private chat messages, calls, or meetings. |
|**5**   |The X axis on the charts is the selected date range for the specific report. <ul><li>On the **Activity** chart, the Y axis is the count of specified activity.</ul></li> <ul><li>On the **Files** chart, the Y axis is the number of users participating in teams chats, private chats, calls, or meetings.</ul></li> |
|**6**   |You can filter the series you see on the chart by clicking on an item in the legend. For example, on the **Activity** chart, click or tap **Channel messages**, **Chat messages**, **Calls**, or **Meetings** to see only the info related to each one. Changing this selection doesn’t change the information in the grid table. |
|**7**   |The list of groups shown is determined by the set of all groups that existed (weren't deleted) across the widest (180-day) reporting time frame.  The activity count will vary according to the date selection. <ul><li>**Username** is the email address of the user. You can display the actual email address or make this field anonymous.</ul></li> <ul><li>**Last Activity Date (UTC)** refers to the last date that the user participated in a Microsoft Teams activity.</ul></li> <ul><li>**Channel messages** is the number of unique messages that the user posted in a team chat during the specified time period.</ul></li> <ul><li>**Chat messages** is the number of unique messages that the user posted in a private chat during the specified time period.</ul></li> <ul><li>**Calls** is the number of calls that the user participated in during the specified time period.</ul></li> <ul><li>**Meetings** is the number of online meetings that the user participated in during the specified time period.</ul></li> <ul><li>**Other activity** is the number of other team activities by the user some of which include, and not limited to: liking messages, apps, working on files, searching, following teams and channel and favoriting them.</ul></li> <ul><li>**Deleted** indicates if the team is deleted. If the team is deleted, but had activity in the reporting period, it will show up in the grid with deleted set to true.</ul></li> <ul><li>**Deleted date** is the date that the team was deleted.</ul></li> <ul><li>**Product assigned** is the list of products that are assigned to the user.</ul></li> <ui>**Note:** You might not see all the items in the list below in the columns until you add them. </ul><br><br> <ui>If your organization's policies prevents you from viewing reports where user information is identifiable, you can change the privacy setting for all these reports. Check out the **How do I hide user level details?** section in the [Activity Reports in the Office 365 Admin Center Preview](https://support.office.com/article/activity-reports-in-the-office-365-admin-center-0d6dfb17-8582-4172-a9a9-aed798150263).</ui> |
|**8**   |Click or tap **Columns** to add or remove columns from the report. |
|**9**   |You can also export the report data into an Excel .csv file, by clicking or tapping the Export link. This exports data of all users and enables you to do simple sorting and filtering for further analysis. If you have less than 2,000 users, you can sort and filter within the table in the report itself. If you have more than 2,000 users, in order to filter and sort, you will need to export the data. |

### Microsoft Teams device usage report

The Microsoft Teams app usage report provides you with information about how your users connect to Microsoft Teams, including mobile apps. The report helps you understand which devices are popular in your organization and how many users work on the go.

![Screenshot of the Teams device usage report in the Office 365 admin center.](media/teams-device-usage-report.png)

## Who can access the Teams activity reports

The activity reports can be accessed by users that are assigned:

- Office 365 global admin role
- Product-specific admin role (Exchange, Skype for Business, or SharePoint)
- Reports reader role

### Reports reader role

You can assign the *Reports reader* role to non-IT staff who you want to have access to these reports. By assigning this role to training managers or business stakeholders, you can make sure that they have access to the insights that are helpful to drive and track adoption of Teams.

## Other information on the Reports dashboard

### At-a-glance activity widget

The Reports dashboard includes the usage data from Microsoft Teams in the at-a-glance activity widget, which gives you a cross-product view of how users communicate and collaborate using the other various services in Office 365.

![Screenshot of the Teams at-a-glance activity widget on the Reports dashboard.](media/at-a-glance-activity-widget.png)

### Teams activity card

The Reports dashboard also includes a new card for Microsoft Teams. The card gives you an overview of the activity in Teams, including the number of active users, so that you can quickly understand how many users are using the service.

![Screenshot of the Teams activity card on the Reports dashboard.](media/teams-activity-card.png)
