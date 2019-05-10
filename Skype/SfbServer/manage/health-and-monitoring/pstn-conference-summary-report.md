---
title: "PSTN Conference Summary Report in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 8e2f0862-4dfa-4c2b-bf8d-ad71419f15d2
description: "Summary: Learn about the PSTN Conference Summary Report in Skype for Business Server."
---

# PSTN Conference Summary Report in Skype for Business Server
 
**Summary:** Learn about the PSTN Conference Summary Report in Skype for Business Server.
  
In Skype for Business Server, a PSTN conference is any conference in which at least one participant dials in to the audio portion by a using a PSTN (public switched telephone network) phone. (A PSTN phone is a "landline," a cell phone, or any other phone which does not make use of Voice over IP.) Although referred to as PSTN conferences in the Monitoring Reports, these conferences are perhaps more-commonly known as dial-in conferences.
  
The PSTN Conference Summary Report provides information about all the PSTN conferences held in your organization (that is, all the conferences that had at least one dial-in user). The report includes information about the total number of PSTN conferences, the total number of people who participated in those conferences, and, perhaps, most important, the total number of dial-in users (the Total PSTN participants metric).
  
## Accessing the PSTN Conference Summary Report

The PSTN Conference Summary Report can only be accessed from the Monitoring Reports home page. This report is not linked to any other reports. Note that you cannot retrieve detailed call information for a PSTN conference, in part because individual endpoints are responsible for submitting this information. PSTN phones are not capable of tracking or submitting call detail information.
  
## Making the Best Use of the PSTN Conference Summary Report

To determine the percentage of all your conferences that include dial-in users, compare the value of the Total PSTN conferences metric with the Total conferences metric found on the [Conference Summary Report in Skype for Business Server](conference-summary-report.md).
  
If you don't see as many PSTN conferences as you might have expected to see, keep in mind that the ability to organize a conference that allows dial-in users depends on the conferencing policy that has been assigned to a user: if very few of your users are allowed to hold PSTN conferences you would obviously see very few PSTN conferences. You can quickly verify which of your conferencing policies (if any) allow users to schedule PSTN conferences by running the following command from within the Skype for Business Server Management Shell:
  
```
Get-CsConferencingPolicy | Select-Object Identity, EnableDialInConferencing
```

That will return data similar to this:
  
<pre>
Identity                                EnableDialInConferencing
--------                                ------------------------
Global                                                      True
site:Redmond                                               False
site:Dublin                                                False
Tag:RedmondDialInUsers                                      True
Tag:DublinDialInUsers                                       True
</pre>

## Filters

Filters provide a way for you to return a more finely targeted set of data or to view the returned data in different ways. For example, the PSTN Conference Summary Report enables you to choose how data should be grouped. In this case, conferences are grouped by hour, day, week, or month.
  
The following table lists the filters that you can use with the PSTN Conference Summary Report.
  
**PSTN Conference Summary Report Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date/time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date/time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Interval** <br/> | Time interval. Select one of the following: <br/>  Hourly (a maximum of 25 hours can be displayed) <br/>  Daily (a maximum of 31 days can be displayed) <br/>  Weekly (a maximum of 12 weeks can be displayed) <br/>  Monthly (a maximum of 12 months can be displayed) <br/>  If the start and end dates exceed the maximum number of values allowed for the selected interval, only the maximum number of values (starting from the start date) is displayed. For example, if you select the Daily interval with a start date of 7/7/2015 and an end date of 2/28/2015, data is displayed for the days 8/7/2015 12:00 AM to 9/7/2015 12:00 AM (that is, a total of 31 days' worth of data). <br/> |
   
## Metrics

The following table lists the information in the PSTN Conference Summary Report.
  
**PSTN Conference Summary Report Metrics**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Hourly** <br/> **Daily** <br/> **Weekly** <br/> **Monthly** <br/> |No  <br/> |Indicates the selected time interval. Where applicable, you can click a given time interval to view detailed information for that interval. For example, if you are using the Daily interval and you click 7/7/2015, you see an hourly breakdown of user registration activity for that date.  <br/> |
|**Total PSTN conferences** <br/> |No  <br/> |Total number conferences that allowed dial-in access.  <br/> |
|**Total participants** <br/> |No  <br/> |Total number of people who participated in conferences that allowed dial-in access.  <br/> |
|**Total A/V conference minutes** <br/> |No  <br/> |Total amount of audio/visual conference time.  <br/> |
|**Total A/V conference participant minutes** <br/> |No  <br/> |Total amount of audio/visual participant time. For example, if one participant spent five minutes in an A/V conference and another participant spent three minutes in the same conference, the total A/V conference participant time would be eight minutes.  <br/> |
|**Total PSTN participants** <br/> |No  <br/> |Total number of users who dialed in to conferences that allowed dial-in access.  <br/> |
|**Total PSTN participant minutes** <br/> |No  <br/> |Total amount of conference time spent by dial-in users. For example, if one dial-in participant spent five minutes in a conference and another participant spent three minutes in the same conference, the total PSTN participant time would be eight minutes.  <br/> |
|**Unique conference organizers** <br/> |No  <br/> |Total number of users who organized at least one conference that allowed dial-in access. Users who organized more than one conference are counted as one unique organizer, just like users who only organized a single conference.  <br/> |
   

