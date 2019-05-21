---
title: "Call Detail Report in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 38862e35-3fec-41b9-a035-0b301942d446
description: "Summary: Learn about the Call Detail Report used in Skype for Business Server."
---

# Call Detail Report in Skype for Business Server
 
**Summary:** Learn about the Call Detail Report used in Skype for Business Server.
  
The Call Detail Report provides a detailed look at an individual call; the report includes nearly all the Quality of Experience metrics and statistics collected by Skype for Business Server, divided into report sections such as:
  
- Call Information 
    
- Caller Device and Signal Metrics
    
- Callee Device and Signal metrics
    
- Caller Client Event
    
- Callee Client Event
    
- Audio Stream (Caller to Callee)
    
- Video Stream (Caller to Callee)
    
- Audio Stream (Callee to Caller)
    
- Video Stream (Callee to Caller)
    
Keep in mind that the categories and the metrics you see on a given report depend on two things: the type of session and the type of endpoints used in the session. For example, an audio-only call will not report metrics for video streams; that's because the call didn't have a video stream. Likewise, you might have a report that lists caller statistics but not callee statistics. That's typically because the callee was not using a SIP-compliant device. Endpoints are responsible for reporting statistics at the end of a call; however, a cell phone (which knows nothing about SIP or SIP statistics) is unable to report that kind of information. If you call someone and they answer you on their cell phone, you will not get a report from that cell phone when the call ends.
  
The Call Detail Report is most useful when you are trying to determine exactly why a given call experienced media quality problems.
  
## Accessing the Call Detail Report

The Call Detail Report can be accessed from any of the following reports:
  
- The [Location Report in Skype for Business Server (location-report.md) (by clicking either the Call volume or the Poor call percentage metric)
    
- The [Media Quality Summary Report in Skype for Business Server (summary.md) (by clicking either the Call volume or Poor call percentage metric)
    
- The [Media Quality Comparison Report in Skype for Business Server](comparison.md) (by clicking the [Call List Report in Skype for Business Server](call-list-report-0.md) and then clicking the Detail metric).
    
- The [Server Performance Report in Skype for Business Server](server-performance.md) (by clicking either the Call volume or Poor call percentage metric)
    
- The [Call List Report in Skype for Business Server](call-list-report-0.md) (by clicking the Detail metric)
    
From within the Call Detail Report you can access the [Device Report in Skype for Business Server](device-report.md) by clicking either of the following metrics:
  
- Capture device
    
- Render device
    
You can also access the Server Media Quality Trend Report by clicking the A/V edge server metric.
  
## Making the Best Use of the Call Detail Report

The Call Detail Report typically includes over 250 different metrics, including such items as Microphone timestamp drift, Low SNR time, and Near end to echo time. If you can't remember what all of these metrics actually measure, try holding your mouse over the metric label; often-times, a tooltip will appear describing that metric.
  
If you have problems locating a metric, type part of the metric label in the search box, and then click **Find**. For example, if you can't find the Low SNR time metric, type SNR in the search box, and then click **Find**.
  
Note that the report only tracks information about a call. The call itself is not recorded.
  
## Filters

None. You cannot filter the Call Detail Report.
  
## Metrics

The following table lists the information provided in the Call Detail Report for each call.
  
**Call Detail Report Metrics**

|**Name**|**Can you sort on this item?**|**Description**|
|:-----|:-----|:-----|
|**Caller PAI** <br/> |No  <br/> |P-Asserted-Identity of the user who initiated the call. The P-Asserted-Identity is used to convey the proven identity of a user within a trusted network.  <br/> |
|**Caller URI** <br/> |No  <br/> |SIP address of the user who initiated the call.  <br/> |
|**Caller endpoint** <br/> |No  <br/> |Device used to make the call.  <br/> |
|**Caller user agent** <br/> |No  <br/> |Software used on the device that made the call.  <br/> |
|**Call start** <br/> |No  <br/> |Date and time that the call was initially placed.  <br/> |
|**Mediation Server bypass call** <br/> |No  <br/> |Indicates whether the call connected to a PSTN voice gateway or qualified IP-PBX without passing through the Mediation Server.  <br/> |
|**Caller OS** <br/> |No  <br/> |Operating system of the caller's computer.  <br/> |
|**Caller CPU** <br/> |No  <br/> |CPU installed in the computer of the user who initiated the call.  <br/> |
|**Caller CPU core number** <br/> |No  <br/> |Processor number in the computer used by the person who initiated the call.  <br/> |
|**Caller CPU speed** <br/> |No  <br/> |Clock speed of the CPU of the computer used by the person who initiated the call.  <br/> |
|**Caller CPU virtualization** <br/> |No  <br/> |Virtualization (if any) used on the computer used by the person who initiated the call.  <br/> |
|**Callee PAI** <br/> |No  <br/> |P-Asserted-Identity of the user who was invited to join the call. The P-Asserted-Identity is used to convey the proven identity of a user within a trusted network.  <br/> |
|**Callee URI** <br/> |No  <br/> |SIP address of the user who was called.  <br/> |
|**Callee endpoint** <br/> |No  <br/> |Device used to receive the call.  <br/> |
|**Callee user agent** <br/> |No  <br/> |Software used on the device that received the call.  <br/> |
|**Duration** <br/> |No  <br/> |Length of time for the call.  <br/> |
|**Media bypass warning flag** <br/> |No  <br/> |Warning issued when the Mediation Server was bypassed.  <br/> |
|**Callee OS** <br/> |No  <br/> |Operating system of the computer for the user who was called.  <br/> |
|**Callee CPU** <br/> |No  <br/> |CPU installed in the computer of the user who was called.  <br/> |
|**Callee core number** <br/> |No  <br/> |Processor number in the computer used by the person who was called.  <br/> |
|**Callee CPU speed** <br/> |No  <br/> |Clock speed of the CPU of the computer used by the person who was called.  <br/> |
|**Callee CPU virtualization** <br/> |No  <br/> |Virtualization (if any) used on the computer used by the person who was called.  <br/> |
   

