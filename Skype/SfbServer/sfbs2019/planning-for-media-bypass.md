---
title: "Planning for media bypass in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8ac732b6-8538-4d7b-b1a9-2035e419dac2
description: "Media bypass refers to removing the Mediation Server from the media path whenever possible for calls whose signaling traverses the Mediation Server."
---

# Planning for media bypass in Lync Server 2013
[]
Media bypass refers to removing the Mediation Server from the media path whenever possible for calls whose signaling traverses the Mediation Server.
  
Media bypass can improve voice quality by reducing latency, needless translation, possibility of packet loss, and the number of points of potential failure. Scalability can be improved, because elimination of media processing for bypassed calls reduces the load on the Mediation Server. This reduction in load complements the ability of the Mediation Server to control multiple gateways.
  
 Where a branch site without a Mediation Server is connected to a central site by one or more WAN links with constrained bandwidth, media bypass lowers the bandwidth requirement by allowing media from a client at a branch site to flow directly to its local gateway without first having to flow across the WAN link to a Mediation Server at the central site and back. 
  
By relieving the Mediation Server from media processing, media bypass may also reduce the number of Mediation Servers that an Enterprise Voice infrastructure requires.
  
The following figure shows basic media and signaling pathways in topologies with and without media bypass.
  
**Media and signaling pathways with and without media bypass**

![Voice CAC Media Bypass Connection Enforcement](media/Plan_CS_VoiceCAC_enforcementofconnectionstoPSTN.jpg)
  
As a general rule, enable media bypass wherever possible.
  
## In this section

- [Overview of media bypass in Lync Server 2013](overview-of-media-bypass.md)
    
- [Media bypass modes in Lync Server 2013](media-bypass-modes.md)
    
- [Media bypass and call admission control in Lync Server 2013](media-bypass-and-call-admission-control.md)
    
- [Technical requirements for media bypass in Lync Server 2013](technical-requirements-for-media-bypass.md)
    
## Related sections

[Deploying advanced Enterprise Voice features in Lync Server 2013](deploying-advanced-enterprise-voice-features.md)
  
## See also

#### 

[Configure a trunk with media bypass in Lync Server 2013](configure-a-trunk-with-media-bypass.md)
#### 

[Global media bypass options in Lync Server 2013](global-media-bypass-options.md)

