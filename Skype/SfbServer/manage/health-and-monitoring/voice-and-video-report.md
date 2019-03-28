---
title: "Peer-to-Peer Voice and Video Report in Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e17c36b5-5a2f-4673-9696-3b2d31c2bb2f
description: "Summary: Learn about the Peer-to-Peer Voice and Video Report in Skype for Business Server."
---

# Peer-to-Peer Voice and Video Report in Skype for Business Server
 
**Summary:** Learn about the Peer-to-Peer Voice and Video Report in Skype for Business Server.
  
The Peer-to-Peer Voice and Video Report provides a detailed look at the distribution of voice and video calls over a specified period of time (for example, calls per hour or calls per day). The report also gives you the option of viewing all the voice and video calls that were made, or of viewing only the successful or failed calls. The reports shows call information broken down into the following groupings:
  
- Calls per pool
    
- Calls per call type (for example, a Skype for Business to Skype for Business call vs. a Skype for Business call to a person on the PSTN network)
    
- Calls per access type (users logged on to the internal network vs. users logged on to the external network)
    
- Calls per Mediation Server
    
## To access the peer-to-peer voice and video report

You can access the Peer-to-Peer Voice and Video Report only by opening the Peer-to-Peer Activity Summary Report and then clicking any of the following metrics:
  
- Total peer-to-peer audio sessions
    
- Total peer-to-peer audio minutes
    
- Total peer-to-peer video sessions
    
- Total peer-to-peer video minutes
    
## To make the best use of the peer-to-peer voice and video report

There are a number of ways you can filter the Peer-to-Peer Voice and Video Report. However, those filtering options are hidden from view by default. To view the filtering options available to you, click **Show/Hide Parameters** button in the upper-right corner of the Report window.
  
## Filters

Filters provide a way for you to return a more finely targeted set of data or to view the data in different ways. The following table lists the filters that you can use with the Peer-to-Peer Voice and Video Report.
  
**Peer-to-peer voice and video report filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date and time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date/time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Interval** <br/> | Time interval. Select one of the following: <br/>  Hourly (a maximum of 25 hours can be displayed) <br/>  Daily (a maximum of 31 days can be displayed) <br/>  Weekly (a maximum of 12 weeks can be displayed) <br/>  Monthly (a maximum of 12 months can be displayed) <br/>  If the start and end dates exceed the maximum number of values allowed for the selected interval, only the maximum number of values (starting from the start date) is displayed. For example, if you select the Daily interval with a start date of 7/7/2015 and an end date of 2/28/2015, data is displayed for the days 8/7/2015 12:00 AM to 9/7/2015 12:00 AM (that is, a total of 31 days' worth of data). <br/> |
|**Media type** <br/> | Indicates the type of media used in the session. Select one of the following: <br/>  Both <br/>  Audio <br/>  Video <br/> |
|**Call disposition** <br/> | Indicates the success or failure of the session. Select one of the following: <br/>  [All] <br/>  Success Calls <br/>  Failed Calls <br/> |
|**Report by** <br/> | Indicates the values to be used in the report. Select one of the following: <br/>  Session count <br/>  Call minutes <br/> |
   
## Metrics for peer-to-peer voice and video activity by Pool

The following table lists the information provided in the Peer-to-Peer Voice and Video Report for each pool.
  
**Metrics for peer-to-peer voice and video activity by pool**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Pool** <br/> |No  <br/> |Name of the Registrar pool or Edge Server used for the call.  <br/> |
|**Date/Time** <br/> |No  <br/> |Date and time period in which the call took place.  <br/> |
|**Total** <br/> |No  <br/> |Total number of sessions or total message count.  <br/> |
   
## Metrics for peer-to-peer voice and video activity by call type

The following table lists the information provided in the Peer-to-Peer Voice and Video Report for each type of call that was made.
  
**Metrics for peer-to-peer voice and video activity by call type**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Call type** <br/> |No  <br/> | Indicates the type of call that was made. Values are one of the following: <br/>  UC-to-UC <br/>  UC-to-PSTN <br/>  PSTN-to-UC <br/>  PSTN-to-PSTN <br/> |
|**Date/Time** <br/> |No  <br/> |Date and time period in which the call took place.  <br/> |
|**Total** <br/> |No  <br/> |Total number of sessions or total message count.  <br/> |
   
## Metrics for peer-to-peer voice and video activity by access type

The following table lists the information provided in the Peer-to-Peer Voice and Video Report for each network access type.
  
**Metrics for peer-to-peer voice and video activity by access type**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Activity type** <br/> |No  <br/> | Indicates whether the clients were logged on to the internal network or the external network when the call was placed. Values are typically one of the following: <br/>  Internal <br/>  External <br/>  Mixed <br/> |
|**Date/Time** <br/> |No  <br/> |Date and time period in which the call took place.  <br/> |
|**Total** <br/> |No  <br/> |Total number of sessions or total message count.  <br/> |
   
## Metrics for peer-to-peer voice and video activity by mediation server

The following table lists the information provided in the Peer-to-Peer Voice and Video Report for each Mediation Server.
  
**Metrics for peer-to-peer voice and video activity by mediation server**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Mediation Server** <br/> |No  <br/> |Name of the Mediation Server.  <br/> |
|**Date/Time** <br/> |No  <br/> |Date and time period in which the call took place.  <br/> |
|**Total** <br/> |No  <br/> |Total number of sessions or total message count.  <br/> |
   

