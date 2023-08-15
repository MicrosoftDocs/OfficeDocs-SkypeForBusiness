---
title: Microsoft Teams webinar usage report
author: wlibebe
ms.author: wlibebe
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: justle
ms.date: 08/15/2023
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
description: Learn how to use the Teams webinar in the Microsoft Teams admin center to get an overview of Teams webinar in your organization.
appliesto: 
  - Microsoft Teams
---
# Microsoft Teams webinar usage report

The Teams webinar usage report in the Microsoft Teams admin center shows you the activity overview for webinars created in your organization. You can view usage information, including event status, start time, views, and production type for each event. You can gain insight into usage trends and see who in your organization schedules, presents, and produces webinars.

## View the webinar usage report

1. In the left navigation of the Microsoft Teams admin center, select **Analytics & reports** > **Usage reports**. On the **View reports** tab, under **Report**, select **Webinar usage reports**.
2. Under **Date range**, select a predefined range or set a custom range. You can set a range to show data up to a year, six months before and after the current date.
3. Under **Organizer**, you can choose to show only webinars organized by a specific user.
4. Select **Run report**.  

   :::image type="content" alt-text="Screenshot of the Teams webinar usage report in the Teams admin center with callouts." source="../media/teams-live-event-usage-report-with-callouts.png" lightbox="../media/teams-live-event-usage-report-with-callouts.png":::

## Interpret the report

|Callout |Description  |
|--------|-------------|
|**1**   |The Teams webinar usage report can be viewed for trends over the last 7 days, 28 days, or a custom date range that you set. |
|**2**   |Each report has a date for when it was generated. The report reflects near real time activity when the page is refreshed. |
|**3**   |<ul><li>The X axis on the chart is the selected date range for the report.</li> <li> The Y axis is the total view count.</li> </ul>Hover over the dot on a given date to see the number of views across all webinars on that date.|
|**4**   |The table gives you a breakdown of each webinar. <ul><li>**Event** is the display name of the webinar. Select the event name to [get more details](#view-event-details) about the event. </li> <li>**Start Time** refers to the start date and time of the event.</li> <li>**Event Status** shows whether the event has taken place.  </li><li>**Organizer** is the name of the event organizer.</li> <li>**Presenters** are the names of the  event presenters.</li><li>**Producers** are the names of the event producers.</li><li>**Views** is the number of unique views after the event is completed.</li><li>**Recording** shows whether the recording setting is on or off.</li><li>**Production Type** shows whether the event is produced in Teams or by an external application or device.</li></li> </ul>If a user account no longer exists in Azure AD, the user name is displayed as "--" in the table. <br><br>To see the information that you want in the table, make sure to add the columns to the table. |
|**5**   |Select **Edit columns** to add or remove columns in the table.|

## Notes
We show a maximum of up to 100 webinars that match the current report criteria. To see more webinars, apply date filters to reduce the list size.

Anonymous presenters aren't included in the report.

Anybody who watches the recording of the event or the event on demand won't be included in the view count. 

## View event details

The webinar details page gives you a summary of the details of a webinar and lists all the files, including transcripts and recordings, associated with the event. Select a file name to view or download the file.

:::image type="content" alt-text="Screenshot showing details of a webinar." source="../media/teams-live-event-usage-report-event-detail.png" lightbox="../media/teams-live-event-usage-report-event-detail.png":::

If your organization uses Microsoft eCDN, advanced analytics can be viewed and exported from the [eCDN Dashboard](https://admin.ecdn.microsoft.com).  If your organization is enabled for [Hive](https://www.hivestreaming.com/partners/integration-partners/microsoft/) eCDN or [Kollective](https://kollective.com) eCDN, you can get more attendee analytics by clicking the partner report link.

## Related articles

- [Set up webinars](set-up-webinars.md)
