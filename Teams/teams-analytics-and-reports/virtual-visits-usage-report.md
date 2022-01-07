---
title: Microsoft Teams Virtual Visits usage report
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
description: Learn how to use the Virtual Visits usage report in the Microsoft Teams admin center to get an overview of Virtual Visits activity in your organization.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---
# Microsoft Teams Virtual Visits usage report

The Virtual Visits usage report in the Microsoft Teams admin center gives you an overview of Teams Virtual Visits activity in your organization. You can view detailed activity for virtual appointments scheduled through the [Bookings app](../expand-teams-across-your-org/bookings-virtual-visits.md) and the [Teams Electronic Health Records (EHR) connector](../expand-teams-across-your-org/healthcare/teams-in-hc.md#virtual-visits-and-electronic-healthcare-record-ehr-integration). To learn more about Virtual Visits, see [Virtual Visits with Teams](../expand-teams-across-your-org/virtual-visits.md).

The report contains the following tabs:

- [Virtual Visits](#virtual-visits): Shows the total number of Virtual Visits, and of these, the total number of Virtual Visits scheduled through the Bookings app and conducted from your EHR system through the Team EHR connector.
- [Duration](#duration): Shows the average duration of Virtual Visits and average lobby wait time.
- [Bookings](#bookings): Shows the total number of Virtual Visits scheduled through the Bookings app.
- [EHR](#ehr): Shows the total number of Virtual Visits conducted from your EHR system through the Teams EHR connector.

Use this report to gain insight into Virtual Visits usage in your organization. The information can help you evaluate, track, and improve Virtual Visits adoption and the attendee experience. For example, you can determine whether sending SMS notifications to attendees before appointments reduces the number of no shows.

## View the Virtual Visits usage report

1. In the left navigation of the Microsoft Teams admin center, choose **Analytics & reports** > **Usage reports**. On the **View reports** tab, under **Report**, select **Virtual Visits usage**.
2. Under **Date range**, select a date range. The report can be viewed for trends over the last 7 days, 30 days, or 90 days. Then, choose **Run report**.

## Interpret the report

### Virtual Visits

|Callout |Description  |
|--------|-------------|
|**1**   |Each report has a date for when the report was generated. The reports usually reflect a 24 to 48-hour latency from time of activity. |
|**2**   |The X axis is the selected date range for the report. The Y axis is the number of Virtual Visits.<br>Hover over the dot on a given date to see the number of Virtual Visits on that date.|
|**3**   |You can filter what you see on the chart by selecting an item in the legend. For example, select **Total Bookings Virtual Visits**, **Total EHR Virtual Visits**, or **Total Virtual Visits** to see only the info related to each one. Changing this selection doesn’t change the information in the table. |
|**4**   |The table gives you detailed information about each virtual appointment that occurred during the selected date range. <ul><li>**Start time (UTC)** is the date and time when both a staff member and attendee are in the meeting.  </li> <li>**Meeting ID** is the unique ID of the meeting.</li> <li>**Lobby wait time** is the time (in minutes) that the attendee waits in the lobby before being admitted to the meeting by a staff member.</li><li>**Duration** is the length of time between the start time and when the last person leaves the meeting.</li> <li>**Status** shows the virtual appointment status. <ul><li>Completed:</li> <li> No show:</li></ul> </li> <li>**Meeting type** indicates whether the virtual appointment was scheduled through the Bookings app or the Teams EHR connector.</li> <li>**Attendees** is the total number of participants in the meeting.</li> <li>**SMS sent** indicates whether an SMS notification was sent to attendees. </li> </li> </ul> |
|**5**   |Select **Edit columns** to add or remove columns in the table. To see the information that you want in the table, make sure to add the columns to the table.|
|**6**   |You can export the report to a CSV file for offline analysis. Select **Export to Excel**, and then on the **Downloads** tab, choose **Download** to download the report when it's ready.|

### Duration

|Callout |Description  |
|--------|-------------|
|**1**   |Each report has a date for when the report was generated. The reports usually reflect a 24 to 48-hour latency from time of activity. |
|**2**   |The X axis is the selected date range for the report. The Y axis is the number of minutes.<br>Hover over the dot on a given date to see the average duration of a virtual visit or average lobby wait time for a given date.  |
|**3**   |You can filter what you see on the chart by selecting an item in the legend. For example, select **Average virtual visit duration** or **Average lobby wait time** to see only the info related to each one. Changing this selection doesn’t change the information in the table. |
|**4**   |The table gives you detailed information about each virtual appointment that occurred during the selected date range. <ul><li>**Start time (UTC)** is the date and time when both a staff member and attendee are in the meeting.  </li> <li>**Meeting ID** is the unique ID of the meeting.</li> <li>**Lobby wait time** is the time (in minutes) that the attendee waits in the lobby before being admitted to the meeting by a staff member.</li><li>**Duration** is the length of time between the start time and when the last person leaves the meeting.</li> <li>**Status** shows the virtual appointment status. <ul><li>Completed:</li> <li> No show:</li></ul> </li> <li>**Meeting type** indicates whether the virtual appointment was scheduled through the Bookings app or the Teams EHR connector.</li> <li>**Attendees** is the total number of participants in the meeting.</li> <li>**SMS sent** indicates whether an SMS notification was sent to attendees. </li> </li> </ul> |
|**5**   |Select **Edit columns** to add or remove columns in the table. To see the information that you want in the table, make sure to add the columns to the table.|
|**6**   |You can export the report to a CSV file for offline analysis. Select **Export to Excel**, and then on the **Downloads** tab, choose **Download** to download the report when it's ready.|
### Bookings

|Callout |Description  |
|--------|-------------|
|**1**   |Each report has a date for when the report was generated. The reports usually reflect a 24 to 48-hour latency from time of activity. |
|**2**   |The X axis is the selected date range for the report. The Y axis is the number of Bookings Virtual Visits.<br>Hover over the dot on a given date to see the number of Bookings Virtual Visits that occurred on that date.|
|**3**   ||
|**4**   |The table gives you detailed information about each virtual appointment that occurred during the selected date range. <ul><li>**Start time (UTC)** is the date and time when both a staff member and attendee are in the meeting.  </li> <li>**Meeting ID** is the unique ID of the meeting.</li> <li>**Lobby wait time** is the time (in minutes) that the attendee waits in the lobby before being admitted to the meeting by a staff member.</li><li>**Duration** is the length of time between the start time and when the last person leaves the meeting.</li> <li>**Status** shows the virtual appointment status. <ul><li>Completed:</li> <li> No show:</li></ul> </li> <li>**Meeting type** indicates whether the virtual appointment was scheduled through the Bookings app or the Teams EHR connector.</li> <li>**Attendees** is the total number of participants in the meeting.</li> <li>**SMS sent** indicates whether an SMS notification was sent to attendees. </li> </li> </ul> |
|**5**   |Select **Edit columns** to add or remove columns in the table. To see the information that you want in the table, make sure to add the columns to the table.|
|**6**   |You can export the report to a CSV file for offline analysis. Select **Export to Excel**, and then on the **Downloads** tab, choose **Download** to download the report when it's ready.|
### EHR

|Callout |Description  |
|--------|-------------|
|**1**   |Each report has a date for when the report was generated. The reports usually reflect a 24 to 48-hour latency from time of activity. |
|**2**   |The X axis is the selected date range for the report. The Y axis is the number of EHR Virtual Visits.<br>Hover over the dot on a given date to see the number of EHR Virtual Visits on that date.|
|**3**   ||
|**4**   |The table gives you detailed information about each virtual appointment that occurred during the selected date range. <ul><li>**Start time (UTC)** is the date and time when both a staff member and attendee are in the meeting.  </li> <li>**Meeting ID** is the unique ID of the meeting.</li> <li>**Lobby wait time** is the time (in minutes) that the attendee waits in the lobby before being admitted to the meeting by a staff member.</li><li>**Duration** is the length of time between the start time and when the last person leaves the meeting.</li> <li>**Status** shows the virtual appointment status. <ul><li>Completed:</li> <li> No show:</li></ul> </li> <li>**Meeting type** indicates whether the virtual appointment was scheduled through the Bookings app or the Teams EHR connector.</li> <li>**Attendees** is the total number of participants in the meeting.</li> <li>**SMS sent** indicates whether an SMS notification was sent to attendees. </li> </li> </ul> |
|**5**   |Select **Edit columns** to add or remove columns in the table. To see the information that you want in the table, make sure to add the columns to the table.|
|**6**   |You can export the report to a CSV file for offline analysis. Select **Export to Excel**, and then on the **Downloads** tab, choose **Download** to download the report when it's ready.|
## Related articles

- [Teams analytics and reporting](teams-reporting-reference.md)
