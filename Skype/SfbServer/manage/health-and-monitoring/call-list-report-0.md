---
title: "Call List Report in Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 9739f9f0-7a37-4844-91d5-f089d2011013
description: "Summary: Learn about the Call List Report used in Skype for Business Server."
---

# Call List Report in Skype for Business Server
 
**Summary:** Learn about the Call List Report used in Skype for Business Server.
  
The Call List Report provides Quality of Experience (QoE) metrics for individual calls made and received in your organization. Note that the actual metrics reported will depend on how you access the Call List report. For example, if you open the report from the [Device Report in Skype for Business Server](device-report.md), you'll see metrics such as the following, metrics that are also reported on the Device Report:
  
- Caller's microphone
    
- Caller's speaker
    
- Callee's microphone
    
- Callee's speaker
    
- Ratio of voice switch time 
    
However, if you open the Call List Report from the [Location Report in Skype for Business Server](location-report.md), you won't see any of those metrics; instead, you'll see metrics like these:
  
- Round trip (ms)
    
- Degradation (MOS)
    
- Packet loss
    
- Jitter (ms)
    
Those are the metrics reported on the Location Report. However, from the Call List Report you can always click the Detail metric to provide complete QoE information for any call.
  
## Accessing the Call List Report

The Call List Report can be accessed from any of the following reports:
  
- The [Location Report in Skype for Business Server](location-report.md) (by clicking the Call volume or Poor call percentage metric)
    
- The [Device Report in Skype for Business Server](device-report.md) (by clicking the Call volume or Poor call percentage metric)
    
- The [Media Quality Summary Report in Skype for Business Server](summary.md) (by clicking the Call volume or Poor call percentage metric)
    
- The [Server Performance Report in Skype for Business Server](server-performance.md) (by clicking the Call volume or Poor call percentage metric)
    
From within the Call List Report you can access the [Call Detail Report in Skype for Business Server](call-detail-report.md) by clicking the Detail metric.
  
## Making the Best Use of the Call List Report

If you can't remember what some of the Call List Report metrics (such as Ratio voice switch time) actually measure, hold your mouse over the metric label; a tool tip will then appear giving you a brief description of the metric.
  
## Filters

None. You cannot filter the Call List Report.
  
## Metrics

The following table lists the information provided in the Call List Report for each call.
  
**Call List Report Metrics**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Details** <br/> |No  <br/> |When you click this item, the report shows additional information on the call.  <br/> |
|**Caller** <br/> |Yes  <br/> |SIP address of the person who initiated the call.  <br/> |
|**Callee** <br/> |Yes  <br/> |SIP address of the person who was called.  <br/> |
|**Start time** <br/> |Yes  <br/> |Date and time that the call started.  <br/> |
|**End time** <br/> |Yes  <br/> |Date and time that the call ended.  <br/> |
|**Caller user agent** <br/> |Yes  <br/> |Software used by the endpoint of the person who initiated the call.  <br/> |
|**Callee user agent** <br/> |Yes  <br/> |Software used by the endpoint of the person who was called.  <br/> |
|**Round trip (ms)** <br/> |Yes  <br/> |Average amount of (in milliseconds) required for a real-time transport protocol (RTP) packet to travel to another endpoint and then back. Round-trip times of 100 milliseconds or less are considered of acceptable quality.  <br/> High round-trip values can be caused by international call routing, a routing misconfiguration, or an overloaded media server. High round-trip times result in difficulties with two-way, real-time audio conversations.  <br/> |
|**Degradation (MOS)** <br/> |Yes  <br/> |Average amount of mean opinion score (MOS) degradation experienced during a call. Degradation values can range from a low of 0.0 to a high of 5.0. A value of 0.5 or less represents acceptable degradation. Historically, mean options scores were calculated by having users rate the quality of a call on a scale of 1-to-5. In Skype for Business Server, a set of algorithms predict how users would have rated a call.  <br/> High degradation values can be caused by congestion, lack of bandwidth, wireless congestion or interference, or an overloaded media server or endpoint. High degradation results in distorted or lost audio.  <br/> |
|**Packet loss** <br/> |Yes  <br/> |Average rate of RTP packet loss. (Packet loss occurs when RTP packets, a protocol used for transmitting audio and video across the Internet, failed to reach their destination.) High loss rates are generally caused by congestion, lack of bandwidth, wireless congestion or interference, or an overloaded media server. Packet loss typically results in distorted or lost audio.  <br/> |
|**Jitter** <br/> |Yes  <br/> |Average jitter detected between RTP packet arrivals. (Jitter is a measure of the "shakiness" of a call.) High jitter values are typically caused by congestion or an overloaded media server, and result in distorted or lost audio.  <br/> |
|**Healer concealed ratio** <br/> |Yes  <br/> |Average ratio of concealed audio samples to the total to the total number of samples. (A concealed audio sample is a technique used to smooth out the abrupt transition that would usually be caused by dropped network packets.) High values indicate significant levels of loss concealment applied caused by packet loss or jitter, and results in distorted or lost audio.  <br/> |
|**Healer stretched ratio** <br/> |Yes  <br/> |Average ratio of stretched audio samples to the total to the total number of samples. (Stretched audio is audio that has been expanded to help maintain call quality when a dropped network packet has been detected.) High values indicate significant levels of sample stretching caused by jitter, and result in audio sounding robotic or distorted.  <br/> |
|**Healer compressed ratio** <br/> |Yes  <br/> |Average ratio of compressed audio samples to the total number of samples. (Compressed audio is audio that has been compressed to help maintain call quality when a dropped network packet has been detected.) High values indicate significant levels of sample compression caused by jitter, and result in audio sounding accelerated or distorted.  <br/> |
|**Connectivity** <br/> |Yes  <br/> | Type of wireless communication link. Typically, this is one of the following: <br/>  Relay <br/>  Direct <br/> |
   

