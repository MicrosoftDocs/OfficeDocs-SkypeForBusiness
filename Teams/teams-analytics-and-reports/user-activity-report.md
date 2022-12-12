---
title: Microsoft Teams user activity report
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: svemu
f1.keywords:
- NOCSH
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
description: Learn how to use the Teams user activity report in the Microsoft Teams admin center to see how users in your organization are using Teams.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Microsoft Teams user activity report

The Teams user activity report gives insight into the types of activities that users in your organization do in Teams. You can see how many users communicate on an unplanned basis through unscheduled meetings (1:1 and group calls). See how many meetings a Teams user has organized, and meetings a Teams user has participated in. See details about screen, video, and audio minutes, and chat communication statistics, such as how many users reply to and post channel messages, and how many users engage in 1:1 or group chat messages.

With more added information about internal and external users, you can now measure users' interaction in internal and external [shared channels](/Teams/shared-channels.md). For example, metrics like tenant name where the user belongs, external tenant names where the user is interacting, and whether the user is external to the tenant will help admins to measure users' inteaction through shared channel features. 

> [!NOTE]
> The ability to schedule a user activity report isn't available at this time.

## View the user activity report

You must be either a global admin, global reader, or Teams service admin to view the report in the Microsoft Teams admin center. See [Use Teams administrator roles to manage Teams](../using-admin-roles.md) to read about getting admin roles and permissions.

1. In the left navigation of the Microsoft Teams admin center, select **Analytics & reports** > **Usage reports**. On the **View reports** tab, under **Report**, select **Teams user activity**.
2. Under **Date range**, select a range, and then select **Run report**.

    ![Screenshot of the Teams user activity report in the Teams admin center with callouts.](../media/teams-reports-user-activity-with-callouts2.png "Screenshot of the Teams user activity report in the Teams admin center with callouts")

## Interpret the report

