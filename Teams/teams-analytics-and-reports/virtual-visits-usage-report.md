---
title: Microsoft Teams virtual visits usage report
author: LanaChin
ms.author: v-lanachin
manager: samanro
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: 
f1.keywords:
- NOCSH
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
description: Learn how to use the Virtual visits usage report in the Microsoft Teams admin center to get an overview of virtual visits activity in your organization.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---
# Microsoft Teams virtual visits report

The virtual visits usage report in the Microsoft Teams admin center gives you an overview of virtual visits  activity in your organization. You can view detailed activity for virtual appointments scheduled through the [Bookings app](../expand-teams-across-your-org/bookings-virtual-visits.md) and the [Teams Electronic Health Records (EHR) connector](../expand-teams-across-your-org/healthcare/teams-in-hc.md#virtual-visits-and-electronic-healthcare-record-ehr-integration).

## View the virtual visits usage report

1. In the left navigation of the Microsoft Teams admin center, choose **Analytics & reports** > **Usage reports**. On the **View reports** tab, under **Report**, select **Virtual visits usage**.
2. Under **Date range**, select a predefined date range or set a custom range, and then choose **Run report**.

    [Placeholder for screenshot, with callouts]

## Interpret the report

### Virtual visits

|Callout |Description  |
|--------|-------------|
|**1**   |The report can be viewed for trends over the last 7 days, 30 days, 90 days, or a custom date range that you set. |
|**2**   |Each report has a date for when the report was generated. The reports usually reflect a 24 to 48 hour latency from time of activity. |
|**3**   |<ul><li>The X axis is the selected date range for the report.</li> <li> The Y axis is the total number of virtual visits on the selected time period.</li> </ul>Hover over the dot on a given date to see the total virtual visits on that date.|
|**4**   |You can filter what you see on the chart by selecting an item in the legend. For example, select **Total Bookings virtual visits** or **Total EHR virtual visits** to see only the info related to each one. Changing this selection doesn’t change the information in the table. |
|**5**   |The table gives you a breakdown of usage by type of virtual visit. <ul><li>**Start time (UTC)** is the when  </li> <li>**Meeting ID** refers to whether the team is a private team or public team.</li> <li>**Lobby wait time** is the average wait time (in minutes) that attendees wait in the lobby before being admitted to the meeting.</li><li>**Duration** is the length of time between when .</li> <li>**Status** is the number of channels that have at least one active user in the specified time period.</li> <li>**Meeting type** is whether the meeting is scheduled through the Bookings app or the Teams EHR connector.</li> <li>**Attendees** is the total number of participants in the meeting.</li> <li>**Calendar name** is the number of scheduled and ad hoc meetings a user organized during the specified time period. </li><li>**SMS sent** is the number  of all the urgent messages in the specified time period.</li><li>**Reactions** is the number  of all the reactions to messages in the specified time period.</li><li>**Mentions** is the number of all the mentions used in messages in the specified time period.</li><li>**Channel messages** is the number of unique messages that the team's users posted in a team chats during the specified time period.</li> </li> </ul>Note that if a user account no longer exists in Azure AD, the user name is displayed as "--" in the table. <br><br>To see the information that you want in the table, make sure to add the columns to the table. |
|**6**   |Select **Edit columns** to add or remove columns in the table.|
|**7**   |You can export the report to a CSV file for offline analysis. Click **Export to Excel**, and then on the **Downloads** tab, click **Download** to download the report when it's ready.<br><br>![Screenshot of the Downloads tab showing exported reports to download.](../media/teams-reports-export-to-csv.png)|


### Bookings

|Callout |Description  |
|--------|-------------|
|**1**   |The report can be viewed for trends over the last 7 days, 30 or 90 days. |
|**2**   |Each report has a date for when this report was generated. The reports usually reflect a 24 to 48 hour latency from time of activity. |
|**3**   |<ul><li>The X axis on the chart is the selected date range for the report.</li> <li> The Y axis is the count of active items or activity.</li> </ul>Hover over the dot representing an item or activity on a given date to see the number of instances of that item or activity on that given date.|
|**4**   |You can filter what you see on the chart by clicking an item in the legend. For example, click  **Total active users**, **Teams & Channels active users**,  **Active channels**, or **Messages** to see only the info related to each one. Changing this selection doesn’t change the information in the table. |
|**5**   |The table gives you a breakdown of usage by team. <ul><li>**Team name** is the display name of the team. You can click the team name to go to the team's settings page in the Microsoft Teams admin center. </li> <li>**Privacy** refers to whether the team is a private team or public team.</li> <li>**Active users** is the number of active users in the team in the specified time period.</li><li>**Guests** is the number of guests in the team in the specified time period.</li> <li>**Active channels** is the number of channels that have at least one active user in the specified time period.</li> <li>**Post Messages** is the number of all the post messages in channels in the specified time period.</li> <li>**Reply messages** is the number  of all the reply messages in channels in the specified time period.</li> <li>**Meetings organized** is the number of scheduled and ad hoc meetings a user organized during the specified time period. </li><li>**Urgent messages** is the number  of all the urgent messages in the specified time period.</li><li>**Reactions** is the number  of all the reactions to messages in the specified time period.</li><li>**Mentions** is the number of all the mentions used in messages in the specified time period.</li><li>**Channel messages** is the number of unique messages that the team's users posted in a team chats during the specified time period.</li> </li> </ul>Note that if a user account no longer exists in Azure AD, the user name is displayed as "--" in the table. <br><br>To see the information that you want in the table, make sure to add the columns to the table. |
|**6**   |Select **Edit columns** to add or remove columns in the table.|
|**7**   |You can export the report to a CSV file for offline analysis. Click **Export to Excel**, and then on the **Downloads** tab, click **Download** to download the report when it's ready.<br><br>![Screenshot of the Downloads tab showing exported reports to download.](../media/teams-reports-export-to-csv.png)|
|**8** |Time series data points in the graph show different usage metrics aggregated at tenant|
|**9** |Tabular data represented different usage metrics aggregated per team|

### EHR

|Callout |Description  |
|--------|-------------|
|**1**   |The report can be viewed for trends over the last 7 days, 30 or 90 days. |
|**2**   |Each report has a date for when this report was generated. The reports usually reflect a 24 to 48 hour latency from time of activity. |
|**3**   |<ul><li>The X axis on the chart is the selected date range for the report.</li> <li> The Y axis is the count of active items or activity.</li> </ul>Hover over the dot representing an item or activity on a given date to see the number of instances of that item or activity on that given date.|
|**4**   |You can filter what you see on the chart by clicking an item in the legend. For example, click  **Total active users**, **Teams & Channels active users**,  **Active channels**, or **Messages** to see only the info related to each one. Changing this selection doesn’t change the information in the table. |
|**5**   |The table gives you a breakdown of usage by team. <ul><li>**Team name** is the display name of the team. You can click the team name to go to the team's settings page in the Microsoft Teams admin center. </li> <li>**Privacy** refers to whether the team is a private team or public team.</li> <li>**Active users** is the number of active users in the team in the specified time period.</li><li>**Guests** is the number of guests in the team in the specified time period.</li> <li>**Active channels** is the number of channels that have at least one active user in the specified time period.</li> <li>**Post Messages** is the number of all the post messages in channels in the specified time period.</li> <li>**Reply messages** is the number  of all the reply messages in channels in the specified time period.</li> <li>**Meetings organized** is the number of scheduled and ad hoc meetings a user organized during the specified time period. </li><li>**Urgent messages** is the number  of all the urgent messages in the specified time period.</li><li>**Reactions** is the number  of all the reactions to messages in the specified time period.</li><li>**Mentions** is the number of all the mentions used in messages in the specified time period.</li><li>**Channel messages** is the number of unique messages that the team's users posted in a team chats during the specified time period.</li> </li> </ul>Note that if a user account no longer exists in Azure AD, the user name is displayed as "--" in the table. <br><br>To see the information that you want in the table, make sure to add the columns to the table. |
|**6**   |Select **Edit columns** to add or remove columns in the table.|
|**7**   |You can export the report to a CSV file for offline analysis. Click **Export to Excel**, and then on the **Downloads** tab, click **Download** to download the report when it's ready.<br><br>![Screenshot of the Downloads tab showing exported reports to download.](../media/teams-reports-export-to-csv.png)|
|**8** |Time series data points in the graph show different usage metrics aggregated at tenant|
|**9** |Tabular data represented different usage metrics aggregated per team|

## Duration

|Callout |Description  |
|--------|-------------|
|**1**   |The report can be viewed for trends over the last 7 days, 30 or 90 days. |
|**2**   |Each report has a date for when this report was generated. The reports usually reflect a 24 to 48 hour latency from time of activity. |
|**3**   |<ul><li>The X axis on the chart is the selected date range for the report.</li> <li> The Y axis is the count of active items or activity.</li> </ul>Hover over the dot representing an item or activity on a given date to see the number of instances of that item or activity on that given date.|
|**4**   |You can filter what you see on the chart by clicking an item in the legend. For example, click  **Total active users**, **Teams & Channels active users**,  **Active channels**, or **Messages** to see only the info related to each one. Changing this selection doesn’t change the information in the table. |
|**5**   |The table gives you a breakdown of usage by team. <ul><li>**Team name** is the display name of the team. You can click the team name to go to the team's settings page in the Microsoft Teams admin center. </li> <li>**Privacy** refers to whether the team is a private team or public team.</li> <li>**Active users** is the number of active users in the team in the specified time period.</li><li>**Guests** is the number of guests in the team in the specified time period.</li> <li>**Active channels** is the number of channels that have at least one active user in the specified time period.</li> <li>**Post Messages** is the number of all the post messages in channels in the specified time period.</li> <li>**Reply messages** is the number  of all the reply messages in channels in the specified time period.</li> <li>**Meetings organized** is the number of scheduled and ad hoc meetings a user organized during the specified time period. </li><li>**Urgent messages** is the number  of all the urgent messages in the specified time period.</li><li>**Reactions** is the number  of all the reactions to messages in the specified time period.</li><li>**Mentions** is the number of all the mentions used in messages in the specified time period.</li><li>**Channel messages** is the number of unique messages that the team's users posted in a team chats during the specified time period.</li> </li> </ul>Note that if a user account no longer exists in Azure AD, the user name is displayed as "--" in the table. <br><br>To see the information that you want in the table, make sure to add the columns to the table. |
|**6**   |Select **Edit columns** to add or remove columns in the table.|
|**7**   |You can export the report to a CSV file for offline analysis. Click **Export to Excel**, and then on the **Downloads** tab, click **Download** to download the report when it's ready.<br><br>![Screenshot of the Downloads tab showing exported reports to download.](../media/teams-reports-export-to-csv.png)|
|**8** |Time series data points in the graph show different usage metrics aggregated at tenant|
|**9** |Tabular data represented different usage metrics aggregated per team|

## No shows

|Callout |Description  |
|--------|-------------|
|**1**   |The report can be viewed for trends over the last 7 days, 30 or 90 days. |
|**2**   |Each report has a date for when this report was generated. The reports usually reflect a 24 to 48 hour latency from time of activity. |
|**3**   |<ul><li>The X axis on the chart is the selected date range for the report.</li> <li> The Y axis is the count of active items or activity.</li> </ul>Hover over the dot representing an item or activity on a given date to see the number of instances of that item or activity on that given date.|
|**4**   |You can filter what you see on the chart by clicking an item in the legend. For example, click  **Total active users**, **Teams & Channels active users**,  **Active channels**, or **Messages** to see only the info related to each one. Changing this selection doesn’t change the information in the table. |
|**5**   |The table gives you a breakdown of usage by team. <ul><li>**Team name** is the display name of the team. You can click the team name to go to the team's settings page in the Microsoft Teams admin center. </li> <li>**Privacy** refers to whether the team is a private team or public team.</li> <li>**Active users** is the number of active users in the team in the specified time period.</li><li>**Guests** is the number of guests in the team in the specified time period.</li> <li>**Active channels** is the number of channels that have at least one active user in the specified time period.</li> <li>**Post Messages** is the number of all the post messages in channels in the specified time period.</li> <li>**Reply messages** is the number  of all the reply messages in channels in the specified time period.</li> <li>**Meetings organized** is the number of scheduled and ad hoc meetings a user organized during the specified time period. </li><li>**Urgent messages** is the number  of all the urgent messages in the specified time period.</li><li>**Reactions** is the number  of all the reactions to messages in the specified time period.</li><li>**Mentions** is the number of all the mentions used in messages in the specified time period.</li><li>**Channel messages** is the number of unique messages that the team's users posted in a team chats during the specified time period.</li> </li> </ul>Note that if a user account no longer exists in Azure AD, the user name is displayed as "--" in the table. <br><br>To see the information that you want in the table, make sure to add the columns to the table. |
|**6**   |Select **Edit columns** to add or remove columns in the table.|
|**7**   |You can export the report to a CSV file for offline analysis. Click **Export to Excel**, and then on the **Downloads** tab, click **Download** to download the report when it's ready.<br><br>![Screenshot of the Downloads tab showing exported reports to download.](../media/teams-reports-export-to-csv.png)|
|**8** |Time series data points in the graph show different usage metrics aggregated at tenant|
|**9** |Tabular data represented different usage metrics aggregated per team|

## Related topics

- [Teams analytics and reporting](teams-reporting-reference.md)
