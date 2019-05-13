---
title: "P2P Summary Subreport in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: fc36185a-3cc5-4167-8c93-8a755fa75ac7
description: "Summary: Learn about the P2P Summary Subreport in Skype for Business Server."
---

# P2P Summary Subreport in Skype for Business Server
 
**Summary:** Learn about the P2P Summary Subreport in Skype for Business Server.
  
The P2P Summary Subreport provides an overall view of your failed peer-to-peer communication sessions.
  
## Filters

Filters provide a way for you to return a more finely targeted set of data or to view the returned data in different ways. The following table lists the filters that you can use with the P2P Summary Subreport.
  
**P2P Summary Subreport Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date and time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date and time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Pool** <br/> |Fully qualified domain name (FQDN) of the Registrar pool or Edge Server. You can either select an individual pool or click **[All]** to view data for all the pools. This drop-down list is automatically populated for you based on the records in the database. <br/> |
   
## Metrics

The following table lists the information provided in the P2P Summary Subreport.
  
**P2P Summary Subreport Metrics**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Total sessions** <br/> |No  <br/> |Total number of sessions, including successful sessions, failed sessions (both expected failures and unexpected failures), and uncategorized sessions.  <br/> |
|**Failure rate** <br/> |No  <br/> |Percentage of peer-to-peer sessions that failed.  <br/> |
|**Sessions by Modality** <br/> |No  <br/> |Total number of sessions grouped by modality (for example, instant messaging).  <br/> |
|**Failure rate by modality** <br/> |No  <br/> |Total number of failed sessions grouped by modality (for example, instant messaging).  <br/> |
   