| **Callout** |**Description**  |
|--------|-------------|
|**1**   |The Teams user activity report can be viewed for trends over the last 7, 30, 90 or 180 days. |
|**2**   |Each report has a date for when this report was generated. The reports usually reflect a 24-48 hour latency from the time of activity. |
|**3**   |Time series data represented in the top graph show different usage metrics aggregated for the entire tenant. |
|**4**   |Tabular data represented in the bottom half shows different usage metrics aggregated per user. |
|**5**   |<ul><li>The X axis on the chart is the selected date range for the report.</li> <li> The Y axis is the count of active items or activity.</li> </ul>Hover over the dot representing an item or activity on a given date to see the number of instances of that item or activity on that given date.|
|**6**   | Each of the metrics is represented in the graph at the tenant level. Filter what you see on the chart by selecting an item in the legend. Select **Channel messages**, **Reply messages**,  **Chat messages**, or **Meetings Organized** and more to see info related to each one. Changing this selection doesn’t change the information in the table. |
|**7**   |The table gives you a breakdown of usage by user.   <ul><li>**User name** is the email address of the user. See [the following section](#make-the-user-specific-data-anonymous) to get guidance on how to anonymize it.  Select the user name to go to the user details page.</li><li>**Tenant name** (new) is the name of an internal or external tenant where a user belongs. If a user belongs to an external tenant, different usage metrics (for example, post messages, reply messages, and more) are calculated based on his interactions in one or more shared channels of the admin’s tenant. Interactions done by an external user in his own tenant are not considered for the admin usage report of a given tenant.  </li><li>**Shared channel tenant names** (new) is the names of internal or external tenants where the user participated as part of a shared channel.</li><li>**Channel messages** is the number of unique messages that the user posted in a team channel during the specified time period.</li><li>**Replies** is the number of unique reply messages that the user posted in a team channel during the specified time period.</li> <li>**Posts** is the number of unique post messages that the user posted in a team channel during the specified time period.</li><li>**Chat messages** is the number of unique messages that the user posted in a private chat during the specified time period.</li><li>**Urgent messages** is the number of urgent messages that the user posted in a  chat during the specified time period.</li><li>**Total organized Meetings** is the sum of one time scheduled, recurring, unplanned, and unclassified meetings a user organized during the specified time period.</li><li>**Meetings organized scheduled onetime** is the number of one-time scheduled meetings a user organized during the specified time period.</li><li>**Meetings organized scheduled recurring** is the number of recurring meetings a user organized during the specified time period.</li><li>**Meetings organized adhoc** is the number of unplanned meetings a user organized during the specified time period.</li><li>**Total participated Meetings** is the sum  of the one-time scheduled, recurring, unplanned, and unclassified meetings a user participated in during the specified time period.</li><li>**Meetings participated scheduled onetime** is the number of the one-time scheduled meetings a user participated in during the specified time period.</li><li>**Meetings participated scheduled recurring** is the number of recurring meetings a user participated in during the specified time period.</li><li>**Meetings participated adhoc** is the number of unplanned meetings a user participated in during the specified time period.</li><li>**1:1 calls** is the number of 1:1 calls that the user participated in during the specified time period.</li><li>**Audio time** is the total audio time (in minutes) that the user participated in during the specified time period.</li><li>**Video time** is the total video time (in minutes) that the user participated in during the specified time period.</li><li>**Screen share time** is the total screen share time (minutes) that the user participated in during the specified time period.</li>  <li>**Last activity** is the last date (UTC) that the user participated in a Teams activity.</li><li>**Other activity** tracks when the user is considered active but has a value of zero for chat messages, 1:1 calls, channel messages, total meetings, and meetings organized. Examples of actions are when a user changes the Teams status or the Teams status message, when a user opens a channel message post but doesn't reply to it, or when a user receives a private message and reads it but doesn't respond to it.</li> </ul> **Unclassified meetings** are those that can't be identified as scheduled, recurring, or unplanned. These are few in number and often can't be identified because of imperfect telemetry information.<br><br>**Group calls** has been replaced by **Meetings organized adhoc** and **Meetings participated adhoc**. The sum of these two values is equal to what was measured by **Group calls**. <br/><br/>Note that if a user no longer exists, the name is displayed as "--" in the table.
|**8**   |Select **Edit columns** to add or remove columns in the table. |
**9**   |Export the report to a CSV file for offline analysis. Select **Export to Excel** and the report will be downloaded within your browser. <br>When you view the report in Excel: <br>- You'll also see a **User ID** column, which represents the User ID. A User ID is typically an alphanumeric string. <br>- You'll also notice that the **Audio duration**, **Video duration**, and **Screen Share duration** columns are represented both in days and in seconds. |


[!INCLUDE [teams-reports-definitions](../includes/teams-reports-definitions.md)]

## Make the user-specific data anonymous

To make the data in the Teams user activity report anonymous, you have to be a global administrator. The Global administrator can hide identifiable information (using MD5 hashes) such as display name, group name, email, and AAD ID in reports and their export.

1. In Microsoft 365 admin center, go to the **Settings** \> **Org Settings**, and under **Services** tab, choose **Reports**.
    
2. Select **Reports**, and then choose to **Display concealed user, group, and site names in all reports**. This setting gets applied both to the usage reports in Microsoft 365 admin center and Teams admin center.
  
3. Select **Save changes**.


> [!NOTE]
> Enabling this setting will de-identify user, group, and site name information in the [Teams user activity report](user-activity-report.md), [Teams device usage report](device-usage-report.md), and [Teams usage report](teams-usage-report.md) . Starting September 1, 2021, this setting is by default enabled for everyone as part of our ongoing commitment to help protect important information and enable companies to support their local privacy laws. 
> This setting also applies to Microsoft 365 usage reports in the Microsoft 365 admin center, Microsoft Graph, and Power BI.
## Related topics

- [Teams analytics and reporting](teams-reporting-reference.md)
