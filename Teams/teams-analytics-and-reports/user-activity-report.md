---
title: Microsoft Teams user activity report
author: cichur
ms.author: v-cichur
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: svemu
f1.keywords:
- NOCSH
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
description: Learn how to use the Teams user activity report in the Microsoft Teams admin center to see how users in your organization are using Teams.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Microsoft Teams user activity report

The Teams user activity report gives insight into the types of activities that users in your organization perform in Teams. For example, one can see how many users communicate on an ad hoc basis through unscheduled meetings commonly referred to as 1:1 and group calls, meetings a Teams user has organized, and meetings a Teams user participated in. We share details about screen, video, and audio minutes, and chat communication statistics, such as how many users reply to and post channel messages, and how many users engage in 1:1 or group chat messages.

## View the user activity report

You must be a Teams service admin to make these changes. See [Use Teams administrator roles to manage Teams](https://docs.microsoft.com/microsoftteams/using-admin-roles) to read about getting admin roles and permissions.

1. In the left navigation of the Microsoft Teams admin center, click **Analytics & reports** > **Usage reports**. On the **View reports** tab, under **Report**, select **Teams user activity**.
2. Under **Date range**, select a range, and then click **Run report**.

    ![Screenshot of the Teams user activity report in the Teams admin center with callouts](../media/teams-reports-user-activity-with-callouts.png "Screenshot of the Teams user activity report in the Teams admin center with callouts")

## Interpret the report

|Callout |Description  |
|--------|-------------|
|**1**   |The Teams user activity report can be viewed for trends over the last 7 days, 30 or 90 days. |
|**2**   |Each report has a date for when this report was generated. The reports usually reflect a 24 hour latency from time of activity. |
|**3**   |<ul><li>The X axis on the charts is the selected date range for the specific report. </li><li>The Y axis is the number of users participating in the activity.</li></ul>Hover over the dot representing an activity on a given date to see the number of instances of that activity on that given date. |
|**4**   |You can filter what you see on the chart by clicking an item in the legend. For example, click **1:1 calls**, **Channel messages**, or **Chat messages** to see only the info related to each one. Changing the selection doesn’t change the information in the table. |
|**5**   |The table gives you a breakdown of usage by user.   <ul><li>**Username** is the display name of the user. You can click the display name to go to the user's settings page in the Microsoft Teams admin center.</li><li>**Channel messages** is the number of unique messages that the user posted in a team chat during the specified time period.</li><li>**Reply messages** is the number of unique reply messages that the user posted in a team channel during the specified time period.</li> <li>**Post messages** is the number of unique post messages that the user posted in a team channel during the specified time period.</li><li>**Chat messages** is the number of unique messages that the user posted in a private chat during the specified time period.</li><li>**Urgent messages** is the number of urgent messages that the user posted in a  chat during the specified time period.</li><li>**Total meetings** is the total number of scheduled and ad hoc meetings a user participated in during the specified time period.</li><li>**Meetings organized** is the number of scheduled and ad hoc meetings a user organized during the specified time period.</li><li>**Meetings organized scheduled** is the number of scheduled meetings a user organized during the specified time period.</li><li>**Meetings organized ad hoc** is the number of ad hoc meetings a user organized during the specified time period.</li><li>**Meetings participated** is the number of the scheduled and the ad hoc meetings a user participated in during the specified time period.</li><li>**Meetings participated scheduled** is the number of the scheduled meetings a user participated in during the specified time period.</li><li>**Meetings participated ad hoc** is the number of ad hoc meetings a user participated in during the specified time period.</li><li>**1:1 calls** is the number of 1:1 calls that the user participated in during the specified time period.</li><li>**Audio time** is the total audio time that the user participated in during the specified time period (measured in minutes). </li><li>**Video time** is the total video time that the user participated in during the specified time period (measured in minutes). </li><li>**Screen sharing time** is the total screen share time that the user participated in during the specified time period (measured in minutes). </li>  <li>**Last activity** is the last date (UTC) that the user participated in a Teams activity.</li><li>**Other activity** tracks when the user is considered active but has a value of zero for chat messages, 1:1 calls, channel messages, total meetings, and meetings organized. Examples of actions are when a user opens a channel message post but doesn't reply to it or when a user receives a private message and reads it but doesn't respond to it.</li> </ul>Note that **Group calls** has been replaced by **Meetings organized ad hoc** and **Meetings participated ad hoc**, in which the sum of these two values is equal to what was measured by **Group calls**.
|**6**   |Select **Edit columns** to add or remove columns in the table. |
|**7**   |You can export the report to a CSV file for offline analysis. Click **Export to Excel**, and then on the **Downloads** tab, click **Download** to download the report when it's ready.<br><br>![Screenshot of the Downloads tab showing exported reports to download](../media/teams-reports-export-to-csv.png) <br>When you view the report in Excel, you'll also see an **Id** column, which represents the team ID. A team ID is typically an alphanumeric string. If the **Id** column shows as **\n**, this means that a user requested their information to be deleted. ||

[!INCLUDE [teams-reports-definitions](../includes/teams-reports-definitions.md)]

## Related topics

- [Teams analytics and reporting](teams-reporting-reference.md)
