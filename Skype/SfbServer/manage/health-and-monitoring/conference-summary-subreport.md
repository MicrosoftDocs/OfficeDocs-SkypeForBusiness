---
title: "Conference Summary Subreport in Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 2fc1d2bf-34f5-4093-a6e2-250ec1f1b004
description: "Summary: Learn about the Conference Summary Subreport in Skype for Business Server."
---

# Conference Summary Subreport in Skype for Business Server
 
**Summary:** Learn about the Conference Summary Subreport in Skype for Business Server.
  
The Conference Summary Subreport provides an overall view of failed conference sessions. These failed sessions are further broken down by session type: Focus sessions and MCU sessions.
  
## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. The following table lists the filters that you can use with the Conference Summary Subreport.
  
**Conference Summary Subreport Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date/time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date/time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Pool** <br/> |Fully qualified domain name (FQDN) of the Registrar pool or Edge Server. You can either select an individual pool or click **[All]** to view data for all the pools. This drop-down list is automatically populated for you based on the records in the database. <br/> |
   
## Metrics

The following table lists the information provided in the Conference Summary Subreport.
  
**Conference Summary Subreport Metrics**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Total conferences** <br/> |No  <br/> |Total number of conferences held.  <br/> |
|**Total conference sessions** <br/> |No  <br/> |Total number of conference sessions. A single conference can have multiple sessions; for example, a conference might include both a Focus session and an MCU session.  <br/> |
|**Overall session failure rate** <br/> |No  <br/> |Percentage of all conferences that failed.  <br/> |
|**Focus sessions** <br/> |No  <br/> |Total number of Focus sessions.  <br/> |
|**Focus failure rate** <br/> |No  <br/> |Percentage of Focus sessions that failed.  <br/> |
|MCU sessions  <br/> |No  <br/> |Total number of MCU sessions.  <br/> |
|**MCU failure rate** <br/> |No  <br/> |Percentage of MCU sessions that failed.  <br/> |
|**MCU sessions by modality** <br/> |No  <br/> |Total number of MCU sessions, grouped by modality (for example, IM conferencing).  <br/> |
|**Failure rate by modality** <br/> |No  <br/> |Percentage of MCU sessions that failed, grouped by modality (for example, IM conferencing).  <br/> |
   

