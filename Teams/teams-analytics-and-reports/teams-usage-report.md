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

## View the usage report

1. In the left navigation of the Microsoft Teams admin center, click **Analytics & reports** > **Usage reports**. On the **View reports** tab, under **Report**, select **Teams usage**.
2. Under **Date range**, select a range, and then click **Run report**.

    ![Screenshot of the Teams usage report in the Teams admin center with callouts.](../media/teams-reports-teams-usage-with-callouts1.png "Screenshot of the Teams usage report in the Teams admin center with callouts")

## Interpret the report

|Callout |Description  |
|--------|-------------|
|**1**   |The Teams usage activity report can be viewed for trends over the last 7 days, 30 or 90 days. |
|**2**   |Each report has a date for when this report was generated. The reports usually reflect a 24 to 48 hour latency from time of activity. |
|**3**   |<ul><li>The X axis on the chart is the selected date range for the report.</li> <li> The Y axis is the count of active items or activity.</li> </ul>Hover over the dot representing an item or activity on a given date to see the number of instances of that item or activity on that given date.|
|**4**   |You can filter what you see on the chart by clicking an item in the legend. For example, click  **Total active users**, **Teams & Channels active users**,  **Active channels**, or **Messages** to see only the info related to each one. Changing this selection doesn’t change the information in the table. |
|**5**   |The table gives you a breakdown of usage by team. <ul><li>**Team name** is the display name of the team. You can click the team name to go to the team's settings page in the Microsoft Teams admin center. </li> <li>**Privacy** refers to whether the team is a private team or public team.</li> <li>**Active users** is the number of active users in the team in the specified time period.</li><li>**Guests** is the number of guests in the team in the specified time period.</li> <li>**Active channels** is the number of channels that have at least one active user in the specified time period.</li> <li>**Post Messages** is the number of all the post messages in channels in the specified time period.</li> <li>**Reply messages** is the number  of all the reply messages in channels in the specified time period.</li> <li>**Meetings organized** is the number of scheduled and ad hoc meetings a user organized during the specified time period. </li><li>**Urgent messages** is the number  of all the urgent messages in the specified time period.</li><li>**Reactions** is the number  of all the reactions to messages in the specified time period.</li><li>**Mentions** is the number of all the mentions used in messages in the specified time period.</li><li>**Channel messages** is the number of unique messages that the team's users posted in a team chats during the specified time period.</li> </li> </ul>Note that if a team no longer exists, the name is displayed as "--" in the table. <br><br>To see the information that you want in the table, make sure to add the columns to the table. |
|**6**   |Select **Edit columns** to add or remove columns in the table.|
|**7**   |You can export the report to a CSV file for offline analysis. Click **Export to Excel**, and then on the **Downloads** tab, click **Download** to download the report when it's ready.<br><br>![Screenshot of the Downloads tab showing exported reports to download.](../media/teams-reports-export-to-csv.png)|
|**8** |Time series data points in the graph show different usage metrics aggregated at tenant|
|**9** |Tabular data represented different usage metrics aggregated per team|

[!INCLUDE [teams-reports-definitions](../includes/teams-reports-definitions.md)]

## Related topics

- [Teams analytics and reporting](teams-reporting-reference.md)
