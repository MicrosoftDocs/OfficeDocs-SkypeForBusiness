---
title: "Conference Summary Report in Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 62f54812-5700-45a3-8526-8f58b0f77fbc
description: "Summary: Learn about the Conference Summary Report in Skype for Business Server."
---

# Conference Summary Report in Skype for Business Server
 
**Summary:** Learn about the Conference Summary Report in Skype for Business Server.
  
The Conference Summary Report provides an overall view of your online conferencing sessions. A conference typically involves more than 2 users and requires the use of conferencing services. By comparison, a peer-to-peer session typically involves just 2 users and does not require the use of Skype for Business Server conferencing services. Peer-to-peer activities are reported on the [Peer-to-Peer Activity Summary Report in Skype for Business Server](peer-to-peer-activity-summary-report.md).
  
The Conference Summary Report not only tells you how many conferences were held during a given time period (hourly, daily, weekly, monthly) but also tells you the total number of people who took part in those conferences, and the total number of unique conference organizers.
  
A "unique" organizer is anyone who schedules at least one conference. For example, if Pilar Ackerman schedules one conference she counts as one unique organizer. If Ken Myer schedules 148 conferences he, too counts as one unique organizer. For example, the following table shows 8 conferences scheduled, but just three unique organizers (Ken Myer, Pilar Ackerman, and David Ahs).
  
|**Conference Organizer**|**Conference Date**|
|:-----|:-----|
|Ken Myer  <br/> |7/7/2015 10:00 AM  <br/> |
|David Ahs  <br/> |7/7/2015 10:00 AM  <br/> |
|Ken Myer  <br/> |7/7/2015 11:00 AM  <br/> |
|Pilar Ackerman  <br/> |7/7/2015 11:00 AM  <br/> |
|Ken Myer  <br/> |7/7/2015 1:00 PM  <br/> |
|Pilar Ackerman  <br/> |7/7/2015 2:00 PM  <br/> |
|Ken Myer  <br/> |7/2/2015 10:00 AM  <br/> |
|Pilar Ackerman  <br/> |7/2/2015 10:00 AM  <br/> |
   
The Conference Summary Report also indicates how many conferences included audio and/or video.
  
## Accessing the Conference Summary Report

The Conference Summary Report is accessed from the Monitoring Reports home page. You can drill down to the Conference Activity report by clicking either of the following metrics:
  
- Total conferences
    
- Total participants
    
## Making the Best Use of the Conference Summary Report

Total values for most of the metrics used on the Conference Summary Report can be found at the bottom of the report; scroll down to see values such as the total number of conferences held during the specified time period, and the total number of people who participated in those conferences. One metric that is not totaled at the bottom of the report is Total unique conference organizers. Why not? Here's one reason. Suppose you are looking at a month's worth of data. On day 1 you had 34 unique conference organizers; on day 2 you had 27 unique conference organizers. Does that mean you had 61 unique conference organizers for those two days? Not necessarily. After all, all 27 people who organized conferences on day 2 might be among the 34 people who organized conferences on day 1. For example, in this simple report, note that Ken Myer and Pilar Ackerman scheduled conferences both on 7/7/2015 and on 7/2/2015:
  
|**Conference Organizer**|**Conference Date**|
|:-----|:-----|
|Ken Myer  <br/> |7/7/2015 10:00 AM  <br/> |
|David Ahs  <br/> |7/7/2015 10:00 AM  <br/> |
|Ken Myer  <br/> |7/7/2015 11:00 AM  <br/> |
|Pilar Ackerman  <br/> |7/7/2015 11:00 AM  <br/> |
|Ken Myer  <br/> |7/7/2015 1:00 PM  <br/> |
|Pilar Ackerman  <br/> |7/7/2015 2:00 PM  <br/> |
|Ken Myer  <br/> |7/2/2015 10:00 AM  <br/> |
|Pilar Ackerman  <br/> |7/2/2015 10:00 AM  <br/> |
   
To get a better idea of the total number of unique users who organized conferences, change your time interval; for example, look at the data by month instead of by day.
  
## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the Conference Summary Report enables you to choose how data should be grouped. In this case, conferences grouped by hour, day, week, or month.
  
The following table lists the filters that you can use with the Conference Summary Report.
  
**Conference Summary Report Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date/time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date/time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Interval** <br/> | Time interval. Select one of the following: <br/>  Hourly (a maximum of 25 hours can be displayed) <br/>  Daily (a maximum of 31 days can be displayed) <br/>  Weekly (a maximum of 12 weeks can be displayed) <br/>  Monthly (a maximum of 12 months can be displayed) <br/>  If the start and end dates exceed the maximum number of values allowed for the selected interval, only the maximum number of values (starting from the start date) are displayed. For example, if you select the Daily interval with a start date of 7/7/2015 and an end date of 2/28/2015, data is displayed for the days 8/7/2015 12:00 AM to 9/7/2015 12:00 AM (that is, a total of 31 days' worth of data). <br/> |
   
## Metrics

The following table the information provided by the Conferences Summary Report.
  
**Conference Summary Report Metrics**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Hourly** <br/> **Daily** <br/> **Weekly** <br/> **Monthly** <br/> |No  <br/> |Indicates the time interval that you selected on the filter toolbar. Where applicable, you can click a given time interval to view detailed information for that interval. For example, if you are using the Daily interval and you click 7/7/2015, you see an hourly breakdown of user registration activity for that date.  <br/> |
|**Total conferences** <br/> |No  <br/> |Total number of conferences (regardless of conference type) that were held. When you click this item, the report shows you the Conference Activity Report for the selected time period.  <br/> |
|**Total participants** <br/> |No  <br/> |Total number of people who took part in the conferences. When you click this item, the report shows you the Conference Activity Report for the selected time period.  <br/> |
|**Average participants per conference** <br/> |No  <br/> |Average number of people who took part in a given conference. Determined by dividing the total conferences by the total participants.  <br/> |
|**Total A/V conferences** <br/> |No  <br/> |Total number of conferences that included audio or video.  <br/> |
|**Total A/V conference minutes** <br/> |No  <br/> |Total number of minutes devoted to audio/video conferencing.  <br/> The Total A/V conference minutes metric summarizes all the audio/visual conference types, including: A/V conferences; IM conferences; app sharing conferences; data conferences; and PSTN conferences.  <br/> |
|**Total A/V conference participant minutes** <br/> |No  <br/> |Total number of participant minutes devoted to audio/video conferencing. For example, suppose one user spends 5 minutes in an audio/video conference and a second user spends 3 minutes in that same conference. That makes a total of 8 participant minutes: 5 minutes plus 3 minutes.  <br/> |
|**Average A/V conference minutes** <br/> |No  <br/> |Average number of minutes per audio/video conference.  <br/> |
|**Total number of unique organizers of conferences** <br/> |No  <br/> |Total number of users who organized at least one conference. Users who organized more than one conference are counted as one unique organizer, just like users who only organized a single conference.  <br/> |
|**Total conference messages** <br/> |No  <br/> |Total number of instant messages sent during the conferences.  <br/> |
   

