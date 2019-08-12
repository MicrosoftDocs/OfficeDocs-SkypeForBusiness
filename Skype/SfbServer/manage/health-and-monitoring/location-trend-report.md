---
title: "Location Trend Report in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 61e2db3c-9f10-4411-8e7e-c6950faf8533
description: "Summary: Learn about the Location Trend Report in Skype for Business Server."
---

# Location Trend Report in Skype for Business Server
 
**Summary:** Learn about the Location Trend Report in Skype for Business Server.
  
The Location Trend Report provides call quality trend information for network locations.
  
## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the Location Trend Report enables you to filter the returned data by such things as access type (that is, interval access vs. external access) or by wired/wireless network connection. You can also choose how data should be grouped. In this case, calls are grouped by hour, day, or week.
  
The following table lists the filters that you can use with the Location Trend Report. 
  
**Location Trend Report Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date/time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date/time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Interval** <br/> | Time interval. Select one of the following: <br/>  Hourly (a maximum of 25 hours can be displayed) <br/>  Daily (a maximum of 31 days can be displayed) <br/>  Weekly (a maximum of 12 weeks can be displayed) <br/>  If the start and end dates exceed the maximum number of values allowed for the selected interval, only the maximum number of values (starting from the start date) is displayed. For example, if you select the Daily interval with a start date of 1/1/2011 and an end date of 2/28/2011, data is displayed for the days 8/1/2011 12:00 AM to 9/1/2011 12:00 AM (that is, a total of 31 days' worth of data). <br/> |
|**Access type** <br/> | Indicates whether the client was logged on to the internal network or the external network when the call was placed. Select one of the following: <br/>  [All] <br/>  Internal <br/>  External <br/> |
|**Network type** <br/> | Indicates the type of network the client was connected to when the call was placed. Select one of the following: <br/>  [All] <br/>  Wired <br/>  Wireless <br/> |
|**VPN** <br/> | Indicates whether an external client was using a virtual private network (VPN) connection when the call was placed. Select one of the following: <br/>  [All] <br/>  VPN <br/>  Non-VPN <br/> |
   

