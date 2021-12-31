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
description: Learn how to use the virtual visits usage report in the Microsoft Teams admin center to get an overview of virtual visits activity in your organization.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---
# Microsoft Teams virtual visits usage report

The virtual visits usage report in the Microsoft Teams admin center gives you an overview of virtual visits activity in your organization. You can view detailed activity for virtual appointments scheduled through the [Bookings app](../expand-teams-across-your-org/bookings-virtual-visits.md) and the [Teams Electronic Health Records (EHR) connector](../expand-teams-across-your-org/healthcare/teams-in-hc.md#virtual-visits-and-electronic-healthcare-record-ehr-integration).

- [Virtual visits](#virtual-visits)
- [Bookings](#bookings)
- [EHR](#ehr)
- [Duration](#duration)
- [No shows](#no-shows)

Use this report to gain insight into virtual visits usage in your organization. The information can help you to evaluate, track, and improve virtual visit adoption and the attendee experience.

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
|**5**   |The table gives you a breakdown of usage by type of virtual visit. <ul><li>**Start time (UTC)** is the when  </li> <li>**Meeting ID** is the unique ID of the meeting.</li> <li>**Lobby wait time** is the average wait time (in minutes) that attendees wait in the lobby before being admitted to the meeting.</li><li>**Duration** is the length of time between when .</li> <li>**Status** shows the virtual appointment status. <ul><li>Completed:</li> <li> No show:</li> <li> Cancelled:</li></ul> </li> <li>**Meeting type** indicates whether the virtual appointment was scheduled through the Bookings app or the Teams EHR connector.</li> <li>**Attendees** is the total number of participants in the meeting.</li> <li>**Calendar name** is the name of the virtual appointment in the calendar.  </li><li>**SMS sent** indicates whether an SMS notification was sent to attendees. </li><li>**TBD** </li><li>**TBD** </li><li>**TBD** </li> </li> </ul> <br><br>To see the information that you want in the table, make sure to add the columns to the table. |
|**6**   |Select **Edit columns** to add or remove columns in the table.|
|**7**   |You can export the report to a CSV file for offline analysis. Click **Export to Excel**, and then on the **Downloads** tab, click **Download** to download the report when it's ready.<br><br>![Screenshot of the Downloads tab showing exported reports to download.](../media/teams-reports-export-to-csv.png)|


### Bookings

|Callout |Description  |
|--------|-------------|
|**1**   |The report can be viewed for trends over the last 7 days, 30 days, 90 days, or a custom date range that you set. |
|**2**   |Each report has a date for when the report was generated. The reports usually reflect a 24 to 48 hour latency from time of activity. |
|**3**   |<ul><li>The X axis is the selected date range for the report.</li> <li> The Y axis is the total number of Bookings virtual visits on the selected time period.</li> </ul>Hover over the dot on a given date to see the total Bookings virtual visits on that date.|
|**4**   |You can filter what you see on the chart by selecting an item in the legend. For example, select **Total Bookings virtual visits** or **Total EHR virtual visits** to see only the info related to each one. Changing this selection doesn’t change the information in the table. |
|**5**   |The table gives you a breakdown of usage by type of virtual visit. <ul><li>**Start time (UTC)** is the when  </li> <li>**Meeting ID** is the unique ID of the meeting.</li> <li>**Lobby wait time** is the average wait time (in minutes) that attendees wait in the lobby before being admitted to the meeting.</li><li>**Duration** is the length of time between when .</li> <li>**Status** shows the virtual appointment status. <ul><li>Completed:</li> <li> No show:</li> <li> Cancelled:</li></ul> </li> <li>**Meeting type** indicates whether the virtual appointment was scheduled through the Bookings app or the Teams EHR connector.</li> <li>**Attendees** is the total number of participants in the meeting.</li> <li>**Calendar name** is the name of the virtual appointment in the calendar.  </li><li>**SMS sent** indicates whether an SMS notification was sent to attendees. </li><li>**TBD** </li><li>**TBD** </li><li>**TBD** </li> </li> </ul> To see the information that you want in the table, make sure to add the columns to the table. |
|**6**   |Select **Edit columns** to add or remove columns in the table.|
|**7**   |You can export the report to a CSV file for offline analysis. Click **Export to Excel**, and then on the **Downloads** tab, click **Download** to download the report when it's ready.<br><br>![Screenshot of the Downloads tab showing exported reports to download.](../media/teams-reports-export-to-csv.png)|
### EHR

|Callout |Description  |
|--------|-------------|
|**1**   |The report can be viewed for trends over the last 7 days, 30 days, 90 days, or a custom date range that you set. |
|**2**   |Each report has a date for when the report was generated. The reports usually reflect a 24 to 48 hour latency from time of activity. |
|**3**   |<ul><li>The X axis is the selected date range for the report.</li> <li> The Y axis is the total number of EHR virtual visits on the selected time period.</li> </ul>Hover over the dot on a given date to see the total EHR virtual visits on that date.|
|**4**   |You can filter what you see on the chart by selecting an item in the legend. For example, select **Total Bookings virtual visits** or **Total EHR virtual visits** to see only the info related to each one. Changing this selection doesn’t change the information in the table. |
|**5**   |The table gives you a breakdown of usage by type of virtual visit. <ul><li>**Start time (UTC)** is the when  </li> <li>**Meeting ID** is the unique ID of the meeting.</li> <li>**Lobby wait time** is the average wait time (in minutes) that attendees wait in the lobby before being admitted to the meeting.</li><li>**Duration** is the length of time between when .</li> <li>**Status** shows the virtual appointment status. <ul><li>Completed:</li> <li> No show:</li> <li> Cancelled:</li></ul> </li> <li>**Meeting type** indicates whether the virtual appointment was scheduled through the Bookings app or the Teams EHR connector.</li> <li>**Attendees** is the total number of participants in the meeting.</li> <li>**Calendar name** is the name of the virtual appointment in the calendar.  </li><li>**SMS sent** indicates whether an SMS notification was sent to attendees. </li><li>**TBD** </li><li>**TBD** </li><li>**TBD** </li> </li> </ul> To see the information that you want in the table, make sure to add the columns to the table. |
|**6**   |Select **Edit columns** to add or remove columns in the table.|
|**7**   |You can export the report to a CSV file for offline analysis. Click **Export to Excel**, and then on the **Downloads** tab, click **Download** to download the report when it's ready.<br><br>![Screenshot of the Downloads tab showing exported reports to download.](../media/teams-reports-export-to-csv.png)|

## Duration

|Callout |Description  |
|--------|-------------|
|**1**   |The report can be viewed for trends over the last 7 days, 30 days, 90 days, or a custom date range that you set. |
|**2**   |Each report has a date for when the report was generated. The reports usually reflect a 24 to 48 hour latency from time of activity. |
|**3**   |<ul><li>The X axis is the selected date range for the report.</li> <li> The Y axis is the total number of virtual visits on the selected time period.</li> </ul>Hover over the dot on a given date to see the total virtual visits on that date.|
|**4**   |You can filter what you see on the chart by selecting an item in the legend. For example, select **Total Bookings virtual visits** or **Total EHR virtual visits** to see only the info related to each one. Changing this selection doesn’t change the information in the table. |
|**5**   |The table gives you a breakdown of usage by type of virtual visit. <ul><li>**Start time (UTC)** is the when  </li> <li>**Meeting ID** is the unique ID of the meeting.</li> <li>**Lobby wait time** is the average wait time (in minutes) that attendees wait in the lobby before being admitted to the meeting.</li><li>**Duration** is the length of time between when .</li> <li>**Status** shows the virtual appointment status. <ul><li>Completed:</li> <li> No show:</li> <li> Cancelled:</li></ul> </li> <li>**Meeting type** indicates whether the virtual appointment was scheduled through the Bookings app or the Teams EHR connector.</li> <li>**Attendees** is the total number of participants in the meeting.</li> <li>**Calendar name** is the name of the virtual appointment in the calendar.  </li><li>**SMS sent** indicates whether an SMS notification was sent to attendees. </li><li>**TBD** </li><li>**TBD** </li><li>**TBD** </li> </li> </ul> To see the information that you want in the table, make sure to add the columns to the table. |
|**6**   |Select **Edit columns** to add or remove columns in the table.|
|**7**   |You can export the report to a CSV file for offline analysis. Click **Export to Excel**, and then on the **Downloads** tab, click **Download** to download the report when it's ready.<br><br>![Screenshot of the Downloads tab showing exported reports to download.](../media/teams-reports-export-to-csv.png)|

## No shows

|Callout |Description  |
|--------|-------------|
|**1**   |The report can be viewed for trends over the last 7 days, 30 days, 90 days, or a custom date range that you set. |
|**2**   |Each report has a date for when the report was generated. The reports usually reflect a 24 to 48 hour latency from time of activity. |
|**3**   |<ul><li>The X axis is the selected date range for the report.</li> <li> The Y axis is the total number of virtual visits on the selected time period.</li> </ul>Hover over the dot on a given date to see the total virtual visits on that date.|
|**4**   |You can filter what you see on the chart by selecting an item in the legend. For example, select **Total Bookings virtual visits** or **Total EHR virtual visits** to see only the info related to each one. Changing this selection doesn’t change the information in the table. |
|**5**   |The table gives you a breakdown of usage by type of virtual visit. <ul><li>**Start time (UTC)** is the when  </li> <li>**Meeting ID** is the unique ID of the meeting.</li> <li>**Lobby wait time** is the average wait time (in minutes) that attendees wait in the lobby before being admitted to the meeting.</li><li>**Duration** is the length of time between when .</li> <li>**Status** shows the meeting status. <ul><li>Completed:</li> <li> No show:</li> <li> Cancelled:</li></ul> </li> <li>**Meeting type** indicates whether the virtual appointment was scheduled through the Bookings app or the Teams EHR connector.</li> <li>**Attendees** is the total number of participants in the meeting.</li> <li>**Calendar name** is the name of the virtual appointment in the calendar.  </li><li>**SMS sent** indicates whether an SMS notification was sent to attendees. </li><li>**TBD** </li><li>**TBD** </li><li>**TBD** </li> </li> </ul> To see the information that you want in the table, make sure to add the columns to the table. |
|**6**   |Select **Edit columns** to add or remove columns in the table.|
|**7**   |You can export the report to a CSV file for offline analysis. Click **Export to Excel**, and then on the **Downloads** tab, click **Download** to download the report when it's ready.<br><br>![Screenshot of the Downloads tab showing exported reports to download.](../media/teams-reports-export-to-csv.png)|

## Related topics

- [Teams analytics and reporting](teams-reporting-reference.md)
