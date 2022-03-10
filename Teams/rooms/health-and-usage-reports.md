---
title: Health and Usage Reports
author: donnah007 
ms.author: v-donnahill
manager: serdars
ms.date: 03/10/2022
ms.reviewer:  
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Reporting node data for health and usage of reports
f1keywords: 
---

# Health

The reporting node contains data for the health and usage of your Microsoft Managed Rooms. The overview surfaces tenant wide health trends of your rooms. In the health tab of reports, all rooms are listed with their corresponding health score and number of meetings impacted by a ticket. Room usage based on the calendar information is visible under the “Usage” tab.

Navigate to the health report for all rooms by going to Reports, then click on the “Health” tab. 

![A screenshot of a Reports health percentage](../media/health-and-usage-001.png)

The health score is a metric designed to surface rooms that are most likely to cause end-user frustration. A room can either be healthy or unhealthy for a given day. It is considered unhealthy if a ticket or many tickets impacted the room for more than 20 total minutes during non-maintenance hours (5AM -9PM machine local time). For example, if a ticket is opened at 5:00AM but closed at 5:15AM, the room is still considered healthy. But, if a second ticket occurred from 09:00AM to 9:10AM, the room would then be considered unhealthy for the day. Similarly, if a ticket occurred from 5:00AM to 5:21AM, it is considered unhealthy for the day.

> [!NOTE]
> Health for the day is aggregated once a day at 12:00 AM UTC time. For customers near the international date line, health aggregation may occur near the middle of the workday.

> [!NOTE]
> Rooms that are onboarding are hidden for the list of rooms in the Health tab and do not count towards the average health of the tenant.

Clicking on a room listed in this view will display more details. 

The bar graph displays the number of tickets on each day. Tickets opened on that respective day are shown in blue, while orange represents on-going tickets opened prior to the respective day. Clicking on a day on the graph will filter the pie-chart and table to the relevant tickets. To reverse the filter, navigate with the breadcrumbs or click on the graph.

Categorization of tickets are represented in the donut chart. Interacting with this will filter the timeline graph and table. To reverse the filter, navigate with the breadcrumbs or click on the graph.



![A screenshot of active tickets bar graph](../media/health-and-usage-002.png)

## Navigating reports
![A screenshot of active tickets pie chart](../media/health-and-usage-003.png)

The overview section provides graphical representations of important aspects of meeting room management. The charts will change depending on the time span selected or group selected. To change the time span, click the drop-down menu.

![A screenshot of a dropdown menu to choose days](../media/health-and-usage-004.png)

To change the group, click the group selection drop down in the banner.

![A screenshot of the banner menu auto-generated](../media/health-and-usage-005.png)


### Tickets by category

This donut shows you the total tickets raised for the selected timespan and group (default: 7 days, all groups). Tickets are represented in their major categories: Audio, Display, Peripherals, Connectivity, Versioning and Customer reported.

![A screenshot of pie chart tickets by category](../media/health-and-usage-006.png)

A flyout for the detailed view for tickets of that category will be shown if it is clicked. 

![A screenshot of tickets and versioning side by side](../media/health-and-usage-007.png)

In the flyout, it is possible to filter the list of tickets by the subcategory by clicking on the respective part of the donut. 

![A screenshot tickets by subcategory automatically generated](../media/health-and-usage-008.png)

To navigate back, either click on the donut or click on the breadcrumb at the top left.

To navigate to a specific ticket in this list view, click on the link under the “Support ticket column”
### Ticket history

The ticket history graph shows a comparison of incidents assigned to you or Microsoft over the specified time period. 

> [!NOTE]
> If a ticket changes owner in a day, whoever owns the assignment for the majority of that day will have the ticket counted towards them. Ex. If you assign the ticket to Microsoft early in the day, the ticket counts towards “Assigned to Microsoft” for the day.

![A screen shot of Tickets history by different periods](../media/health-and-usage-009.png)
### Health history

This graph shows the average health (definition in Health section) for all the rooms in the tenant as well as the average health for all MMR customers on a day-to-day basis. It is possible to look at the average health for up to 90 days.

![A screenshot of rooms health and average health](../media/health-and-usage-010.png)

Two tables  show the most reliable and least reliable rooms based on health. For the full list view, select Health, then sort the list by the Health column.

# Usage

Navigate to the Usage report for all rooms by selecting **Reports**, then **Usage**.

![A screenshot of all rooms' usage by health](../media/health-and-usage-011.png)

The headlines provide a few insights:

- Total rooms in your tenant
- How many do not have any booked meetings, either offline or online
- Percentage of utilization of rooms across the tenant
- Total number of booked meetings through exchange
- Percentage of booked meetings that included a Skype or Teams link

Usage is calculated at the end of each day at midnight (00:00) local time of the meeting room device.

Utilization is calculated based on the total booked meeting time for that day divided by 8 hours.

The circles are filled in quarter intervals only, with the following thresholds:

- Less than 15% -> Empty
- Between 15% and 40% -> ¼ fill 
- Between 40% and 60% -> ½ fill
- Between 60% and 80% -> ¾ fill
- Over 80% -> Whole 
## Usage details of a room
 
Clicking on a room in the list view will prompt a flyout with more in-depth information. Under the Utilization tab of the flyout is a graph showing hours of usage of the last five business days. For each day there are two bars: blue – representing booked meeting time – and purple – for scheduled time of Teams/Skype enabled meetings. At the bottom, the average meeting bookings and duration for the past 5 business days is calculated.

![A screenshot utilization by hours per day](../media/health-and-usage-012.png)

The “Nearby” tab displays up to 5 other rooms that are located within 100m, approximately. This view facilitates comparisons to rooms in the same building. It is important to note that the distance measurement is horizontal and based on location data from the device in the room. Vertical distance is not accounted for in this metric.

![A screenshot of rooms' usage within given radius](../media/health-and-usage-013.png)

The settings tab displays the metadata of the room such as the hardware information, device settings, BIOS information, app settings, and location.