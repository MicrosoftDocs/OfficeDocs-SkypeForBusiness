---
title: "Conference Diagnostic Report in Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e9edc23c-8ce8-4ab8-8786-9d22e1e51e14
description: "Summary: Learn about the Conference Diagnostic Report used in Skype for Business Server."
---

# Conference Diagnostic Report in Skype for Business Server
 
**Summary:** Learn about the Conference Diagnostic Report used in Skype for Business Server.
  
The Conference Diagnostic Report provides information about the success and failure of all conferencing sessions. Note that Skype for Business Server distinguishes between different kinds of failure:
  
- **Expected failure**. An expected failure is typically a failure only in the most technical sense. For example, suppose someone starts a conference but hangs up before anyone can join. Technically that's a failure: the conference was initiated, but not completed. However, that's a failure that you would expect to happen: if the organizer cancels the conference before anyone can join then you would not expect that conference to be completed.
    
- **Unexpected failure**. An unexpected error is exactly what the name implies: an error that, based on the circumstances, you would not expect to occur. For example, suppose a conference could not be held because the organizer's meeting policy could not be retrieved. That's an unexpected error: after all, you should always be able to retrieve a user's meeting policy.
    
Note that the Success, Expected failure, and Unexpected failure metrics might not add up to the Total sessions metric. For example, you might see the following values in the Report:
  
|**Successes**|**Expected failures**|**Unexpected failures**|**Total sessions**|
|:-----|:-----|:-----|:-----|
|2024  <br/> |469  <br/> |16  <br/> |2521  <br/> |
   
If you add 2024 + 469 + 16 you get a total of 2,509 sessions and yet, the Total sessions column shows a total of 2,521 sessions. The "missing" 12 sessions for are sessions that the system was unable to categorize as successful or unsuccessful. That will sometimes be the case when a third-party product introduces a new diagnostic code that is unfamiliar to Monitoring Server. When that happens, calls made using that product, and reporting that diagnostic code, cannot always be categorized as being a Success, an Expected failure, or an Unexpected failure.
  
## Accessing the Conference Diagnostic Report

The Conference Diagnostic Report is accessed from the Monitoring Reports home page. You can access the [Failure Distribution Report in Skype for Business Server](failure-distribution-report.md) by clicking either of the following metrics:
  
- Unexpected failure volume
    
- Expected failure volume
    
## Making the Best Use of the Conference Diagnostic Report

The Conference Diagnostic Report includes a series of graphs. Each of the columns shown in the graph is actually a hyperlink. If you click a column, you'll drill down to the [Failure Distribution Report in Skype for Business Server](failure-distribution-report.md) for that time period and that conference type.
  
## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the Conference Diagnostic Report enables you to filter on such things as the type of conference being conducted (for example, a Focus-based conference) or by the Edge Server used in the conference. You can also choose how data should be grouped. In this case, conferences are grouped by hour, day, week, or month.
  
The following table lists the filters that you can use with the Conference Diagnostic Report.
  
**Conference Diagnostic Report Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date/time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date/time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Interval** <br/> | Time interval. Select one of the following: <br/>  Hourly (a maximum of 25 hours can be displayed) <br/>  Daily (a maximum of 31 days can be displayed) <br/>  Weekly (a maximum of 12 weeks can be displayed) <br/>  Monthly (a maximum of 12 months can be displayed) <br/>  If the start and end dates exceed the maximum number of values allowed for the selected interval, only the maximum number of values (starting from the start date) is displayed. For example, if you select the Daily interval with a start date of 7/7/2015 and an end date of 2/28/2015, data is displayed for the days 8/7/2015 12:00 AM to 9/7/2015 12:00 AM (that is, a total of 31 days' worth of data). <br/> |
|**Pool** <br/> |Fully qualified domain name (FQDN) of the Registrar pool or Edge Server. You can either select an individual pool or click **[All]** to view data for all the pools. This drop-down list is automatically populated for you based on the records in the database. <br/> |
|**Conference sessions** <br/> | Indicates the type of conferencing session. Select one of the following: <br/>  [All] <br/>  Focus sessions <br/>  All MCU sessions <br/>  IM conferencing <br/>  Application sharing <br/>  A/V conferencing <br/> |
   
## Metrics

The following table lists the information provided in the Conference Diagnostic Report for each type of conferencing session.
  
**Conference Diagnostic Report Metrics**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Success volume** <br/> |No  <br/> |Total number of successful conferences.  <br/> |
|**Success percentage** <br/> |No  <br/> |Percentage of conferences that completed with significant problems. Calculated by dividing the Success volume by the Total sessions.  <br/> |
|**Expected failure volume** <br/> |No  <br/> |Total number of conferences where an "expected failure" occurred.  <br/> An expected failure is a failure that is expected to happen. For example, if a user has set his or her status to Do Not Disturb you would expect any call to that user to fail.  <br/> |
|**Expected failure percentage** <br/> |No  <br/> |Percentage of conferences that experienced an expected error. Calculated by dividing the Expected failure volume by the Total sessions.  <br/> |
|**Unexpected failure volume** <br/> |No  <br/> |Total number of conferences where an "unexpected failure" occurred.  <br/> An unexpected failure is a failure that occurs in what would appear to be an otherwise healthy system. For example, a call should not be terminated if the caller is placed on hold. If that occurs, that would be flagged as an unexpected failure.  <br/> |
|**Unexpected failure percentage** <br/> |No  <br/> |Percentage of conferences that experienced an unexpected error. Calculated by dividing the Unexpected failure volume by the Total sessions.  <br/> |
|**Total sessions** <br/> |No  <br/> |Total number of conferences, including successful conferences, failed conferences (both expected failures and unexpected failures), and uncategorized conferences.  <br/> |
   

