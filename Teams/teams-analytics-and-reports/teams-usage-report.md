---
title: Microsoft Teams usage report
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: kojika
f1.keywords:
- NOCSH
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
description: Learn how to use the Teams usage report in the Microsoft Teams admin center to get an overview of Teams activity in your organization.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---
# Microsoft Teams usage report

The Teams usage report in the Microsoft Teams admin center gives you an overview of the usage activity in Teams, including the number of active users and channels, so you can quickly see how many users across your organization are using Teams to communicate and collaborate. You can view usage information for  teams, including the number of active users and channels, guests, and messages in each team.

With more added information about internal and external users, you can now measure collaboration within internal and external [shared channels](/Teams/shared-channels.md) in a team. For example, metrics like active shared channels and external active users in a team will help the admin measure collaboration across shared channels within a team.

## View the usage report

You must be either a global admin, global reader, or Teams service admin to view the reports in Teams admin center. See [Use Teams administrator roles to manage Teams](../using-admin-roles.md) to read about getting admin roles and permissions.

1. In the left navigation of the Microsoft Teams admin center, click **Analytics & reports** > **Usage reports**. On the **View reports** tab, under **Report**, select **Teams usage**.
2. Under **Date range**, select a range, and then click **Run report**.

    ![Screenshot of the Teams usage report in the Teams admin center with callouts.](../media/teams-reports-teams-usage-with-callouts2.png "Screenshot of the Teams usage report in the Teams admin center with callouts")

## Interpret the report

|Callout |Description  |
|--------|-------------|
|**1**   |The Teams usage activity report can be viewed for trends over the last 7, 30, 90, and 180 days. |
|**2**   |Each report has a date for when this report was generated. The reports usually reflect a 24-48 hour latency from time of activity. |
|**3**   |<ul><li>The X axis on the chart is the selected date range for the report.</li> <li> The Y axis is the count of active items or activity.</li> </ul>Hover over the dot representing an item or activity on a given date to see the number of instances of that item or activity on that given date.|
|**4**   |You can filter what you see on the chart by clicking an item in the legend. For example, click  **Internal active users**, **Active guests**,  **Active channels**, **Posts**, and more to see only the info related to each one. Changing this selection doesn’t change the information in the table. |
|**5**   |The table gives you a breakdown of usage by team. <ul><li>**Team name** is the display name of the team. You can click the team name to go to the team's settings page in the Microsoft Teams admin center. </li> <li>**Team ID** is the unique team identifier. </li> <li>**Type** refers to whether the team is a private team or public team  .</li> <li>**Internal active users** is the number of active users including guests who perform an action in that team in the specified time period. <br/>Internal users and guests reside in the same tenant but are not the same.</li><li>**Active guests** is the number of guests who perform an action in that team in the specified time period.</li> <li>**External active users** (new) is the number of active users from external organizations who perform an action in that team in a resource - such as a shared channel in a team. <br/> External users have their own identities in different tenants and are not the same as a guest account.</li><li>**Active channels** is the number of channels in the team that has at least one active user in the specified time period. This includes private, public, and shared channels. </li><li>**Active shared channels** (new) is the number of shared channels in a team that has at least one active internal or external user in the specified time period. </li> <li>**Total organized meetings** is the sum of one time scheduled, recurring, unplanned, and unclassified meetings a user organized during the specified time period. </li><li>**Posts** is the number of all the post messages in channels in the specified time period.</li> <li>**Replies** is the number  of all the reply messages in channels in the specified time period.</li> <li>**Mentions** is the number of all the mentions used in messages in the specified time period.</li><li>**Reactions** is the number  of all the reactions to messages in the specified time period.</li><li>**Urgent messages** is the number of all the urgent messages in the specified time period.</li><li>**Channel messages** is the number of unique messages that the team's users posted in team chats during the specified time period.</li> </li> </ul>Note that if a team no longer exists, the name is displayed as "--" in the table. <br><br>To see the information that you want in the table, make sure to add the columns to the table. |
|**6**   |Select **Edit columns** to add or remove columns in the table.|
|**7**   |Export the report to a CSV file for offline analysis. Select the **Export to Excel** icon, and the report will be downloaded within your browser.|
|**8** |Time series data represented in the top graph show different usage metrics aggregated for the entire tenant|
|**9** |Tabular data represented in the bottom half shows different usage metrics aggregated per team|

[!INCLUDE [teams-reports-definitions](../includes/teams-reports-definitions.md)]


## Make the user specific data anonymous

To make the data in Teams user activity report anonymous, you have to be a global administrator. The global administrator can hide identifiable information (using MD5 hashes) such as display name, group name, email, and AAD ID in the report and its export.

1. In Microsoft 365 admin center, go to the **Settings** \> **Org Settings**, and under **Services** tab, choose **Reports**.
    
2. Select **Reports**, and then choose to **Display concealed user, group, and site names in all reports**. This setting gets applied both to the usage reports in Microsoft 365 admin center as well as Teams admin center.
  
3. Select **Save changes**.

> [!NOTE]
> Enabling this setting will de-identify user, group, and site name information in [Teams user activity report](user-activity-report.md), [Teams device usage report](device-usage-report.md), and [Teams usage report](teams-usage-report.md). Starting September 1, 2021, this setting is enabled by default for everyone as part of our ongoing commitment to help protect important information and enable companies to support their local privacy laws. 
>
>This setting also applies to Microsoft 365 usage reports in Microsoft 365 admin center, Microsoft Graph, and Power BI.

## Related topics

- [Teams analytics and reporting](teams-reporting-reference.md)
