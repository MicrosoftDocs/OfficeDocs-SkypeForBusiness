---
title: 'Lync Server 2013: Components and topologies for SIP trunking'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Components and topologies for SIP trunking
ms:assetid: 8ed9a9d0-517e-4f36-a131-22cdafa257fa
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398720(v=OCS.15)
ms:contentKeyID: 48184775
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Components and topologies for SIP trunking in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-21_

The following figure depicts the SIP trunking topology in Lync Server.

**SIP trunking topology**

![SIP Trunking Topology](images/Gg398720.669fb55d-7c81-4e21-9421-fabc43d6e064(OCS.15).jpg "SIP Trunking Topology")

As shown in the diagram, an IP virtual private network (VPN) is used for connectivity between the enterprise network and the public switched telephone network (PSTN) service provider. The purpose of this private network is to provide IP connectivity, enhance security, and (optionally) obtain Quality of Service (QoS) guarantees. Because of the nature of a VPN, you do not need to use Transport Layer Security (TLS) for SIP signaling traffic or secure real-time transport protocol (SRTP) for the media traffic. Connections between the enterprise and the service provider therefore consist of plain TCP connections for SIP and plain real-time transport protocol (RTP) (over UDP) for media tunneled through an IP VPN. Ensure that all firewalls between the VPN routers have ports open to allow the VPN routers to communicate, and that the IP addresses on the external edges of the VPN routers are publicly routable.

<div>


> [!IMPORTANT]  
> Contact your service provider to determine whether it provides support for high availability, including failover. If so, you will need to determine the procedures for setting it up. For example, do you need to configure only one IP address and one SIP trunk on each Mediation Server, or do you need to configure multiple SIP trunks on each Mediation Server?<BR>If you have multiple central sites, also ask whether the service provider has the ability to enable connections to and from another central site.



</div>

<div>


> [!NOTE]  
> For SIP trunking, we strongly recommend that you deploy stand-alone Mediation Servers. For details, see <A href="lync-server-2013-deploying-mediation-servers-and-defining-peers.md">Deploying Mediation Servers and defining peers in Lync Server 2013</A> in the Deployment documentation.



</div>

<div>

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

</div>

</div>

<span> </span>

</div>

</div>

</div>

