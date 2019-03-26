---
title: "Server Performance Report in Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 942bb39a-1790-498e-9d99-8f6ce2d155c3

description: "Summary: Learn about the Server Performance Report in Skype for Business Server."
---

# Server Performance Report in Skype for Business Server
 
**Summary:** Learn about the Server Performance Report in Skype for Business Server.
  
The Server Performance Report provides a list of Skype for Business Server servers that have experienced the highest percentage of poor calls. The report breaks down servers by server type, reporting separate statistics for the following types:
  
- Mediation Server
    
- A/V Conferencing Server
    
- A/V Edge Server
    
- Gateway (Mediation Server)
    
- Gateway (Mediation Server bypass)
    
- Video (including video metrics for A/V Conferencing servers and A/V Edge servers)
    
- Application Sharing (including application sharing metrics for A/V Conferencing servers and A/V Edge servers)
    
It's important to note that the ranking shown in this report as relative rankings. For example, suppose your worst-performing server had one poor call among its 1,000 placed calls. That's a more-than-acceptable percentage of .1%. However, if that's the worst-performing server you have (that is, if all your other servers have a poor call percentage even lower than .1%), then that server will still appear on the Server Performance Report.
  
## Accessing the Server Performance Report

The Server Performance Report is accessed from the Monitoring Reports home page. You can drill down to the [Call List Report in Skype for Business Server](call-list-report-0.md) by clicking either of the following metrics:
  
- Call volume
    
- Poor call percentage
    
In addition, you can drill down to the Server Media Quality Trend Report by clicking the following metric:
  
- Trend
    
## Making the best use of the Server Performance Report

The Server Performance Report provides a number of ways to filter data; for example, you can filter on network type (calls made from a wired connection vs. calls made from a wireless connection) and access type (calls made from inside the firewall vs. calls made from outside the firewall). It's a good idea when viewing the server performance report to make use of these filters. For example, suppose you have a Mediation Server that has a poor call percentage of 3.24%. If you look solely at wireless calls, that same server might have a poor call percentage approaching 20%. That means that the server was having difficulty with wireless calls, a problem that is partially obscured because the server was not having problems with wired calls.
  
## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the Server Performance Report enables you to do such things as filter the returned data by server type or by network type (that is, wired or wireless). You can also choose how data should be grouped. In this case, data is grouped by hour, day, week, or month.
  
The following table lists the filters that you can use with the Server Performance Report.
  
**Server Performance Report Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date/time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date/time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Server type** <br/> |Indicates the type of server whose performance should be reported. Select one of the following:  <br/> [All] Mediation Server A/V Conferencing Server A/V Edge Server |
|**Top N** <br/> |Indicates the number of servers (based on their poor call percentage) to be displayed in each category. For example, if you select **5** then the five poorest-performing servers are displayed. Select one of the following: <br/> [All] 5 10 |
|**Access type** <br/> |Indicates whether the client was logged on to the internal network or the external network when the call was placed. Select one of the following:  <br/> [All] Internal External |
|**Network type** <br/> |Indicates the type of network the client was connected to when the call was placed. Select one of the following:  <br/> [All] Wired Wireless |
|**VPN** <br/> |Indicates whether an external client was using a virtual private network (VPN) connection when the call was placed. Select one of the following:  <br/> [All] VPN Non-VPN |
   
## Metrics

The following table lists the information provided in the Server Performance Report.
  
**Server Performance Report Metrics: Audio Call Summary**

|**Name**|**Can Sort On**|**Description**|
|:-----|:-----|:-----|
|**Server** <br/> |No  <br/> |Name/IP address of the server.  <br/> |
|**Call volume** <br/> |No  <br/> |Total number of calls made.  <br/> |
|**Poor call percentage** <br/> |No  <br/> |Total number of calls classified as poor. A poor call is any call which at least one of the measured metrics exceeded the allowed value (for example, a call that experienced excessive jitter).  <br/> |
|**Round trip (ms)** <br/> |Yes  <br/> |Average amount of (in milliseconds) required for a real-time transport protocol (RTP) packet to travel to another endpoint and then back. Round-trip times of 100 milliseconds or less are considered of acceptable quality.  <br/> High round-trip values can be caused by international call routing; a routing misconfiguration; or an overloaded media server. High round-trip times result in difficulties with two-way, real-time audio conversations.  <br/> |
|**Degradation (MOS)** <br/> |Yes  <br/> |Average amount of mean opinion score (MOS) degradation experienced during a call. Degradation values can range from a low of 0.0 to a high of 5.0. A value of 0.5 or less represents acceptable degradation. Historically, mean options scores were calculated by having users rate the quality of a call on a scale of 1-to-5. In Skype for Business Server, the Monitoring Server uses a set of algorithms to predict how users would have rated a call.  <br/> High degradation values can be caused by congestion, lack of bandwidth, wireless congestion or interference, or an overloaded media server or endpoint. High degradation results in distorted or lost audio.  <br/> |
|**Packet loss** <br/> |Yes  <br/> |Average rate of real-time transport protocol (RTP) packet loss. (Packet loss occurs when RTP packets, a protocol used for transmitting audio and video across the Internet, failed to reach their destination.) High loss rates are generally caused by congestion, lack of bandwidth, wireless congestion or interference, or an overloaded media server. Packet loss typically results in distorted or lost audio.  <br/> |
|**Jitter (ms)** <br/> |Yes  <br/> |Average jitter detected between RTP packet arrivals. (Jitter is a measure of the "shakiness" of a call.) High jitter values are typically caused by congestion or an overloaded media server, and result in distorted or lost audio.  <br/> |
|**Healer concealed ratio** <br/> |Yes  <br/> |Average ratio of concealed audio samples to the total to the total number of samples. (A concealed audio sample is a technique used to smooth out the abrupt transition that would usually be caused by dropped network packets.) High values indicate significant levels of loss concealment applied caused by packet loss or jitter, and results in distorted or lost audio.  <br/> |
|**Healer stretched ratio** <br/> |Yes  <br/> |Average ratio of stretched audio samples to the total to the total number of samples. (Stretched audio is audio that has been expanded to help maintain call quality when a dropped network packet has been detected.) High values indicate significant levels of sample stretching caused by jitter, and result in audio sounding robotic or distorted.  <br/> |
|**Healer compressed ratio** <br/> |Yes  <br/> |Average ratio of compressed audio samples to the total number of samples. (Compressed audio is audio that has been compressed to help maintain call quality when a dropped network packet has been detected.) High values indicate significant levels of sample compression caused by jitter, and result in audio sounding accelerated or distorted.  <br/> |
   
