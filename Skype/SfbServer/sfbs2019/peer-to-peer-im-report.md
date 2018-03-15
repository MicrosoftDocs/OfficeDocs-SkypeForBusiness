---
title: "Peer-to-Peer IM Report in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 19ec0145-2398-437b-8989-f780c179b798
description: "In this articleAccessing the Peer-to-Peer IM ReportMaking the Best Use of the Peer-to-Peer IM ReportFiltersMetrics for Peer-to-Peer IM Session by PoolMetrics for Peer-to-Peer IM Session by Authentication Type"
---

# Peer-to-Peer IM Report in Lync Server 2013
[]
 **In this article**
  
[Accessing the Peer-to-Peer IM Report](#sectionSection0)
  
[Making the Best Use of the Peer-to-Peer IM Report](#sectionSection1)
  
[Filters](#sectionSection2)
  
[Metrics for Peer-to-Peer IM Session by Pool](#sectionSection3)
  
[Metrics for Peer-to-Peer IM Session by Authentication Type](#sectionSection4)
  
The Peer-to-Peer IM Report provides trend information about peer-to-peer instant messaging (IM) sessions, broken down by pool and by authentication type. The report can show either the total number of sessions held during the specified time period (for example, day-by-day or hour-by-hour), or it can show the total number of instant messages sent during that time period.
  
## Accessing the Peer-to-Peer IM Report
<a name="sectionSection0"> </a>

You can access the Peer-to-Peer IM Report only by opening the [Peer-to-Peer Activity Summary Report in Lync Server 2013](peer-to-peer-activity-summary-report.md) and then clicking either of the following metrics: 
  
- Total peer-to-peer IM sessions
    
- Total peer-to-peer IM messages
    
## Making the Best Use of the Peer-to-Peer IM Report
<a name="sectionSection1"> </a>

By default, the Peer-to-Peer IM Report shows you the message count per-hour (or day, depending on your settings). However, you can also choose to view the day by sessions per hour. To do that, click **Hide/Show Parameters** in the upper-right corner of the Reports window, and then click **Session Count** from the **Report by** list. 
  
## Filters
<a name="sectionSection2"> </a>

Filters provide a way for you to return a more finely targeted set of data or to view the returned data in different ways. The following table lists the filters that you can use with the Peer-to-Peer IM Report.
  
**Peer-to-Peer IM Report Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date and time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2012 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2012  <br/> To view by week or by month, enter a date that falls anywhere within the week or month (you do not have to enter the first day of the week or month):  <br/> 7/3/2012  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date and time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2012 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2012  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2012  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Interval** <br/> | Time interval. Select one of the following:  <br/>  Hourly (a maximum of 25 hours can be displayed)  <br/>  Daily (a maximum of 31 days can be displayed)  <br/>  Weekly (a maximum of 12 weeks can be displayed)  <br/>  Monthly (a maximum of 12 months can be displayed)  <br/>  If the start and end dates exceed the maximum number of values allowed for the selected interval then only the maximum number of values (starting from the start date) are displayed. For example, if you select the Daily interval with a start date of 7/7/2012 and an end date of 2/28/2012, data is displayed for the days 8/7/2012 12:00 AM to 9/7/2012 12:00 AM (that is, a total of 31 days' worth of data).  <br/> |
|**Report by** <br/> | Indicates the values to be used in the report. Select one of the following:  <br/>  Session count  <br/>  Message count  <br/> |
   
## Metrics for Peer-to-Peer IM Session by Pool
<a name="sectionSection3"> </a>

The following table lists the information provided in the Peer-to-Peer IM Report.
  
**Metrics for Peer-to-Peer IM Session by Pool**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Pool** <br/> |No  <br/> |Name of the Registrar pool or Edge Server.  <br/> |
|**Date/Time** <br/> |No  <br/> |Date and time that the sessions took place.  <br/> |
|**Total** <br/> |No  <br/> |Total number of sessions or total message count.  <br/> |
   
## Metrics for Peer-to-Peer IM Session by Authentication Type
<a name="sectionSection4"> </a>

The following table lists the information provided in the Peer-to-Peer IM Report for each type of authentication used by the participants in a peer-to-peer session.
  
**Metrics for Peer-to-Peer IM Session by Authentication Type**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Authentication type** <br/> |No  <br/> | Type of authentication used by the session participants. Values are typically one of the following:  <br/>  Enterprise  <br/>  Federated  <br/>  PIC  <br/> |
|**Date/Time** <br/> |No  <br/> |Date and time that the sessions took place.  <br/> |
|**Total** <br/> |No  <br/> |Total number of sessions or total message count.  <br/> |
   

