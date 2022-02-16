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

The Virtual Visits usage report in the Microsoft Teams admin center gives you an overview of Teams Virtual Visits activity in your organization. You can view detailed activity for virtual appointments scheduled through the [Bookings app](../expand-teams-across-your-org/bookings-virtual-visits.md) and the [Microsoft Teams Electronic Health Records (EHR) connector](../expand-teams-across-your-org/healthcare/teams-in-hc.md#virtual-visits-and-electronic-healthcare-record-ehr-integration). To learn more about Virtual Visits, see [Virtual Visits with Teams](../expand-teams-across-your-org/virtual-visits.md).

To view the report, you must be a global admin, Teams admin, or Virtual Visits admin.

The report contains the following tabs. The information you’ll see in the report depends on whether you have a license for the Bookings app, the Teams EHR connector, or both.

|Tab |Description  |
|---------|---------|
|**[Virtual Visits](#virtual-visits)**     |Shows the total number of Virtual Visits, with a breakdown of the number of visits scheduled using the Bookings app and Teams EHR-integrated meetings conducted from your EHR system.         |
|**[Duration](#duration)**     |Shows the average duration of visits and average lobby wait time of attendees.         |
|**[Bookings](#bookings)**     |Shows the number of visits scheduled through the Bookings app.         |
|**[EHR](#ehr)**     |Shows the number of Teams EHR-integrated visits conducted from your EHR system..         |  

Use this report to gain insight into Virtual Visits activity and trends in your organization. The information can help you evaluate, track, and improve Virtual Visits adoption and the attendee experience. For example, you can determine whether sending SMS notifications to attendees before appointments reduces the number of no shows.

## View the Virtual Visits usage report

1. In the left navigation of the Microsoft Teams admin center, choose **Analytics & reports** > **Usage reports**. On the **View reports** tab, under **Report**, select **Virtual Visits usage**.
2. Under **Date range**, select a date range of 7 days, 30 days, or 90 days. Then, choose **Run report**.

> [!NOTE]
> By using these reports, you give Microsoft permission to collect data about Virtual Visits in your organization. For information about our data retention policies, see [Data retention, deletion, and destruction in Microsoft 365](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview).

## Interpret the report

### Virtual Visits

The graphs you'll see here depend on whether you have a license for the Bookings app, the Teams EHR connector, or both. To learn more, see [Manage the Bookings app](../bookings-app-admin.md), and [Integration into Cerner EHR](../expand-teams-across-your-org/healthcare/ehr-admin-cerner.md) or [Integration into Epic EHR](../expand-teams-across-your-org/healthcare/ehr-admin.md).

:::image type="content" source="../media/virtual-visits-usage-report-virtual-visits.png" alt-text="Screenshot of the Virtual Visits tab of the Virtual Visits usage report showing numbered callouts." lightbox="../media/virtual-visits-usage-report-virtual-visits.png":::

|Callout |Description  |
|--------|-------------|
|**1**   |Each report has a date for when the report was generated. The reports usually reflect a 24 to 48-hour latency from time of activity. |
|**2**   |The X axis is the selected date range for the report. The Y axis is the number of visits.<br>Hover over the dot on a given date to see the number of visits on that date.|
|**3**   |You can filter what you see on the chart by selecting an item in the legend. For example, select **Total Bookings Virtual Visits** or **Total EHR Virtual Visits** to see only the info related to each one. Changing this selection doesn’t change the information in the table. |
|**4**   |The table gives you detailed information about each visit that took place during the selected date range. <ul><li>**Start time (UTC)** is the date and time when both a staff member and participant are in the meeting or when the first activity happened in the meeting.  </li> <li>**Meeting ID** is the unique ID of the meeting.</li> <li>**Lobby wait time** is the time between when a participant first joins the lobby to when that same participant or a different participant is admitted to the meeting by a staff member.</li><li>**Duration** is the time difference between the start time and when the last person leaves the meeting. If both a staff member and a participant didn’t join the meeting, duration shows as 0 (zero).</li> <li>**Status** shows the meeting status. <ul><li>**Completed**: If one or more staff members and participants join the meeting and the meeting has ended. Or, if one or more participants join the meeting and the meeting has ended.</li> <li> **No show**: If one staff member joins the meeting but no other people join, and the meeting has ended. </li></ul> </li> <li>**Meeting type** indicates whether the virtual appointment was scheduled through the Bookings app or the Teams EHR connector.</li> <li>**Attendees** is the total number of staff members and participants in the meeting.</li> <li>**SMS sent** indicates whether an SMS notification was sent to attendees. </li> </li> </ul> |
|**5**   |Select **Edit columns** to add or remove columns in the table. To see the information that you want in the table, make sure to add the columns to the table.|
|**6**   |You can export the report to a CSV file for offline analysis. Select **Export to Excel**, and then on the **Downloads** tab, choose **Download** to download the report when it's ready.|

### Duration

:::image type="content" source="../media/virtual-visits-usage-report-duration.png" alt-text="Screenshot of the Virtual Visits tab of the Virtual Visits usage report showing numbered callouts." lightbox="../media/virtual-visits-usage-report-duration.png":::

|Callout |Description  |
|--------|-------------|
|**1**   |Each report has a date for when the report was generated. The reports usually reflect a 24 to 48-hour latency from time of activity. |
|**2**   |The X axis is the selected date range for the report. The Y axis is the number of minutes.<br>Hover over the dot on a given date to see the average visit duration or average lobby wait time for a given date.  |
|**3**   |You can filter what you see on the chart by selecting an item in the legend. For example, select **Average Virtual Visit duration** or **Average lobby wait time** to see only the info related to each one. Changing this selection doesn’t change the information in the table. |
|**4**   |The table gives you detailed information about each visit that took place during the selected date range. <ul><li>**Start time (UTC)** is the date and time when both a staff member and participant are in the meeting or when the first activity happened in the meeting.  </li> <li>**Meeting ID** is the unique ID of the meeting.</li> <li>**Lobby wait time** is the time between when a participant first joins the lobby to when that same participant or a different participant is admitted to the meeting by a staff member.</li><li>**Duration** is the time difference between the start time and when the last person leaves the meeting. If both a staff member and a participant didn’t join the meeting, duration shows as 0 (zero).</li> <li>**Status** shows the meeting status. <ul><li>**Completed**: If one or more staff members and participants join the meeting and the meeting has ended. Or, if one or more participants join the meeting and the meeting has ended.</li> <li> **No show**: If one staff member joins the meeting but no other people join, and the meeting has ended. </li></ul> </li> <li>**Meeting type** indicates whether the virtual appointment was scheduled through the Bookings app or the Teams EHR connector.</li> <li>**Attendees** is the total number of staff members and participants in the meeting.</li> <li>**SMS sent** indicates whether an SMS notification was sent to attendees. </li> </li> </ul>|
|**5**   |Select **Edit columns** to add or remove columns in the table. To see the information that you want in the table, make sure to add the columns to the table.|
|**6**   |You can export the report to a CSV file for offline analysis. Select **Export to Excel**, and then on the **Downloads** tab, choose **Download** to download the report when it's ready.|
### Bookings

You'll see this tab if you have a license that includes the Bookings app. To learn more, see [Manage the Bookings app](../bookings-app-admin.md).

:::image type="content" source="../media/virtual-visits-usage-report-bookings.png" alt-text="Screenshot of the Bookings tab of the Virtual Visits usage report showing numbered callouts." lightbox="../media/virtual-visits-usage-report-bookings.png":::

|Callout |Description  |
|--------|-------------|
|**1**   |Each report has a date for when the report was generated. The reports usually reflect a 24 to 48-hour latency from time of activity. |
|**2**   |The X axis is the selected date range for the report. The Y axis is the number of Bookings visits.<br>Hover over the dot on a given date to see the number of Bookings visits that occurred on that date.|
|**3**   |The table gives you detailed information about each visit that took place during the selected date range. <ul><li>**Start time (UTC)** is the date and time when both a staff member and participant are in the meeting or when the first activity happened in the meeting.  </li> <li>**Meeting ID** is the unique ID of the meeting.</li> <li>**Lobby wait time** is the time between when a participant first joins the lobby to when that same participant or a different participant is admitted to the meeting by a staff member.</li><li>**Duration** is the time difference between the start time and when the last person leaves the meeting. If both a staff member and a participant didn’t join the meeting, duration shows as 0 (zero).</li> <li>**Status** shows the meeting status. <ul><li>**Completed**: If one or more staff members and participants join the meeting and the meeting has ended. Or, if one or more participants join the meeting and the meeting has ended.</li> <li> **No show**: If one staff member joins the meeting but no other people join, and the meeting has ended. </li></ul> </li> <li>**Meeting type** indicates whether the virtual appointment was scheduled through the Bookings app or the Teams EHR connector.</li> <li>**Attendees** is the total number of staff members and participants in the meeting.</li> <li>**SMS sent** indicates whether an SMS notification was sent to attendees. </li> </li> </ul>|
|**4**   |Select **Edit columns** to add or remove columns in the table. To see the information that you want in the table, make sure to add the columns to the table.|
|**5**   |You can export the report to a CSV file for offline analysis. Select **Export to Excel**, and then on the **Downloads** tab, choose **Download** to download the report when it's ready.|
### EHR

You'll see this tab if you have a license that includes the Teams EHR connector. To learn more, see [Integration into Cerner EHR](../expand-teams-across-your-org/healthcare/ehr-admin-cerner.md) or [Integration into Epic EHR](../expand-teams-across-your-org/healthcare/ehr-admin.md).

:::image type="content" source="../media/virtual-visits-usage-report-ehr.png" alt-text="Screenshot of the EHR tab of the Virtual Visits usage report showing numbered callouts." lightbox="../media/virtual-visits-usage-report-ehr.png":::

|Callout |Description  |
|--------|-------------|
|**1**   |Each report has a date for when the report was generated. The reports usually reflect a 24 to 48-hour latency from time of activity. |
|**2**   |The X axis is the selected date range for the report. The Y axis is the number of EHR visits.<br>Hover over the dot on a given date to see the number of EHR visits on that date.|
|**3**   |The table gives you detailed information about each visit that took place during the selected date range. <ul><li>**Start time (UTC)** is the date and time when both a staff member and participant are in the meeting or when the first activity happened in the meeting.  </li> <li>**Meeting ID** is the unique ID of the meeting.</li> <li>**Lobby wait time** is the time between when a participant first joins the lobby to when that same participant or a different participant is admitted to the meeting by a staff member.</li><li>**Duration** is the time difference between the start time and when the last person leaves the meeting. If both a staff member and a participant didn’t join the meeting, duration shows as 0 (zero).</li> <li>**Status** shows the meeting status. <ul><li>**Completed**: If one or more staff members and participants join the meeting and the meeting has ended. Or, if one or more participants join the meeting and the meeting has ended.</li> <li> **No show**: If one staff member joins the meeting but no other people join, and the meeting has ended. </li></ul> </li> <li>**Meeting type** indicates whether the virtual appointment was scheduled through the Bookings app or the Teams EHR connector.</li> <li>**Attendees** is the total number of staff members and participants in the meeting.</li> <li>**SMS sent** indicates whether an SMS notification was sent to attendees. </li> </li> </ul>|
|**4**   |Select **Edit columns** to add or remove columns in the table. To see the information that you want in the table, make sure to add the columns to the table.|
|**5**   |You can export the report to a CSV file for offline analysis. Select **Export to Excel**, and then on the **Downloads** tab, choose **Download** to download the report when it's ready.|

> [!NOTE]
> We’re working on a new Teams app for Virtual Visits reporting. With this app, non-admin users such as business decision makers can view Virtual Visits reports directly from within Teams. If your organization would like to participate in private preview of the app, [reach out us](mailto:).

## Related articles

- [Virtual Visits with Teams](../expand-teams-across-your-org/virtual-visits.md)
- [Teams analytics and reporting](teams-reporting-reference.md)
