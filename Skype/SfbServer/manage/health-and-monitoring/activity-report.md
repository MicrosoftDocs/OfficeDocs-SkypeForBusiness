---
title: "Conference Activity Report in Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 22ddb509-af16-4fc8-9b98-6f58caa6f37e
description: "Summary: Learn about the Conference Activity Report used in Skype for Business Server."
---

# Conference Activity Report in Skype for Business Server
 
**Summary:** Learn about the Conference Activity Report used in Skype for Business Server.
  
The Conference Activity Report makes it easy for you to answer questions like these: how many conferences are being held each day, and when are those conferences being held? Information like this is useful not only in its own right, but also as a troubleshooting tool. For example, suppose users are complaining that the network seems particularly slow in the middle of the day. A quick glance at the Conference Activity reports might suggest one possible reason: far more conferences are being scheduled between the hours of 10:00 AM and 2:00 PM then at any other time.
  
If the slow network is causing problems, you can encourage users to reschedule some of their conferences during the less-heavily trafficked times of the day.
  
## Accessing the Conference Activity Report

The Conference Activity Report is accessed from the [Conference Summary Report in Skype for Business Server](conference-summary-report.md) by clicking either one of the following metrics:
  
- Total conferences
    
- Total participants
    
## Making the Best Use of the Conference Activity Report

By default the Conference Activity Report shows you the total number of conferences for the specified time period (for example, the total number of conferences per day, or the total number of conferences per hour of the day). However, you can also choose to display the total number of participants for that time period or the total number of participant minutes. To do that, click the Show/Hide Parameters button to display the filtering options, and then select one of the following from the Report by dropdown list:
  
- Participant count
    
- Participant minutes
    
- Conference count
    
## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. The following table lists the filters that you can use with the Conference Activity Report.
  
**Conference Activity Report Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date/time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date/time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Interval** <br/> | Time interval. Select any of the following: <br/>  Hourly (a maximum of 25 hours can be displayed) <br/>  Daily (a maximum of 31 days can be displayed) <br/>  Weekly (a maximum of 12 weeks can be displayed) <br/>  Monthly (a maximum of 12 months can be displayed) <br/>  If the start and end dates exceed the maximum number of values allowed for the selected interval, only the maximum number of values (starting from the start date) is displayed. For example, if you select the Daily interval with a start date of 7/7/2015 and an end date of 2/28/2015, data is displayed for the days 8/7/2015 12:00 AM to 9/7/2015 12:00 AM (that is, a total of 31 days' worth of data). <br/> |
|**Report by** <br/> | Indicates the values to be used in the report. You can select one of the following: <br/>  Participant Count <br/>  Participant Minutes <br/>  Conference Count <br/> |
   
## Metrics for Conferences by Pool

The following table lists the information in the Conference Activity Report for each pool.
  
**Metrics for Conferences by Pool**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Pool** <br/> |No  <br/> |Name of the Registrar pool or Edge Server used in the conference.  <br/> |
|**Date/Time** <br/> |No  <br/> |Date and time when the conference was held.  <br/> |
|**Total** <br/> |No  <br/> |Total participant count, total participant minutes, or total conference count.  <br/> |
   
## Metrics for Conferences by Server Type

The following table lists the information in the Conference Activity Report for each type of server.
  
**Metrics for Conferences by Server Type**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Conferencing server type** <br/> |No  <br/> | Type of server used in the conference, typically one of the following: <br/>  Web Conferencing Server <br/>  IM Conferencing Server <br/>  Telephony Conferencing Server <br/>  AV Conferencing Server <br/>  Application Sharing <br/> |
|**Date/Time** <br/> |No  <br/> |Date and time when the conference was held.  <br/> |
|**Total** <br/> |No  <br/> |Total participant count, total participant minutes, or total conference count.  <br/> |
   

