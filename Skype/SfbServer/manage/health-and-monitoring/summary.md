---
title: "Media Quality Summary Report in Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 8bd59ad6-3087-49c8-b692-5573fe2ffcd8
description: "Summary: Learn about the Media Quality Summary Report in Skype for Business Server."
---

# Media Quality Summary Report in Skype for Business Server
 
**Summary:** Learn about the Media Quality Summary Report in Skype for Business Server.
  
The Media Quality Summary Report is perhaps your best bet for analyzing call quality in your organization: this report provides detailed Quality of Experience (QoE) call metrics broken down into the following categories:
  
- UC Peer to Peer Calls (such as a Skype for Business to Skype for Business call)
    
- UC Conference Sessions
    
- PSTN Conference Sessions
    
- PSTN Calls: Media Bypass
    
- PSTN Calls (Non-Bypass): UC Leg
    
- PSTN Calls (Non-Bypass): Gateway Leg
    
- Other Call Types
    
When you first open the report, you see summary information for each of these categories. Without leaving the report, you can expand each category to look at subcategories such as calls made from Office Communicator 2007 R2 to Skype for Business. In turn, you can then drill down into these subcategories to see details about each call made within that subcategory.
  
In Skype for Business Server the Media Quality Summary Report further breaks the data down into three call types: audio calls, video calls, and application sharing calls. Each call type has its own section in the report, and its own custom set of call metrics.
  
The Media Quality Summary Report also allows you to apply filters that enable you to compare the call quality of wired calls vs. wireless calls, internal calls vs. external calls, and VPN calls vs. non-VPN calls.
  
## Accessing the Media Quality Summary Report

The Media Quality Summary Report is accessed from the Monitoring Reports home page. You can drill down to the [Call List Report in Skype for Business Server](call-list-report-0.md) by clicking either of the following metrics:
  
- Call volume
    
- Poor call percentage
    
In addition, you can access the Media Quality Metrics Distribution Report by clicking any of the following audio call metrics:
  
- Round trip (ms)
    
- Degradation (MOS)
    
- Packet loss
    
- Jitter (ms)
    
- Healer concealed ratio
    
- Healer stretched ratio
    
- Healer compressed ratio
    
## Filters

Filters provide a way for you to return a more finely-targeted set of data or to view the returned data in different ways. For example, the Media Quality Summary Report enables you to filter the returned data by such things as access type (that is, interval access vs. external access) or by wired/wireless network connection. You can also choose how data should be grouped. In this case, calls are grouped by hour, day, week, or month.
  
The following table lists the filters that you can use with the Media Quality Summary Report.
  
**Media Quality Summary Report Filters**

|**Name**|**Description**|
|:-----|:-----|
|**From** <br/> |Start date/time for the time range. To view data by hours, enter both the start date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter a start time, the report automatically begins at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**To** <br/> |End date/time for the time range. To view data by hours, enter both the end date and time as follows:  <br/> 7/7/2015 1:00 PM  <br/> If you do not enter an end time, the report automatically ends at 12:00 AM on the specified day. To view data by day, enter just the date:  <br/> 7/7/2015  <br/> To view by week or by month, enter a date that falls anywhere within the week or month that you want to view (you do not have to enter the first day of the week or month):  <br/> 7/3/2015  <br/> Weeks always run from Sunday through Saturday.  <br/> |
|**Access type** <br/> | Indicates whether the client was logged on to the internal network or the external network when the call was placed. Select one of the following: <br/>  [All] <br/>  Internal <br/>  External <br/> |
|**Network type** <br/> | Indicates the type of network the client was connected to when the call was placed. Select one of the following: <br/>  [All] <br/>  Wired <br/>  Wireless <br/> |
|**VPN** <br/> | Indicates whether an external client was using a virtual private network (VPN) connection when the call was placed. Select one of the following: <br/>  [All] <br/>  VPN <br/>  Non-VPN <br/> |
   
## Metrics

The following table lists the information provided in the Media Quality Summary Report.
  
