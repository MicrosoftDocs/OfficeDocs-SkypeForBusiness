---
title: Microsoft Teams webinar usage report
author: wlibebe
ms.author: wlibebe
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: justle
ms.date: 08/16/2023
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
description: Learn how to use the Teams webinar in the Microsoft Teams admin center to get an overview of Teams webinar in your organization.
appliesto: 
  - Microsoft Teams
---
# Microsoft Teams webinar usage report

The Teams webinar usage report in the Microsoft Teams admin center shows you the activity overview for webinars created in your organization. You can view usage information, including the event title, event ID, start time, end time, event access type, and the names of the organizers, presenters, and co-organizers for each event. You can gain insight into usage trends and see who in your organization schedules and produces webinars.

## View the webinar usage report

1. In the left navigation of the Microsoft Teams admin center, select **Analytics & reports** > **Usage reports**. On the **View reports** tab, under **Report**, select **Webinar usage reports**.
2. Under **Date range**, select a predefined range or set a custom range. You can set a range to show data up to a year, six months before and after the current date.
3. Under **Organizer**, you can choose to show only webinars organized by a specific user.
4. Select **Run report**.  

   :::image type="content" alt-text="Screenshot of the Teams webinar usage report in the Teams admin center with callouts." source="../media/webinar-report-small.png" lightbox="../media/webinar-report-expand.png":::

## Interpret the report

|Callout |Description  |
|--------|-------------|
|**1**   |The Teams webinar usage report can be viewed for trends over the last 7 days, 28 days, or a custom date range that you set. |
|**2**   |Each report has a date for when it was generated. The report reflects near real time activity when the page is refreshed. |
|**3**   |<ul><li>The X axis on the chart is the selected date range for the report.</li> <li> The Y axis is the total view count.</li> </ul>Hover over the dot on a given date to see the number of views across all webinars on that date.|
|**4**   |The table gives you a breakdown of each webinar. <ul><li>**Event ID** is the unique ID of the webinar</li> <li>**Event Title** is the name the organizer created for the webinar.</li><li>**Start Time(UTC)** refers to the start date and time of the webinar.</li><li>**End Time(UTC)** refers to the end date and time of the webinar.</li><li>**Organizer** is the name of the webinar organizer.</li> <li>**Co-organizer** is the name of the webinar co-organizer.</li></li><li>**Presenters** is the name of the webinar presenter.</li></li><li>**Event access type** specifies whether the webinar access was in org or private.</li></li> </ul>If a user account no longer exists in Azure AD, the user name is displayed as "--" in the table. <br><br>

> [!NOTE]
> We show a maximum of up to 100 webinars that match the current report criteria. To see more webinars, apply date filters to reduce the list size.

## Related topics

- [Teams analytics and reporting](teams-reporting-reference.md)
- [Set up webinars](../set-up-webinars.md)
