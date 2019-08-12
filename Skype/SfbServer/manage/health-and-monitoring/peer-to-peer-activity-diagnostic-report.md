---
title: "Peer-to-Peer Activity Diagnostic Report in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 025e8ab4-2e64-4a6b-8f52-caf756a5cac3
description: "Summary: Learn about the Peer-to-Peer Activity Diagnostic Report in Skype for Business Server."
---

# Peer-to-Peer Activity Diagnostic Report in Skype for Business Server
 
**Summary:** Learn about the Peer-to-Peer Activity Diagnostic Report in Skype for Business Server.
  
The Peer-to-Peer Activity Diagnostic Report provides information about the success and failure of your peer-to-peer communication sessions. Note that Skype for Business Server distinguishes between different kinds of failure:
  
- **Expected failure**. An expected failure is typically a failure only in the most technical sense. For example, suppose you call someone, but he or she is away from the office and is unable to answer the phone. Because the call was not answered, the call is technically considered a failure. On the other hand, this was an expected failure: Skype for Business Server does not expect you to answer the phone if you're not available to answer the phone. Likewise, an expected failure will occur if you attempt to send an instant message to a user who is offline, or is logged on only to a phone that does not support instant messaging.
    
- **Unexpected failure**. An unexpected error is exactly what the name implies: an error that, based on the circumstances, you would not expect to occur. For example, suppose you call someone and that person is available to answer the call; however, when Skype for Business Server tries to route your call to voice mail the call fails because connectivity to Exchange Unified Messaging has been lost. That's an unexpected error: you would expect that calls could always be routed to voice mail. As a general rule, unexpected failures are true failures: they are problems that likely cannot be remedied through user education or similar measures.
    
Note that the Success, Expected failure, and Unexpected failure metrics might not add up to the Total sessions metric. For example, in the preceding illustration, we have the following values:
  
|**Successes**|**Expected failures**|**Unexpected failures**|**Total sessions**|
|:-----|:-----|:-----|:-----|
|2024  <br/> |469  <br/> |16  <br/> |2521  <br/> |
   
If you add 2024 + 469 + 16 you get a total of 2,509 sessions, yet the Total sessions column shows a total of 2,521 sessions. The "missing" 12 sessions are sessions that the system was unable to categorize as successful or unsuccessful. That will sometimes be the case when a third-party product introduces a new diagnostic code that is unfamiliar to Skype for Business Server. When that happens, calls made using that product, and reporting that diagnostic code, cannot always be categorized as being a Success, an Expected failure, or an Unexpected failure.
  
## Accessing the Peer-to-Peer Activity Diagnostic Report

The Peer-to-Peer Diagnostic Report is accessed from the Monitoring Reports home page. You can access the [Failure Distribution Report in Skype for Business Server](failure-distribution-report.md) by clicking either of the following metrics:
  
- Unexpected failure volume
    
- Expected failure volume
    
## Making the Best Use of the Peer-to-Peer Activity Diagnostic Report

There are a number of ways you can filter the Peer-to-Peer Activity Diagnostic Report but, by default, those filtering options are hidden from view. To view the filtering options available to you, click the Show/Hide Parameters button in the upper right-hand corner of the report window. Once you do that the filtering options will be available for use.
  
## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the Peer-to-Peer Activity Diagnostic Report enables you to filter on such things as the session modality (for example, instant messaging, file transfer, or application sharing). You can also choose how data should be grouped. In this case, calls are grouped by hour, day, week, or month.
  
The following table lists the filters that you can use with the Peer-to-Peer Activity Diagnostic Report.
  
**Peer-to-Peer Activity Diagnostic Report Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date/time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date/time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Interval** <br/> | Time interval. Select one of the following: <br/>  Hourly (a maximum of 25 hours can be displayed) <br/>  Daily (a maximum of 31 days can be displayed) <br/>  Weekly (a maximum of 12 weeks can be displayed) <br/>  Monthly (a maximum of 12 months can be displayed) <br/>  If the start and end dates exceed the maximum number of values allowed for the selected interval, only the maximum number of values (starting from the start date) is displayed. For example, if you select the Daily interval with a start date of 7/7/2015 and an end date of 2/28/2015, data is displayed for the days 8/7/2015 12:00 AM to 9/7/2015 12:00 AM (that is, a total of 31 days' worth of data). <br/> |
|**Pool** <br/> |Fully qualified domain name (FQDN) of the Registrar pool or Edge Server. You can either select an individual pool or click **[All]** to view data for all the pools. This drop-down list is automatically populated for you based on the records in the database. <br/> |
|**Modality** <br/> | Indicates the type of communication activity that took place. Select one of the following: <br/>  [All] <br/>  Instant messaging <br/>  File transfer <br/>  Application sharing <br/>  Audio <br/>  Video <br/> |
   
## Metrics (per modality)

The following table lists the information provided in the Peer-to-Peer Activity Diagnostic Report for each modality.
  
**Metrics (per modality)**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Success volume** <br/> |No  <br/> |Total number of successful peer-to-peer sessions.  <br/> |
|**Success percentage** <br/> |No  <br/> |Percentage of peer-to-peer sessions that completed with significant problems. Calculated by dividing the Success volume by the Total sessions.  <br/> |
|**Expected failure volume** <br/> |No  <br/> |Total number of sessions where an "expected failure" occurred.  <br/> An expected failure is a failure that is expected to happen. For example, if a user has set his or her status to Do Not Disturb you would expect any call to that user to fail.  <br/> |
|**Expected failure percentage** <br/> |No  <br/> |Percentage of peer-to-peer sessions that experienced an expected error. Calculated by dividing the Expected failure volume by the Total sessions.  <br/> |
|**Unexpected failure volume** <br/> |No  <br/> |Total number of sessions where an "unexpected failure" occurred.  <br/> An unexpected failure is a failure that occurs in what would appear to be an otherwise healthy system. For example, a call should not be terminated if the caller is placed on hold. If that occurs, that would be flagged as an unexpected failure.  <br/> |
|**Unexpected failure percentage** <br/> |No  <br/> |Percentage of peer-to-peer sessions that experienced an unexpected error. Calculated by dividing the Unexpected failure volume by the Total sessions.  <br/> |
|**Total sessions** <br/> |No  <br/> |Total number of sessions, including successful sessions, failed sessions (both expected failures and unexpected failures), and uncategorized sessions.  <br/> |
   

