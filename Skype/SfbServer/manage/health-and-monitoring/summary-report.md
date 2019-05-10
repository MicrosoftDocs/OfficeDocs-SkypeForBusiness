---
title: "Call Diagnostic Summary Report in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 9091de56-13e6-440e-9353-f57c10c906fe
description: "Summary: Learn about the Call Diagnostic Summary Report used in Skype for Business Server."
---

# Call Diagnostic Summary Report in Skype for Business Server
 
**Summary:** Learn about the Call Diagnostic Summary Report used in Skype for Business Server.
  
The Call Diagnostic Summary Report provides an overall look at failed peer-to-peer and conferencing sessions. The report shows the overall failure rate for both types of sessions, and further breaks the failure information down by session modality type:
  
- Instant messaging
    
- Application sharing
    
- File transfer
    
- Audio
    
- Video
    
## Accessing the Call Diagnostic Summary Report

The Call Diagnostic Summary Report is accessed from the Monitoring Reports Home page. From the Call Diagnostic Summary Report you can access the [Peer-to-Peer Activity Diagnostic Report in Skype for Business Server](peer-to-peer-activity-diagnostic-report.md) by clicking the Failure rate metric under the Peer-to-Peer Session Summary section of the report. You can also access the [Conference Diagnostic Report in Skype for Business Server](conference-diagnostic-report.md) by clicking any of the following conference metrics:
  
- Overall session failure rate
    
- Focus failure rate
    
- MCU failure rate
    
## Making the Best Use of the Call Diagnostic Summary Report

The Call Diagnostic Summary Report includes graphs that compare failure rates for the various modalities used in Skype for Business Server. The columns in these graphs are actually hotlinks; for example, if you click the Instant messaging column for peer-to-peer sessions, you'll drill down to an instance of the [Peer-to-Peer Activity Diagnostic Report in Skype for Business Server](peer-to-peer-activity-diagnostic-report.md), a report that provides additional details about all the instant messaging sessions included in the Call Diagnostic Summary Report.
  
## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the Call Diagnostic Summary Report enables you to filter on such things as the Registrar pool or Edge Server used in the session. You can also choose how data should be grouped. In this case, calls are grouped by hour, day, week, or month.
  
The following table lists the filters that you can use with the Call Diagnostic Summary Report.
  
**Call Diagnostic Summary Report Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date/time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date/time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Interval** <br/> | Time interval. Select one of the following: <br/>  Hourly (a maximum of 25 hours can be displayed) <br/>  Daily (a maximum of 31 days can be displayed) <br/>  Weekly (a maximum of 12 weeks can be displayed) <br/>  Monthly (a maximum of 12 months can be displayed) <br/>  If the start and end dates exceed the maximum number of values allowed for the selected interval, only the maximum number of values (starting from the start date) is displayed. For example, if you select the Daily interval with a start date of 7/7/2015 and an end date of 2/28/2015, data is displayed for the days 8/7/2015 12:00 AM to 9/7/2015 12:00 AM (that is, a total of 31 days' worth of data). <br/> |
|**Pool** <br/> |Fully qualified domain name (FQDN) of the Registrar pool or Edge Server. You can either select an individual pool or click **[All]** to view data for all the pools. This drop-down list is automatically populated for you based on the records in the database. <br/> |
   
## Metrics for Peer-to-Peer Sessions

The following table lists the information provided in the Call Diagnostic Summary Report for peer-to-peer sessions (that is, sessions involving just two participants).
  
**Metrics for Peer-to-Peer Sessions**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Total sessions** <br/> |No  <br/> |Total number of peer-to-peer sessions conducted.  <br/> |
|**Failure rate** <br/> |No  <br/> |Percentage of peer-to-peer sessions that failed. When you click this item, the report shows the Peer-to-Peer Activity Diagnostic report, which displays more detailed information about the failed peer-to-peer sessions.  <br/> |
   
## Metrics for Conferencing Sessions

The following table lists the information provided in the Call Diagnostic Report for conferencing sessions (that is, sessions involving three or more participants).
  
**Metrics for Conferencing Sessions**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Total conferences** <br/> |No  <br/> |Total number of conferences conducted.  <br/> |
|**Total conference sessions** <br/> |No  <br/> |Total number of conferencing sessions conducted.  <br/> |
|**Overall session failure rate** <br/> |No  <br/> |Percentage of the total conferencing sessions that failed.  <br/> |
|**Focus sessions** <br/> |No  <br/> |Total number of Focus-based conferencing sessions that failed.  <br/> |
|**Focus failure rate** <br/> |No  <br/> |Percentage of the Focus-based conferencing sessions that failed.  <br/> |
|**MCU sessions** <br/> |No  <br/> |Total number of conferencing server-based (formerly known as Multipoint Control Unit or MCU) conferences that failed.  <br/> |
|**MCU failure rate** <br/> |No  <br/> |Percentage of the conferencing server-based (formerly known as Multipoint Control Unit or MCU) conferences that failed.  <br/> |
   

