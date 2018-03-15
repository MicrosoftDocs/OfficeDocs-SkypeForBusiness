---
title: "Components and topologies for SIP trunking in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8ed9a9d0-517e-4f36-a131-22cdafa257fa
description: "The following figure depicts the SIP trunking topology in Lync Server."
---

# Components and topologies for SIP trunking in Lync Server 2013
[]
The following figure depicts the SIP trunking topology in Lync Server.
  
**SIP trunking topology**

![SIP Trunking Topology](media/SIPTrunkingTopology.jpg)
  
As shown in the diagram, an IP virtual private network (VPN) is used for connectivity between the enterprise network and the public switched telephone network (PSTN) service provider. The purpose of this private network is to provide IP connectivity, enhance security, and (optionally) obtain Quality of Service (QoS) guarantees. Because of the nature of a VPN, you do not need to use Transport Layer Security (TLS) for SIP signaling traffic or secure real-time transport protocol (SRTP) for the media traffic. Connections between the enterprise and the service provider therefore consist of plain TCP connections for SIP and plain real-time transport protocol (RTP) (over UDP) for media tunneled through an IP VPN. Ensure that all firewalls between the VPN routers have ports open to allow the VPN routers to communicate, and that the IP addresses on the external edges of the VPN routers are publicly routable.
  
> [!IMPORTANT]
> Contact your service provider to determine whether it provides support for high availability, including failover. If so, you will need to determine the procedures for setting it up. For example, do you need to configure only one IP address and one SIP trunk on each Mediation Server, or do you need to configure multiple SIP trunks on each Mediation Server? > If you have multiple central sites, also ask whether the service provider has the ability to enable connections to and from another central site. 
  
> [!NOTE]
> For SIP trunking, we strongly recommend that you deploy stand-alone Mediation Servers. For details, see [Deploying Mediation Servers and defining peers in Lync Server 2013](deploying-mediation-servers-and-defining-peers.md) in the Deployment documentation. 
  
## Securing the Mediation Server for SIP Trunking

For security purposes, you should set up a virtual LAN (VLAN) for each connection between the two VPN routers. The actual process for setting up a VLAN varies from one router manufacturer to another. For details, contact your router vendor.
  
We recommend that you follow these guidelines:
  
- Set up a virtual LAN (VLAN) between the Mediation Server and the VPN router in the perimeter network (also known as DMZ, demilitarized zone, and screened subnet).
    
- Do not allow broadcast or multicast packets to be transferred from the router to the VLAN.
    
- Block any routing rules that route traffic from the router to anywhere but the Mediation Server.
    
If you use a VPN server, we recommend that you follow these guidelines:
  
- Set up a VLAN between the VPN server and the Mediation Server.
    
- Do not allow broadcast or multicast packets to be transmitted from the VPN server to the VLAN.
    
- Block any routing rule that routes VPN server traffic to anywhere but the Mediation Server.
    
- Encrypt data on the VPN by using generic routing encapsulation (GRE).
    

