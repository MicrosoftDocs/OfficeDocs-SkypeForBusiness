---
title: "Conference Join Time Report in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e64dc89a-25e4-4cb8-bcb1-51712e69ba5a
description: "Summary: Learn about the Conference Join Time Summary Report in Skype for Business Server."
---

# Conference Join Time Report in Skype for Business Server
 
**Summary:** Learn about the Conference Join Time Summary Report in Skype for Business Server.
  
The Conference Join Time Summary enables you to determine how long it takes your users to join a conference. The report shows the average join time (in milliseconds), and also provides a breakdown that lets you know how many users were able to join a conference in 2 seconds or less, how many users required between 2 and 5 seconds to join the conference, and so on.
  
## Accessing the Conference Join Time Report

The Conference Join Time Report is accessed from the Monitoring Reports home page.
  
## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. The following table lists the filters that you can use with the Conference Join Time Report.
  
**Conference Join Time Report Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date/time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date/time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Interval** <br/> | Time interval. Select one of the following: <br/>  Hourly (a maximum of 25 hours can be displayed) <br/>  Daily (a maximum of 31 days can be displayed) <br/>  Weekly (a maximum of 12 weeks can be displayed) <br/>  Monthly (a maximum of 12 months can be displayed) <br/>  If the start and end dates exceed the maximum number of values allowed for the selected interval, only the maximum number of values (starting from the start date) is displayed. For example, if you select the Daily interval with a start date of 7/7/2015 and an end date of 2/28/2015, data is displayed for the days 8/7/2015 12:00 AM to 9/7/2015 12:00 AM (that is, a total of 31 days' worth of data). <br/> |
|**Pool** <br/> |Fully qualified domain name (FQDN) of the Registrar pool or Edge Server. You can either select an individual pool or click **[All]** to view data for all the pools. This drop-down list is automatically populated for you based on the records in the database. <br/> |
|**Conference sessions** <br/> | Type of session. Allowed values are: <br/>  [All] <br/>  Focus sessions (the Focus is the central policy and state manager for online meetings and coordinates all aspects of A conference <br/>  Application sharing <br/>  A/V conferencing <br/>  If you select [All], the total conference join time will be displayed at the top of the report. Note that these totals are only for conferences which were scheduled by using Microsoft Exchange or Microsoft Outlook. <br/> |
   
## Metrics

The following table lists the information provided in the Conference Join Time Report.
  
**Conference Join Time Report Metrics**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Date** <br/> The actual title for this metric will vary depending on the Interval that was selected.  <br/> |No  <br/> |Date and time that the conference took place.  <br/> |
|**Total sessions** <br/> |No  <br/> |Total number of sessions, including successful sessions, failed sessions (both expected failures and unexpected failures), and uncategorized sessions.  <br/> |
|**Average (ms)** <br/> |No  <br/> |Average amount of time (in milliseconds) that it took participants to join the conference.  <br/> |
|**Sessions \< 2 seconds, Volume** <br/> |No  <br/> |Number of participants who were able to join the conference in less than 2 seconds.  <br/> |
|**Sessions \< 2 seconds, Percentage** <br/> |No  <br/> ||
|**Sessions 2-5 seconds, Volume** <br/> |No  <br/> |Number of participants who took between 2 seconds and 5 seconds to join the conference.  <br/> |
|**Sessions 2-5 seconds, Percentage** <br/> |No  <br/> |Percentage of the total call participants who took between 2 seconds and 5 seconds to join the conference.  <br/> |
|**Sessions 5-10 seconds, Volume** <br/> |No  <br/> |Number of participants who took between 5 seconds and 10 seconds to join the conference.  <br/> |
|**Sessions 5-10 seconds, Percentage** <br/> |No  <br/> |Percentage of the total call participants who took between 5 seconds and 10 seconds to join the conference.  <br/> |
|**Sessions \> 10 seconds, Volume** <br/> |No  <br/> |Number of participants who required more than 10 seconds to join the conference.  <br/> |
|**Sessions \> 10 seconds, Percentage** <br/> |No  <br/> |Percentage of the total call participants who required more than 10 seconds to join the conference.  <br/> |
   

