---
title: "Planning for call admission control in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ca367138-adf5-4119-bc40-5ddf335ed22f
description: "For unified communications (UC) applications that are IP-based, such as telephony, video, and application sharing, the available bandwidth of enterprise networks is not generally considered to be a limiting factor within LAN environments. However, on WAN links that interconnect sites, network bandwidth can be limited. When an influx of network traffic oversubscribes a WAN link, current mechanisms such as queuing, buffering, and packet dropping are used to resolve the congestion. The extra traffic is typically delayed until the network congestion eases or, if necessary, the traffic is dropped. For conventional data traffic in such situations, the receiving client can recover. For real-time traffic such as unified communications, network congestion cannot be resolved in this manner, because the unified communications traffic is sensitive to both latency and packet loss. Congestion on the WAN can result in a poor Quality of Experience (QoE) for users. For real-time traffic in congested conditions, it is better to deny calls than to provide connections with poor quality."
---

# Planning for call admission control in Lync Server 2013
[]
For unified communications (UC) applications that are IP-based, such as telephony, video, and application sharing, the available bandwidth of enterprise networks is not generally considered to be a limiting factor within LAN environments. However, on WAN links that interconnect sites, network bandwidth can be limited. When an influx of network traffic oversubscribes a WAN link, current mechanisms such as queuing, buffering, and packet dropping are used to resolve the congestion. The extra traffic is typically delayed until the network congestion eases or, if necessary, the traffic is dropped. For conventional data traffic in such situations, the receiving client can recover. For real-time traffic such as unified communications, network congestion cannot be resolved in this manner, because the unified communications traffic is sensitive to both latency and packet loss. Congestion on the WAN can result in a poor Quality of Experience (QoE) for users. For real-time traffic in congested conditions, it is better to deny calls than to provide connections with poor quality.
  
Call admission control (CAC) determines whether there is sufficient network bandwidth to establish a real-time session of acceptable quality. In Lync Server 2013, CAC controls real-time traffic only for audio and video, but it does not affect data traffic. If the default WAN path does not have the required bandwidth, CAC can attempt to route the call through an Internet path or the public switched telephone network (PSTN). CAC is available only in Lync Server.
  
This section describes the call admission control functionality and explains how to plan for CAC.
  
> [!NOTE]
> Lync Server has three advanced Enterprise Voice features: call admission control (CAC), emergency services (E9-1-1), and media bypass. For an overview of planning information that is common to all three of these features, see [Network settings for the advanced Enterprise Voice features in Lync Server 2013](network-settings-for-the-advanced-enterprise-voice-features.md). 
  
## In this section

- [Overview of call admission control in Lync Server 2013](overview-of-call-admission-control.md)
    
- [Defining your requirements for call admission control in Lync Server 2013](defining-your-organization-s-requirements-for-call-admission-control.md)
    
- [Example: Gathering your requirements for call admission control in Lync Server 2013](example-gathering-your-organization-s-requirements-for-call-admission-control.md)
    
- [Components and topologies for CAC in Lync Server 2013](components-and-topologies-for-cac.md)
    
- [Best practices for call admission control in Lync Server 2013](best-practices-for-call-admission-control.md)
    
- [Deployment checklist for call admission control in Lync Server 2013](deployment-checklist-for-call-admission-control.md)
    

