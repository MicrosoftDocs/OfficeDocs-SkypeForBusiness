---
title: "Top Failures Report in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 438942e2-580a-4b67-9d42-f116111fb26a
description: "Summary: Learn about the Top Failures Report in Skype for Business Server."
---

# Top Failures Report in Skype for Business Server
 
**Summary:** Learn about the Top Failures Report in Skype for Business Server.
  
The Top Failures Report provides a look at the most-commonly reported failures and their trends over time. Failures are based on a combination of the following two metrics:
  
- **Diagnostic ID**. Unique identifier (in the form of an ms-diagnostics header) that is attached to a SIP message. Diagnostic IDs provide information useful in troubleshooting call-related problems.
    
- **Response code**. Response codes are used in SIP communication sessions to respond to SIP requests. For example, suppose Ken sends the INVITE request to Pilar Ackerman (that is, suppose Ken Myer calls Pilar Ackerman). If Pilar answers, her phone will send the response code 200 (OK), letting Ken's phone know that Pilar has answered. The Top Failures Report only includes response codes that were sent in response to a call failure; Skype for Business Server does not keep track of all the response codes issued during the course of a call.
    
Information is reported not only for the total number of sessions where a failure occurred but also for the total number of users who were impacted by the failure.
  
## Accessing the Top Failures Report

The Top Failures Report is accessed from the Monitoring Reports home page. Clicking the Reported sessions metric will take you to the [Failure Distribution Report in Skype for Business Server](failure-distribution-report.md).
  
## Making the Best Use of the Top Failures Report

The Top Failures Report is unusual in one regard: it allows you to filter on as many as 5 diagnostic IDs at once. (Typically you can only filter on one item - such as one user SIP address - at a time.) To filter on multiple diagnostic IDs, simply enter each ID in the Diagnostic IDs box, separating the IDs by using commas. (If you want to, you can leave a blank space after each comma.) For example:
  
1011, 2412, 1033, 52116, 1008
  
Do that, and only failed calls that reported at least one of those five diagnostic IDs will be displayed.
  
If you hold your mouse over a Response code you'll see a tooltip that tells you what the Response code in question means. For example, if you hold the mouse over the Response code 486 you'll see this message:
  
Busy Here.
  
## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the Top Failures Report enables you to filter the returned data based on such things as the activity type (peer-to-peer session or conferencing session) or by the SIP response code that accompanied the failed session. You can also choose how data should be grouped. In this case, usages are grouped by hour, day, week, or month.
  
The following table lists the filters that you can use with the Top Failures Report.
  
**Top Failures Report Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date/time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date/time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Activity type** <br/> | Type of activity. Select one of the following: <br/>  [All] <br/>  Peer-to-peer <br/>  Conference <br/> |
|**Modality** <br/> |At this time the only option available is **[All]**.  <br/> |
|**Pool** <br/> |Fully qualified domain name (FQDN) of the Registrar pool or Edge Server. You can either select an individual pool or click **[All]** to view data for all the pools. This drop-down list is automatically populated for you based on the records in the database. <br/> |
|**Category** <br/> | Type of failure experienced. Select one of the following: <br/>  Both expected and unexpected failure <br/>  Unexpected failure <br/>  An "expected failure" is a failure that is expected to happen. For example, if a user has set his or her status to Do Not Disturb you would expect any call to that user to fail. An "unexpected failure" is a failure that occurs in what would appear to be an otherwise healthy system. For example, a call should not be terminated if the caller is placed on hold. If that occurs, that would be flagged as an unexpected failure. <br/> |
|**Response code** <br/> |SIP response code sent when the conference failed. Enter the entire response code For example:  <br/> 400  <br/> |
|**Diagnostic ID** <br/> |Unique identifier (in the form of an ms-diagnostics header) attached to a SIP message that often provides information useful in troubleshooting errors. Diagnostics headers are optional (it is possible to have SIP sessions that do not include these headers), and diagnostic IDs are reported only for sessions that experienced problems of some kind.  <br/> |
   
## Metrics

The following table lists the information provided in the Top Failures Report.
  
**Top Failures Report Metrics**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Rank** <br/> |Yes  <br/> |Relative rank based on the number of reported sessions.  <br/> |
|**Reported sessions** <br/> |Yes  <br/> |Total number of failed sessions based on diagnostic ID and SIP response code.  <br/> |
|**Users impacted** <br/> |Yes  <br/> |Total number of users affected by the failed session.  <br/> |
|**Failure information** <br/> |No  <br/> |Detailed information about the failure, including diagnostic ID, SIP response code, and description of why the session failed.  <br/> |
|**Trend in the past** <br/> |No  <br/> |Graphs failed sessions over time.  <br/> |
   

