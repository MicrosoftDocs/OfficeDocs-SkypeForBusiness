---
title: "Server Media Quality Trend Report in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 8a51fd13-1487-4632-b5ec-f7ae2abe8ed4
description: "Summary: Learn about the Server Media Quality Trend Report in Skype for Business Server."
---

# Server Media Quality Trend Report in Skype for Business Server
 
**Summary:** Learn about the Server Media Quality Trend Report in Skype for Business Server.
  
The Server Media Quality Trend Report provides a way for you to graphically compare up to five servers on Quality of Experience metrics such as call volume, poor call percentage, packet loss, and jitter. This makes it easier to do such things as identify servers that are performing poorly, identify servers that are underutilized, or identify servers that are being overused.
  
## Accessing the Server Media Quality Trend Report

The Server Media Quality Trend Report can be accessed from either one of the following report:
  
- [Server Performance Report in Skype for Business Server](server-performance.md) (by clicking the Trend metric)
    
- [Call Detail Report in Skype for Business Server](call-detail-report.md) (by clicking the A/V edge server metric. If the caller or callee is a server, you can also reach the Server Quality Media Trend Report by clicking the endpoint name.)
    
## Making the Best Use of Server Media Quality Trend Report

When you click the Trend metric on the [Server Performance Report in Skype for Business Server](server-performance.md) for a specific server, the Server Media Quality Trend Report will open. However, you will see only a blank instance of that report; the server you selected on the Server Performance Report will not be displayed onscreen. Instead, you will need to select that server from the Servers dropdown. Note, too that the Servers dropdown includes a Select All option. This option will not work if you have more than 5 servers; the Server Media Quality Trend Report can only display data for a maximum of 5 servers at a time.
  
On the graphs displayed by the Server Media Quality Trend Report, the points labeled Call Volume and Poor Call Percentage are hotlinks; clicking a point on the graph will open an instance of the [Call List Report in Skype for Business Server](call-list-report-0.md) showing the total calls (or poor calls) for the specified time period.
  
## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. The following table lists the filters that you can use with the Server Media Quality Trend Report.
  
**Server Media Quality Trend Report Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date/time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date/time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Interval** <br/> | Time interval. Select one of the following: <br/>  Hourly (a maximum of 25 hours can be displayed) <br/>  Daily (a maximum of 31 days can be displayed) <br/>  Weekly (a maximum of 12 weeks can be displayed) <br/>  If the start and end dates exceed the maximum number of values allowed for the selected interval, only the maximum number of values (starting from the start date) is displayed. For example, if you select the Daily interval with a start date of 8/7/2015 and an end date of 9/28/2015, data is displayed for the days 8/7/2015 12:00 AM to 9/7/2015 12:00 AM (that is, a total of 31 days' worth of data). <br/> |
|**Server type** <br/> | Type of server involved in the call. Allowed values are: <br/>  Mediation Server <br/>  A/V Conferencing Server <br/>  A/V Edge Server <br/>  Gateway (Mediation Server) <br/>  Gateway (Mediation Server Bypass) <br/>  AS Conferencing Server <br/> |
|**Servers** <br/> |Name of the server involved in the session; this dropdown list is automatically populated for you based on the value of the Server type filter. You can select up to 5 different servers when compiling a report.  <br/> |
|**Access type** <br/> | Indicates whether the participant was logged on to the internal network or from the external network. Allowed values are: <br/>  [All] <br/>  Internal <br/>  External <br/> |
|**Network type** <br/> | Indicates the type of network the participant was connected to. Allowed values are: <br/>  [All] <br/>  Wired <br/>  Wireless <br/> |
|**VPN** <br/> | Indicates whether an external participant was using a virtual private network (VPN) connection during the session. Allowed values are: <br/>  [All] <br/>  VPN <br/>  Non-VPN <br/> |
   
## Metrics

The following table lists the information provided in the Server Media Quality Trend Report.
  
**Server Media Quality Trend Report Metrics**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Call volume** <br/> |No  <br/> |Total number of calls.  <br/> |
|**Degradation (MOS)** <br/> |No  <br/> |Average amount of MOS (mean option score) degradation experienced during a call. Degradation values can range from a low of 0.0 to a high of 5.0; a value of 0.5 or less represents acceptable degradation. Historically, mean options scores were calculated by having users rate the quality of a call on a scale of 1-to-5. Skype for Business Server uses a set of algorithms to predict how users would have rated a call.  <br/> High degradation values can be caused by congestion; lack of bandwidth; wireless congestion or interference, or an overloaded media server or endpoint. High degradation results in distorted or lost audio.  <br/> |
|**Poor call percentage** <br/> |No  <br/> |The total number of calls classified as poor. A poor call is any call which at least one of the measured metrics exceeded the allowed value (for example, a call that experienced excessive jitter).  <br/> |
|**Round trip (ms)** <br/> |No  <br/> |Average amount of time (in milliseconds) required for a Real-Time Transport Protocol packet to travel to one endpoint and then back. Round-trip times of 200 milliseconds or less are considered of acceptable quality.  <br/> High round-trip values can be caused by international call routing; a routing misconfiguration; or an overloaded media server. High round-trip times result in difficulties with two-way, real-time audio conversations.  <br/> |
|**Packet loss** <br/> |No  <br/> |Average rate of Real-Time Transport Protocol (RTP) packet loss. (Packet loss occurs when RTP packets, a protocol used for transmitting audio and video across the Internet, failed to reach their destination.) High loss rates are generally caused by congestion; lack of bandwidth; wireless congestion or interference; or an overloaded media server. Packet loss typically results in distorted or lost audio.  <br/> |
|**Jitter (ms)** <br/> |No  <br/> |Average jitter detected between RTP packet arrivals. (Jitter is a measure of the "shakiness" of a call.) High jitter values are typically caused by congestion or an overloaded media server, and result in distorted or lost audio.  <br/> |
|**Healer concealed ratio** <br/> |No  <br/> |Average ratio of concealed audio samples to the total to the total number of samples. (A concealed audio sample is a technique used to smooth out the abrupt transition that would usually be caused by dropped network packets.) High values indicate significant levels of loss concealment applied caused by packet loss or jitter, and results in distorted or lost audio.  <br/> |
|**Healer stretched ratio** <br/> |No  <br/> |Average ratio of stretched audio samples to the total to the total number of samples. (Stretched audio is audio that has been expanded to help maintain call quality when a dropped network packet has been detected.) High values indicate significant levels of sample stretching caused by jitter, and result in audio sounding robotic or distorted.  <br/> |
|**Healer compressed ratio** <br/> |No  <br/> |Average ratio of compressed audio samples to the total number of samples. (Compressed audio is audio that has been compressed to help maintain call quality when a dropped network packet has been detected.) High values indicate significant levels of sample compression caused by jitter, and result in audio sounding accelerated or distorted.  <br/> |
   