**Server Performance Report Metrics: Video Call Summary**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Call type/Endpoint type** <br/> |No  <br/> | When you click this item, the report shows detailed information about calls based on that type. Call types include: <br/>  UC Peer-to-Peer Calls <br/>  UC Conference Sessions <br/>  PSTN Conference Sessions <br/>  PSTN Calls: Media Bypass <br/>  PSTN Calls (Non-Bypass): UC Leg <br/>  PSTN Calls (Non-Bypass): Gateway Leg <br/>  Other Call Types <br/> |
|**Call volume** <br/> |No  <br/> |Total number of calls per call type.  <br/> |
|**Poor call percentage** <br/> |No  <br/> |Total number of calls classified as poor. A poor call is any call which at least one of the measured metrics exceeded the allowed value (for example, a call that experienced excessive jitter).  <br/> |
|**Call volume (wireless call)** <br/> |No  <br/> |Total number of calls that used a wireless connection.  <br/> |
|**Call volume (VPN call)** <br/> |No  <br/> |Total number of calls that used a VPN connection.  <br/> |
|**Call volume (external call)** <br/> |No  <br/> |Number of calls that used an external connection (that is, a connection outside the internal network).  <br/> |
|**Avg bit-rate (Kbits/s)** <br/> |No  <br/> |Average video bit rate (in kilobits per second).  <br/> |
|**Low bit-rate %** <br/> |No  <br/> |Percentage of the call where the bit rate was low.  <br/> |
|**Outbound packet loss** <br/> |No  <br/> |Real-Time Transport Protocol (RTP) packet loss for outbound packets. (Packet loss occurs when RTP packets, a protocol used for transmitting audio and video across the Internet, failed to reach their destination.) High loss rates are generally caused by congestion; lack of bandwidth; wireless congestion or interference; or an overloaded media server. Packet loss typically results in distorted or lost audio.  <br/> |
|**Frozen frame %** <br/> |No  <br/> |Percentage of "frozen" frames. In a frozen frame, the video stops advancing while the audio portion of the call continues.  <br/> |
|**Outbound avg frame rate** <br/> |No  <br/> |Average frame rate for outbound transmissions during the call.  <br/> |
|**Inbound avg frame rate** <br/> |No  <br/> |Average frame rate for incoming transmissions during the call.  <br/> |
|**Inbound low frame rate %** <br/> |No  <br/> |Percentage of the call where the bit rate for incoming video was low.  <br/> |
|**Client health %** <br/> ||Indicates the relative health of the client device during the call.  <br/> |
   
**Server Performance Report Metrics: Application Sharing Call Summary**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Call type/Endpoint type** <br/> |No  <br/> | When you click this item, the report shows detailed information about calls based on that type. Call types include: <br/>  UC Peer-to-Peer Calls <br/>  UC Conference Sessions <br/>  PSTN Conference Sessions <br/>  PSTN Calls: Media Bypass <br/>  PSTN Calls (Non-Bypass): UC Leg <br/>  PSTN Calls (Non-Bypass): Gateway Leg <br/>  Other Call Types <br/> |
|**Call volume** <br/> |No  <br/> |Total number of calls per call type.  <br/> |
|**Poor call percentage** <br/> |No  <br/> |Total number of calls classified as poor. A poor call is any call which at least one of the measured metrics exceeded the allowed value (for example, a call that experienced excessive jitter).  <br/> |
|**Call volume (wireless call)** <br/> |No  <br/> |Total number of calls that used a wireless connection.  <br/> |
|**Call volume (VPN call)** <br/> |No  <br/> |Total number of calls that used a VPN connection.  <br/> |
|**Call volume (external call)** <br/> |No  <br/> |Number of calls that used an external connection (that is, a connection outside the internal network).  <br/> |
|**Jitter (ms)** <br/> |No  <br/> |Average jitter detected between RTP packet arrivals. (Jitter is a measure of the "shakiness" of a call.) High jitter values are typically caused by congestion or an overloaded media server, and result in distorted or lost audio.  <br/> |
|**Avg. relative one way** <br/> |No  <br/> |Average relative one-way delay between two media endpoints. This is a single-hop latency measure.  <br/> |
|**Avg. RDP tile processing latency** <br/> |No  <br/> |The average RDP tile processing latency in the AS Conferencing Server over the duration of the viewing session. This metric does not cover network latency. A high average reflects a longer delay in the viewing experience. An overloaded conferencing server may experience higher average delays.  <br/> |
|**Total spoiled tile %** <br/> |No  <br/> |Total percentage of spoiled RDP tiles.  <br/> |
   

