---
title: "Media Quality Comparison Report in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c1d0b5a8-98ff-455a-b78b-a05a21cf066d
description: "Summary: Learn about the Media Quality Comparison Report in Skype for Business Server."
---

# Media Quality Comparison Report in Skype for Business Server
 
**Summary:** Learn about the Media Quality Comparison Report in Skype for Business Server.
  
The Media Quality Comparison Report enables you to compare call quality values for different types of audio calls (for example, calls made over a wireless network vs. calls made across a wired connection).
  
## Accessing the Media Quality Comparison Report

The Media Quality Comparison Report is accessed from the Monitoring Reports home page. 
  
## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. The following table lists the filters that you can use with the Media Quality Comparison Report.
  
**Media Quality Comparison Report Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date/time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date/time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Calls** <br/> | Type of call to be used as the main comparison item. Allowed values are: <br/>  [All] <br/>  External <br/>  Internal <br/>  VPN <br/>  Non-VPN <br/>  Wired <br/>  Wireless <br/>  External and wired <br/>  External and wireless <br/>  External and VPN <br/>  External and non-VPN <br/>  Internal and wired <br/>  Internal and wireless <br/> |
|**Compare with calls** <br/> | Type of call to be used as the secondary comparison item. Allowed values are: <br/>  [All] <br/>  External <br/>  Internal <br/>  VPN <br/>  Non-VPN <br/>  Wired <br/>  Wireless <br/>  External and wired <br/>  External and wireless <br/>  External and VPN <br/>  External and non-VPN <br/>  Internal and wired <br/>  Internal and wireless <br/> |
|**Interval** <br/> | Time interval. Select one of the following: <br/>  Hourly (a maximum of 25 hours can be displayed) <br/>  Daily (a maximum of 31 days can be displayed) <br/>  Weekly (a maximum of 12 weeks can be displayed) <br/>  If the start and end dates exceed the maximum number of values allowed for the selected interval, only the maximum number of values (starting from the start date) is displayed. For example, if you select the Daily interval with a start date of 7/7/2015 and an end date of 2/28/2015, data is displayed for the days 8/7/2015 12:00 AM to 9/7/2015 12:00 AM (that is, a total of 31 days' worth of data). <br/> |
   
## Metrics

The following table lists the information provided in the Media Quality Comparison Report.
  
**Media Quality Comparison Report Metrics**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Call volume** <br/> |No  <br/> |Total number of calls.  <br/> |
|**Degradation (MOS)** <br/> |No  <br/> |Average amount of MOS (mean opinion score) degradation experienced during a call. Degradation values can range from a low of 0.0 to a high of 5.0; a value of 0.5 or less represents acceptable degradation. Historically, mean opinion scores were calculated by having users rate the quality of a call on a scale of 1-to-5. Skype for Business Server uses a set of algorithms to predict how users would have rated a call.  <br/> High degradation values can be caused by congestion; lack of bandwidth; wireless congestion or interference, or an overloaded media server or endpoint. High degradation results in distorted or lost audio.  <br/> |
|**Poor call percentage** <br/> |No  <br/> |The total number of calls classified as poor. A poor call is any call which at least one of the measured metrics exceeded the allowed value (for example, a call that experienced excessive jitter).  <br/> |
|**Round trip (ms)** <br/> |No  <br/> |Average amount of (in milliseconds) required for a Real-Time Transport Protocol packet to travel to another endpoint and then back. Round-trip times of 200 milliseconds or less are considered of acceptable quality.  <br/> High round-trip values can be caused by international call routing; a routing misconfiguration; or an overloaded media server. High round-trip times result in difficulties with two-way, real-time audio conversations.  <br/> |
|**Packet loss** <br/> |No  <br/> |Average rate of Real-Time Transport Protocol (RTP) packet loss. (Packet loss occurs when RTP packets, a protocol used for transmitting audio and video across the Internet, failed to reach their destination.) High loss rates are generally caused by congestion; lack of bandwidth; wireless congestion or interference; or an overloaded media server. Packet loss typically results in distorted or lost audio.  <br/> |
|**Jitter (ms)** <br/> |No  <br/> |Average jitter detected between RTP packet arrivals. (Jitter is a measure of the "shakiness" of a call.) High jitter values are typically caused by congestion or an overloaded media server, and result in distorted or lost audio.  <br/> |
|**Healer concealed ratio** <br/> |No  <br/> |Average ratio of concealed audio samples to the total to the total number of samples. (A concealed audio sample is a technique used to smooth out the abrupt transition that would usually be caused by dropped network packets.) High values indicate significant levels of loss concealment applied caused by packet loss or jitter, and results in distorted or lost audio.  <br/> |
|**Healer stretched ratio** <br/> |No  <br/> |Average ratio of stretched audio samples to the total to the total number of samples. (Stretched audio is audio that has been expanded to help maintain call quality when a dropped network packet has been detected.) High values indicate significant levels of sample stretching caused by jitter, and result in audio sounding robotic or distorted.  <br/> |
|**Healer compressed ratio** <br/> |No  <br/> |Average ratio of compressed audio samples to the total number of samples. (Compressed audio is audio that has been compressed to help maintain call quality when a dropped network packet has been detected.) High values indicate significant levels of sample compression caused by jitter, and result in audio sounding accelerated or distorted.  <br/> |
   

