---
title: "The Media Quality Metrics Distribution Report in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: d07996e6-b0a5-4ff8-9512-ab707762b4e2
description: "Summary: Learn about the Media Quality Metrics Distribution Report in Skype for Business Server."
---

# The Media Quality Metrics Distribution Report in Skype for Business Server 
 
**Summary:** Learn about the Media Quality Metrics Distribution Report in Skype for Business Server.
  
The Media Quality Metrics Distribution Report enables you to see a graph that shows the distribution values for a Quality of Experience metric such as jitter or packet loss. For example, suppose your users make a total of 10 phone calls; those 10 calls report the following roundtrip times:
  
|**Call Number**|**Round trip Time (milliseconds)**|
|:-----|:-----|
|1  <br/> |50  <br/> |
|2  <br/> |50  <br/> |
|3  <br/> |50  <br/> |
|4  <br/> |50  <br/> |
|5  <br/> |50  <br/> |
|6  <br/> |50  <br/> |
|7  <br/> |50  <br/> |
|8  <br/> |4550  <br/> |
|9  <br/> |50  <br/> |
|10  <br/> |50  <br/> |
   
The average for those round trip times is 500 milliseconds (5000 divided by 10). Five hundred milliseconds is an extremely large round trip time; as a result, you might believe that you have a serious problem with network congestion. (Long round trip times are typically the result of overloaded networks.)
  
In reality, of course, 90% of your calls had excellent round trip times; you merely had one bad call that skewed the overall results. If you only look at the average round trip time you might jump to a very wrong conclusion.
  
The Media Quality Metrics Distribution Report helps you avoid jumping to wrong conclusions by showing you a graphical distribution of a specified metric (such as round trip time). These graphs can help make it clear that you had nine very good calls and one very bad call. Admittedly, you might still want to further investigate that one call; however, the fact that 9 out of the 10 calls were very good suggests that there is no reason to make any drastic changes to your network, at least not at this point in time.
  
## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. The following table lists the filters that you can use with the Media Quality Metrics Distribution Report.
  
**Media Quality Metrics Distribution Report Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date/time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date/time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Minimum in x axis** <br/> |Lowest value to be displayed on the X axis of the graph.  <br/> |
|**Maximum in x axis** <br/> |Highest value to be displayed on the X axis of the graph.  <br/> |
|**Access type** <br/> | Indicates whether the client was logged on to the internal network or the external network when the call was placed. Select one of the following: <br/>  [All] <br/>  Internal <br/>  External <br/> |
|**VPN** <br/> | Indicates whether an external client was using a virtual private network (VPN) connection when the call was placed. Select one of the following: <br/>  [All] <br/>  VPN <br/>  Non-VPN <br/> |
|**Network type** <br/> | Indicates the type of network the client was connected to when the call was placed. Select one of the following: <br/>  [All] <br/>  Wired <br/>  Wireless <br/> |
   

