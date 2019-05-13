---
title: "User Registration Report in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 151d5cc9-cc1b-4cfa-be9c-55ebe321f7a4
description: "Summary: Learn about the User Registration Report in Skype for Business Server."
---

# User Registration Report in Skype for Business Server
 
**Summary:** Learn about the User Registration Report in Skype for Business Server.
  
The User Registration Report provides an overview of user logon activity, most notably information about the number of users who logged on to Skype for Business Server during a specified time period (hourly, daily, weekly, monthly). Keep in mind that the report only tells you how many people logged on. It does not tell you which people logged on. Monitoring Reports do not provide information about which specific users are using Skype for Business Server (and which ones are not). However, you can get a rough estimate of user information by using the User Activity Report.
  
When providing information about user logons, the User Registration Report draws two important distinctions. First, it breaks logons down into two primary categories: internal logons and external logons. Internal logons represent users who logged on from inside your organization's firewall (that is, while connected to the corporate network). External logons represent users who logged on from outside the firewall through an Edge Server (for example, a user who logged on from an Internet café counts as an external logon). If you need to know how many of your users are logging on from outside the firewall, the User Registration Report can provide you with this information.
  
In addition, the User Registration Report notes how many active users were present during a given time period. An active user is a user who took part in an instant messaging (IM) session, participated in a Skype for Business Server Meeting, made or received a phone call, or otherwise used Skype for Business Server during that period of time. This is different from a user who logged on, but never actually used the system.
  
## Accessing the User Registration Report

You access the User Registration Report only from the Monitoring Reports home page. The User Registration Report does not link to any other reports.
  
## Making the Best Use of the User Registration Report

After you've deployed Skype for Business Server one commonly-asked question is this: How do I know if my users are actually using this new technology? Although it has a few limitations in this regard, the User Registration Report can help you answer this question. To determine whether or not users are using Skype for Business Server, you need to do two things. First, get the value of the Unique logon users metric from the User Registration Report. This value tells you how many distinct individuals logged on to Skype for Business Server.
  
By comparison, the Total logons metric shows how many total times anyone logged on to Skype for Business Server. For example, suppose Ken Myer logged on to Skype for Business Server five different times in a single day. In that case, Ken Myer would count as five separate logon sessions for the Total logons metric, but just one logon user for the Unique logon users metric. Likewise, it's not uncommon for a user to log on from multiple devices or multiple locations. For example, a user can log on using her desktop computer, her laptop computer, and she can have an IP phone that automatically logs on to Skype for Business Server. In this example, there is one unique user with three logons.
  
To further explain the difference between total logons and unique logons, consider the logons for a given time period in the following table.
  
|**User**|**Logon time**|
|:-----|:-----|
|Ken Myer  <br/> |7/7/2015 8:45 AM  <br/> |
|Ken Myer  <br/> |7/7/2015 8:46 AM  <br/> |
|Pilar Ackerman  <br/> |7/7/2015 9:17 AM  <br/> |
|Ken Myer  <br/> |7/7/2015 9:22 AM  <br/> |
|Pilar Ackerman  <br/> |7/7/2015 9:31 AM  <br/> |
   
Notice that there is a total of five logons; however, there are only two unique logon users: Ken Myer (who logged on three times) and Pilar Ackerman (who logged on twice). That's the difference between logons and unique logon users.
  
In addition to knowing the number of unique logons, you need to know the total number of users who have been enabled for Skype for Business Server. That value can be retrieved by opening the Skype for Business Server Management Shell and running the following Windows PowerShell command:
  
```
(Get-CsUser).Count
```

If the preceding command returns a value of 1,236 and Unique logon users metric returns an average value of 667, that suggests that a little over half of your users enable for Skype for Business are actually logging on to the system each day (that is, 667 divided by 1,236, which is approximately 54%).
  
> [!CAUTION]
> Keep in mind that the logon metrics record users who actually logged on during the specified time period. They don't keep track of users who were already logged on to the system. For example, if your Unique logon users metric shows 667 logons and you have 1,236 users, that suggests that about half your users are logging on to the system. However, suppose 300 users were already logged on to the system at the time you began checking the logon data. That would mean that you actually had nearly 1,000 users logged on to Skype for Business Server, which would mean that closer to 80% of your users were logged on. 
  
You should also compare the Unique logon users value with the value of the Unique active users metric. The Unique active users metric tells you how many unique users actually used Skype for Business Server: they made a phone call, they joined a Skype for Business Server Meeting, or they participated in an IM session. This is useful information, because Skype for Business Server can be configured to automatically start each time a user starts Windows. Because of that, you might have a large number of users who automatically log on to Skype for Business when they log on to Windows each day, but then never actually use Skype for Business Server during that time period.
  
The Unique active users metric also provides more meaningful data in an organization where users typically do not log off Windows at the end of the day. Instead, they simply lock their computers and leave Windows and Skype for Business running. In a situation like that, you might end up with very few logons per day because your users logged on several days ago and never logged off. However, Unique active users tells you whether users are actively using Skype for Business or another Skype for Business Server client.
  
## Filters

Filters provide a way for you to return a more finely targeted set of data or to view the returned data in different ways. For example, the User Registration Report enables you to view data for all your Registrar pool and Edge Servers or to view data for an individual pool. You can also choose how data should be grouped. In this case, registrations grouped by hour, day, week, or month.
  
The following table lists the filters that you can use with the User Registration Report.
  
**User Registration Report Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date and time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date and time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Interval** <br/> | Time interval. Select one of the following: <br/>  Hourly (a maximum of 25 hours can be displayed) <br/>  Daily (a maximum of 31 days can be displayed) <br/>  Weekly (a maximum of 12 weeks can be displayed) <br/>  Monthly (a maximum of 12 months can be displayed) <br/>  If the start and end dates exceed the maximum number of values allowed for the selected interval, only the maximum number of values (starting from the start date) are displayed. For example, if you select the Daily interval with a start date of 7/7/2015 and an end date of 2/28/2015, data is displayed for the days 8/7/2015 12:00 AM to 9/7/2015 12:00 AM (that is, a total of 31 days' worth of data). <br/> |
|**Pool** <br/> |Fully qualified domain name (FQDN) of the Registrar pool or Edge Server. You can either select an individual pool or choose **[All]** to view data for all the pools. This drop-down list is automatically populated for you based on the records in the database. <br/> |
   
## Metrics

The following table lists the information provided in the User Registration Report. 
  
**User Registration Report Metrics**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Hourly** <br/> **Daily** <br/> **Weekly** <br/> **Monthly** <br/> |No  <br/> |Indicates the time interval that you selected on the filter toolbar. Where applicable, you can click a given time interval to view detailed information for that interval. For example, if you are using the Daily interval and you click 7/7/2015, you see an hourly breakdown of user registration activity for that date.  <br/> |
|**Total logons** <br/> |No  <br/> |Total number of successful logon sessions.  <br/> |
|**Internal logons** <br/> |No  <br/> |Total number of logons within the internal network.  <br/> |
|**External logons** <br/> |No  <br/> |Total number of logons from outside the internal network, using the Edge Server.  <br/> |
|**Unique logon users** <br/> |No  <br/> |Total number of users who had at least one logon session. A user who had multiple logon sessions counts as one user, the same as a person who had just a single logon session.  <br/> |
|**Unique active users** <br/> |No  <br/> |Total number of users who were involved in a peer-to-peer or conferencing session. A user who had multiple sessions counts as one user, the same as a person who had just a single session.  <br/> |
   

