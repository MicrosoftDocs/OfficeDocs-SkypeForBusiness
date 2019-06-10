---
title: Microsoft Teams PSTN usage report
author: LanaChin    
ms.author: v-lanac
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: svemu
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
description: Learn how to use the Teams PSTN usage report in the Microsoft Teams admin center to get an overview of calling and audio conferencing usage in your organization.
appliesto: 
- Microsoft Teams
---
# Microsoft Teams PSTN usage report

The Teams PSTN usage report in the Microsoft Teams admin center gives you an overview of PSTN calling and audio conferencing activity in your organization. You can drill into the report for more granular information about the activities of each user. You can see the number of minutes spent in inbound and outbound PSTN calls and the cost of these calls. Use this information to gain insight into calling and audio conferencing usage in your organization and help you to investigate, plan, and make business decisions. 

![Screen shot of the PSTN usage report in the admin center](../media/teams-reports-teams-usage.png "Screen shot of the PSTN usage report in the Microsoft Teams admin center")

## View the report

1. Go to the Microsoft Teams admin center, in the left navigation, click **Analytics & reports**, and then under **Report**, select **PSTN usage**. 
2. Under **Date range**, select a range, and then click **Run report**.

## Interpret the report

![Screen shot of the PSTN usage report in the admin center](../media/teams-reports-teams-usage-with-callouts.png "Screen shot of the PSTN usage report in the Microsoft Teams admin center with numbered callouts")

|Callout |Description  |
|--------|-------------|
|**1**   |The Teams usage activity report can be viewed for trends over the last 7 days or 28 days. |
|**2**   |Each report has a date for when this report was generated. The reports usually reflect a 24 to 48 hour latency from time of activity. |
|**3**   |<ul><li>The X axis on the chart is the selected date range for the report.</li> <li> The Y axis is the count of active items or activity.</li> </ul>Hover over the dot representing an item or activity on a given date to see the number of instances of that item or activity on that given date.|
|**4**   |You can filter what you see on the chart by clicking an item in the legend. For example, click  **Total active users**, **Teams & Channels active users**,  **Active channels**, or **Messages** to see only the info related to each one. Changing this selection doesn’t change the information in the table. |
|**5**   |The table gives you a breakdown of usage by team. <ul><li>**Team name** is the display name of the team. You can click the team name to go to the team's settings page in the Microsoft Teams admin center. </li> <li>**Privacy** refers to whether the team is a private team or public team.</li> <li>**Active users** is the number of active users in the team in the specified time period.</li><li>**Guests** is the number of guests in the team in the specified time period.</li> </li> </ul>To see the information that you want in the table, make sure to add the columns to the table. |
|**6**   |Select **Edit columns** to add or remove columns in the table.|
|**7**   |You can export the report to a CSV file for offline analysis. Click **Export to Excel**, and then on the **Downloads** tab, click **Download** to download the report when it's ready.<br>![Screen shot of the Downloads tab showing exported reports to download](../media/teams-reports-export-to-csv.png)|

## Related topics
- [Teams analytics and reporting](teams-reporting-reference.md)
- [Teams user activity report](user-activity-report.md)
- [Teams device usage report](device-usage-report.md)