**Media Quality Summary Report Metrics: Audio Call Summary**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Call type/Endpoint type** <br/> |No  <br/> | When you click this item, the report shows detailed information about calls based on that type. Call types include: <br/>  UC Peer-to-Peer Calls <br/>  UC Conference Sessions <br/>  PSTN Conference Sessions <br/>  PSTN Calls: Media Bypass <br/>  PSTN Calls (Non-Bypass): UC Leg <br/>  PSTN Calls (Non-Bypass): Gateway Leg <br/>  Other Call Types <br/> |
|**Call volume** <br/> |No  <br/> |Total number of calls per call type.  <br/> |
|**Poor call percentage** <br/> |No  <br/> |Total number of calls classified as poor. A poor call is any call which at least one of the measured metrics exceeded the allowed value (for example, a call that experienced excessive jitter).  <br/> |
|**Call volume (wireless call)** <br/> |No  <br/> |Total number of calls that used a wireless connection.  <br/> |
|**Call volume (VPN call)** <br/> |No  <br/> |Total number of calls that used a VPN connection.  <br/> |
|**Call volume (external call)** <br/> |No  <br/> |Number of calls that used an external connection (that is, a connection outside the internal network).  <br/> |
|**Round trip (ms)** <br/> |No  <br/> |Average amount of (in milliseconds) required for a real-time transport protocol (RTP) packet to travel to another endpoint and then back. Round-trip times of 100 milliseconds or less are considered of acceptable quality.  <br/> High round-trip values can be caused by international call routing, a routing misconfiguration, or an overloaded media server. High round-trip times result in difficulties with two-way, real-time audio conversations.  <br/> |
|**Degradation (MOS)** <br/> |No  <br/> |Average amount of mean opinion score (MOS) degradation experienced during a call. Degradation values can range from a low of 0.0 to a high of 5.0. A value of 0.5 or less represents acceptable degradation. Historically, mean options scores were calculated by having users rate the quality of a call on a scale of 1-to-5. In Skype for Business Server a set of algorithms predict how users would have rated a call.  <br/> High degradation values can be caused by congestion, lack of bandwidth, wireless congestion or interference, or an overloaded media server or endpoint. High degradation results in distorted or lost audio.  <br/> |
|**Packet loss** <br/> |No  <br/> |Average rate of RTP packet loss. (Packet loss occurs when RTP packets, a protocol used for transmitting audio and video across the Internet, failed to reach their destination.) High loss rates are generally caused by congestion, lack of bandwidth, wireless congestion or interference, or an overloaded media server. Packet loss typically results in distorted or lost audio.  <br/> |
|**Jitter (ms)** <br/> |No  <br/> |Average jitter detected between RTP packet arrivals. (Jitter is a measure of the "shakiness" of a call.) High jitter values are typically caused by congestion or an overloaded media server, and result in distorted or lost audio.  <br/> |
|**Healer concealed ratio** <br/> |No  <br/> |Average ratio of concealed audio samples to the total to the total number of samples. (A concealed audio sample is a technique used to smooth out the abrupt transition that would usually be caused by dropped network packets.) High values indicate significant levels of loss concealment applied caused by packet loss or jitter, and results in distorted or lost audio.  <br/> |
|**Healer stretched ratio** <br/> |No  <br/> |Average ratio of stretched audio samples to the total to the total number of samples. (Stretched audio is audio that has been expanded to help maintain call quality when a dropped network packet has been detected.) High values indicate significant levels of sample stretching caused by jitter, and result in audio sounding robotic or distorted.  <br/> |
|**Healer compressed ratio** <br/> |No  <br/> |Average ratio of compressed audio samples to the total number of samples. (Compressed audio is audio that has been compressed to help maintain call quality when a dropped network packet has been detected.) High values indicate significant levels of sample compression caused by jitter, and result in audio sounding accelerated or distorted.  <br/> |
   
**Media Quality Summary Report Metrics: Video Call Summary**

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
|**Outbound packet loss** <br/> |No  <br/> |Real-Time Transport Protocol (RTP) packet loss for outbound packets. (Packet loss occurs when RTP packets, a protocol used for transmitting audio and video across the Internet, failed to reach their destination.) High loss rates are generally caused by congestion, lack of bandwidth, wireless congestion or interference, or an overloaded media server. Packet loss typically results in distorted or lost audio.  <br/> |
|**Frozen frame %** <br/> |No  <br/> |Percentage of "frozen" frames. In a frozen frame, the video stops advancing while the audio portion of the call continues.  <br/> |
|**Outbound avg frame rate** <br/> |No  <br/> |Average frame rate for outbound transmissions during the call.  <br/> |
|**Inbound avg frame rate** <br/> |No  <br/> |Average frame rate for incoming transmissions during the call.  <br/> |
|**Inbound low frame rate %** <br/> |No  <br/> |Percentage of the call where the bit rate for incoming video was low.  <br/> |
|**Client health %** <br/> ||Indicates the relative health of the client device during the call.  <br/> |
   
**Media Quality Summary Report Metrics: Application Sharing Call Summary**

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
|**Avg. RDP tile processing latency** <br/> |No  <br/> |The average RDP tile processing latency in the AS Conferencing Server over the duration of the viewing session. A high average reflects a longer delay in the viewing experience, and includes network latency. An overloaded conferencing server may experience higher average delays.  <br/> |
|**Total spoiled tile %** <br/> |No  <br/> |Total percentage of spoiled RDP tiles.  <br/> |
   

