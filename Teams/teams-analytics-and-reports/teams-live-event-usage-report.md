---
title: Microsoft Teams live event usage report
author: LanaChin    
ms.author: v-lanac
manager: serdars
ms.date: 04/24/2019
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: svemu
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
description: Learn how to use the Teams live event usage report in the Microsoft Teams admin center to get an overview of Teams live events activity in your organization.
appliesto: 
- Microsoft Teams
---
# Microsoft Teams live event usage report

The Teams live event usage report in the Microsoft Teams admin center shows you the activity overview for live events held in your organization. You can view usage information, including event status, start time, views, and production type for each event. You can gain insight into usage trends and see who in your organization schedules, presents, and produces live events. 

![Screen shot of the Teams live event usage report in the Microsoft Teams admin center](../media/teams-reports-teams-usage.png "Screen shot of the Teams usage report in the Microsoft Teams admin center")

## View the report

1. Go to the Microsoft Teams admin center, in the left navigation, click **Analytics & reports**, and then under **Report**, select **Teams live event usage**.
2. Under **Date range**, select a predefined range or set a custom range. You can set a range to show  data up to a year, six months before and after the current date.
3. (Optional) Under **Organizer**, you can choose to show only live events organized by a specific user.
4. Click **Run report**.  

## Interpret the report

![Screen shot of the Teams live events report in the Microsoft Teams admin center](../media/teams-reports-teams-usage-with-callouts.png "Screen shot of the Teams live events usage report in the Microsoft Teams admin center with numbered callouts")

|Callout |Description  |
|--------|-------------|
|**1**   |The Teams live event report can be viewed for trends over the last 7 days, 28 days, or a custom date range that you set. |
|**2**   |Each report has a date for when it was generated. The reports usually reflect a 24 to 48 hour latency from time of activity. |
|**3**   |<ul><li>The X axis on the chart is the selected date range for the report.</li> <li> The Y axis is the total view count.</li> </ul>Hover over the dot on a given date to see the number of views across all live events on that given date.|
|**4**   |The table gives you a breakdown of each live event. <ul><li>**Event** is the display name of the live event. Click the the event name to go to the ??? page in the Microsoft Teams admin center. </li> <li>**Start Time** refers to the start date and time of the event.</li> <li>**Event Status** shows whether the event has taken place.  </li><li>**Organizer** is the name of the event organizer.</li> <li>**Presenters** are the names of the  event presenters.</li><li>**Producers** are the names of the event producers.</li><li>**Views** is the number of unique views.</li><li>**Recording** shows whether the recording setting is on or off.</li><li>**Production Type** shows whether the event is produced in Teams or by an external application or device.</li></li> </ul>To see the information that you want in the table, make sure to add the columns to the table. |
|**6**   |Select **Edit columns** to add or remove columns in the table.|
|**7**   |You can export the report to a CSV file for offline analysis. Click **Export to Excel**, and then on the **Downloads** tab, click **Download** to download the report when it's ready.<br>
??? Don't see this in my test tenant. Included it in case the feature will be added. <br>![Screen shot of the Downloads tab showing exported reports to download](../media/teams-reports-export-to-csv.png)|

## Related topics
- [Teams analytics and reporting](teams-reporting-reference.md)

