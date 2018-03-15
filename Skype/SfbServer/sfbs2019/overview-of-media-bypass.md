---
title: "Overview of media bypass in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9ea090b3-f607-46f7-97dd-2510052524e5
description: "Media bypass is useful when you want to minimize the number of Mediation Servers deployed. Typically, a Mediation Server pool will be deployed at a central site, and it will control gateways at branch sites. Enabling media bypass allows media for public switched telephone network (PSTN) calls from clients at branch sites to flow directly through the gateways at those sites. Lync Server 2013 outbound call routes and Enterprise Voice policies must be properly configured so that PSTN calls from clients at a branch site are routed to the appropriate gateway."
---

# Overview of media bypass in Lync Server 2013
[]
Media bypass is useful when you want to minimize the number of Mediation Servers deployed. Typically, a Mediation Server pool will be deployed at a central site, and it will control gateways at branch sites. Enabling media bypass allows media for public switched telephone network (PSTN) calls from clients at branch sites to flow directly through the gateways at those sites. Lync Server 2013 outbound call routes and Enterprise Voice policies must be properly configured so that PSTN calls from clients at a branch site are routed to the appropriate gateway.
  
Wi-Fi networks typically experience more packet loss than wired networks. Recovery from this packet loss is not typically something that can be accommodated by gateways. Therefore, we recommend that you evaluate the quality of a Wi-Fi network before determining whether bypass should be enabled for a wireless subnet. There is a tradeoff in latency reduction versus recovery from packet loss to consider, as well. RTAudio, a codec which is available for calls that do not bypass the Mediation Server, is better suited for handling packet loss.
  
After your Enterprise Voice structure is in place, planning for media bypass is straightforward.
  
- If you have a centralized topology without WAN links to branch sites, you can enable global media bypass, because fine-tuned control is unnecessary.
    
- If you have a distributed topology that consists of one or more network regions and their affiliated branch sites, determine the following:
    
  - Whether your Mediation Server peers are able to support the capabilities required for media bypass.
    
  - Which sites in each network region are well-connected.
    
  - Which combination of media bypass and call admission control is appropriate for your network.
    
When you enable media bypass, a unique bypass ID is automatically generated for a network region, and for all network sites without bandwidth constraints within that region. Sites with bandwidth constraints within the region and sites connected to the region over WAN links with bandwidth constraints are each assigned their own unique bypass IDs.
  
When a user makes a call to the PSTN, the Mediation Server compares the bypass ID of the client subnet with the bypass ID of the gateway subnet. If the two bypass IDs match, media bypass is used for the call. If the bypass IDs do not match, media for the call must flow through the Mediation Server.
  
When a user receives a call from the PSTN, the user's client compares its bypass ID to that of the PSTN gateway. If the two bypass IDs match, media flows directly from the gateway to the client, bypassing the Mediation Server.
  
Only Lync 2010 or above clients and devices support media bypass interactions with a Mediation Server.
  
> [!IMPORTANT]
> In addition to enabling media bypass globally, you must enable media bypass individually on each PSTN trunk. If bypass is enabled globally, but is not enabled for a particular PSTN trunk, media bypass will not be invoked for any calls involving that PSTN trunk. In addition, when media bypass is set to **Use Site and Region Information**, you must associate all routable subnets with the sites in which they are located. If there are routable subnets within a site for which bypass is not wanted, these subnets should be grouped within a new site before you enable media bypass. Doing so will assure that the unroutable subnets are assigned a different bypass ID. 
  
## See also

#### 

[Media bypass modes in Lync Server 2013](media-bypass-modes.md)
  
[Media bypass and call admission control in Lync Server 2013](media-bypass-and-call-admission-control.md)
  
[Technical requirements for media bypass in Lync Server 2013](technical-requirements-for-media-bypass.md)

