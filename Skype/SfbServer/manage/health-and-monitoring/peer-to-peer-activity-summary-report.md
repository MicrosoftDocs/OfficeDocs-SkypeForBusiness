---
title: "Peer-to-Peer Activity Summary Report in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e829a21e-9dfa-46ba-9b5b-077c175d6586
description: "Summary: Learn about the Peer-to-Peer Activity Summary Report in Skype for Business Server."
---

# Peer-to-Peer Activity Summary Report in Skype for Business Server
 
**Summary:** Learn about the Peer-to-Peer Activity Summary Report in Skype for Business Server.
  
The Peer-to-Peer Activity Summary Report provides an overall view of your peer-to-peer communication sessions. A peer-to-peer session typically involves just two users, and does not require the use of the Skype for Business Server conferencing services. By comparison, a conference typically involves more than two users and requires the use of Skype for Business Server conferencing services. Conference activity is reported on the Conference Summary Report.
  
The Peer-to-Peer Activity Summary Report helps you answer questions like the following:
  
- How many peer-to-peer instant messages do my users send on a typical day?
    
- Are any of my users actually taking advantage of the Skype for Business Server application sharing and file transfer capabilities?
    
- Users have been complaining that the network seems slow at certain times of the day. How many minutes are devoted to peer-to-peer audio and video sessions during those time periods?
    
## Accessing the Peer-to-Peer Activity Summary Report

You access the Peer-to-Peer Activity Summary Report from the Monitoring Reports home page. You open the [Peer-to-Peer IM Report in Skype for Business Server](im-report.md) by clicking either of the following metrics:
  
- Total peer-to-peer IM sessions
    
- Total peer-to-peer IM messages
    
Likewise, you can open the Peer-to-Peer Voice and Video Report by clicking any of these metrics:
  
- Total peer-to-peer audio sessions
    
- Total peer-to-peer audio session minutes
    
- Total peer-to-peer audio sessions
    
- Total peer-to-peer audio session minutes
    
## Making the Best Use of the Peer-to-Peer Activity Summary Report

At the bottom of the Peer-to-Peer Activity Summary Report you'll find totals for metrics such as Total peer-to-peer IM sessions and Total peer-to-peer IM messages. This provides a quick summary of the detailed information found in the body of the report.
  
## Filters

Filters provide a way for you to return a more finely targeted set of data or to view the returned data in different ways. For example, the Peer-to-Peer Activity Summary Report enables you to choose how data should be grouped. In this case, activity grouped by hour, day, week, or month.
  
The following table lists the filters that you can use with the Peer-to-Peer Activity Summary Report.
  
**Peer-to-Peer Activity Summary Report Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date and time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/17/12015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/17/12015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/13/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date and time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/17/12015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/17/12015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/13/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Interval** <br/> | Time interval. Select one of the following: <br/>  Hourly (a maximum of 25 hours can be displayed) <br/>  Daily (a maximum of 31 days can be displayed) <br/>  Weekly (a maximum of 12 weeks can be displayed) <br/>  Monthly (a maximum of 12 months can be displayed) <br/>  If the start and end dates exceed the maximum number of values allowed for the selected interval, only the maximum number of values (starting from the start date) is displayed. For example, if you select the Daily interval with a start date of 7/17/12015 and an end date of 2/28/2015, data is displayed for the days 8/7/12015 12:00 AM to 9/7/12015 12:00 AM (that is, a total of 31 days' worth of data). <br/> |
   
## Metrics

The following table lists the information provided in the Peer-to-Peer Activity Summary Report.
  
**Peer-to-Peer Activity Summary Report Metrics**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Hourly** <br/> **Daily** <br/> **Weekly** <br/> **Monthly** <br/> |No  <br/> |Indicates the time interval that you selected on the filter toolbar. Where applicable, you can click a given time interval to view detailed information for that interval. For example, if you are using the Daily interval and you click 7/17/12015, you see an hourly breakdown of user registration activity for that date.  <br/> |
|**Total peer-to-peer sessions** <br/> |No  <br/> |Total number of peer-to-peer sessions conducted, regardless of session type.  <br/> |
|**Total peer-to-peer IM sessions** <br/> |No  <br/> |Total number of peer-to-peer instant messaging (IM) sessions. When you click this item, the report shows you the Peer-to-Peer IM Report for the selected time period.  <br/> |
|**Total peer-to-peer IM messages** <br/> |No  <br/> |Total number of instant messages sent in peer-to-peer sessions. When you click this item, the report shows you the Peer-to-Peer IM Report for the selected time period.  <br/> |
|**Total peer-to-peer audio sessions** <br/> |No  <br/> |Total number of peer-to-peer audio calls. When you click this field, the report shows you the Peer-to-Peer Voice and Video Report for the selected time period.  <br/> |
|**Total peer-to-peer audio session minutes** <br/> |No  <br/> |Total amount of time spent in peer-to-peer audio sessions. When you click this item, the report shows you the Peer-to-Peer Voice and Video Report for the selected time period.  <br/> |
|**Average peer-to-peer audio session minutes** <br/> |No  <br/> |Average amount of time spent in peer-to-peer audio sessions. Calculated by dividing the total audio session time by the total number of audio sessions.  <br/> |
|**Total peer-to-peer video sessions** <br/> |No  <br/> |Total number of peer-to-peer video calls. Note that video sessions are also counted as audio sessions: each video session is counted as one video session and one audio session. When you click this item, the report shows you the Peer-to-Peer Voice and Video Report for the selected time period.  <br/> |
|**Total peer-to-peer video session minutes** <br/> |No  <br/> |Total amount of time spent in peer-to-peer video sessions. When you click this item, the report shows you the Peer-to-Peer Voice and Video Report for the selected time period.  <br/> |
|**Average peer-to-peer video session minutes** <br/> |No  <br/> |Average amount of time spent in peer-to-peer video sessions. Calculated by dividing the total video session time by the total number of video sessions.  <br/> |
|**Total peer-to-peer file transfer sessions** <br/> |No  <br/> |Total number of peer-to-peer sessions that included file transfers.  <br/> |
|**Total peer-to-peer application sharing sessions** <br/> |No  <br/> |Total number of peer-to-peer sessions that included application sharing.  <br/> |
   

