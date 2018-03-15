---
title: "Monitoring group chat in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: bddcf0be-ebf3-46bc-90c7-2576877734fb
description: "We highly recommend running the most recent Cumulative Server Update Installer available on the Microsoft Download Center for performance improvements."
---

# Monitoring group chat in Lync Server 2013
[]
We highly recommend running the most recent [Cumulative Server Update Installer](https://support.microsoft.com/kb/968802) available on the Microsoft Download Center for performance improvements. 
  
Assuming you are running latest cumulative update, use the following stress test table for metrics to understand if your Group Chat Servers are running at optimal health.
  
**Test environment and user model**

||
|:-----|
|Three Group Chat Servers in a Group Chat pool, each with 8 GB memory and 8 processors.  <br/> |
|Two Lync Server 2013 Front Ends in Enterprise Edition.  <br/> |
|60,000 concurrent users across three Group Chat Servers.  <br/> |
|25,000 channels hosted by Group Chat Pool.  <br/> |
| Channel Size:  <br/>  Small Channel Size: 30  <br/>  Medium Channel Size: 150  <br/>  Large Channel Size: 2500  <br/> |
| Channel Count:  <br/>  Number small channels: 24,000  <br/>  Number medium channels 800  <br/>  Number large channels 24  <br/>  Total Channels 24,824  <br/> |
| Invite channels:  <br/>  Half the channels were invite channels  <br/> |
| Number of channels a user joins:  <br/>  Small: 12  <br/>  Medium: 2  <br/>  Large: 1  <br/> |
| Join rate:  <br/>  10 total/second, 3.33/second per server  <br/> |
| Logout rate:  <br/>  10 total/second, 3.33/second per server  <br/> |
| Chat rate:  <br/>  20 total/second, 6.66/second per server  <br/> |
   
> [!IMPORTANT]
> The following performance counter numbers will likely vary when different hardware specifications or user profiles are used. 
  
**Performance counter to be monitored**

|**Performance Counter**|**Thresholds**|
|:-----|:-----|
|Process(ChannelService)-\>%Processor Time  <br/> |Min: 0  <br/> |
   

