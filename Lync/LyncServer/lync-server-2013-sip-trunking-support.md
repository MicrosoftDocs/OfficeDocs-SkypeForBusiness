---
title: Lync Server 2013 SIP trunking support
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: SIP trunking support
ms:assetid: e3042831-e8d8-4ea2-baa2-1a697401ffa0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg399005(v=OCS.15)
ms:contentKeyID: 48185714
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# SIP trunking support in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-03_

If you plan to use Enterprise Voice with SIP trunking, you must deploy a Mediation Server and make sure that other infrastructure and components meet the support requirements appropriate to your deployment model. For details about determining whether to implement SIP trunking, see [Overview of SIP trunking in Lync Server 2013](lync-server-2013-overview-of-sip-trunking.md) in the Planning documentation.

You can use the Microsoft Unified Communications Open Interoperability Program for enterprise telephony infrastructure to find qualified public switched telephone network (PSTN) gateways, IP-PBXs, and SIP trunking services, including qualified IP telephony service providers. For details, see the Microsoft Unified Communications Open Interoperability Program website at [http://go.microsoft.com/fwlink/p/?LinkId=203309](http://go.microsoft.com/fwlink/p/?linkid=203309).

<div>

## Mediation Server Support

To implement SIP trunking, you must route the connection through a Mediation Server, which acts as a proxy for communications sessions between Lync Server 2013 clients and the service provider. The Mediation Server decodes the media traffic from clients and servers and re-encodes it before sending it to the service provider. The re-encoding is needed because SIP trunks do not support some codecs used, such as Real Time Audio (RTA) or Interactive Connectivity Establishment (ICE) protocol negotiation for firewall traversal.

Each Mediation Server can have two network adapters, which provide an internal and an external network interface. The external interface is commonly called the gateway interface because, traditionally, it has been used to connect to a PSTN gateway or an IP-PBX. To implement a SIP trunk, you connect the external interface to a Session Border Controller (SBC) at a service provider.

</div>

<div>

## Centralized vs. Distributed SIP Trunking

*Centralized* SIP trunking routes all Voice over Internet Protocol (VoIP) traffic, including branch site traffic, through your data center. The centralized deployment model is simple, cost-effective, and is generally the preferred approach for implementing SIP trunks with Lync Server 2013.

Depending on usage patterns within your enterprise, you may not want to route all users through the centralized SIP trunk. To analyze your needs, answer the following questions:

  - How big is each site? How many users?

  - Which Direct Inward Dialing (DID) numbers at each site get the most phone calls?

*Distributed* SIP trunking is a deployment model in which you implement a local SIP trunk at one or more branch sites. VoIP traffic is then routed from the branch site directly to their service provider, without going through your data center.

Distributed SIP trunking is required only in the following cases:

  - The branch site requires survivable phone connectivity (for example, if the WAN goes down). If the branch does need redundancy and failover, the service provider will charge more and the configuration will take longer. This should be analyzed for each branch site. Some of your branches may require redundancy and failover, while others may not.

  - The branch site and data center are in different countries/regions. For compatibility and legal reasons, you need at least one SIP trunk per country/region.

Deciding whether to deploy centralized or distributed SIP trunking requires a cost-benefit analysis. In some cases, it may be advantageous to opt for the distributed deployment mode, even if it is not required. In a completely centralized deployment, all branch site traffic is routed over WAN links. Instead of paying for the bandwidth required for WAN linking, you may want to use distributed SIP trunking.

<div>


> [!NOTE]  
> For details about why and how you might use distributed SIP trunking, see <A href="lync-server-2013-branch-site-sip-trunking.md">Branch site SIP trunking in Lync Server 2013</A> in the Planning documentation.



</div>

</div>

<div>

## Supported SIP Trunking Connection Types

Lync Server 2013 supports the following connection types for SIP trunking:

  - Multiprotocol Label Switching (MPLS) is a private network that directs and carries data from one network node to the next. The bandwidth in an MPLS network is shared with other subscribers, and each data packet is assigned a label to distinguish one subscriber’s data from another’s. This connection type does not require VPN. A potential drawback is that excessive IP traffic can interfere with VoIP operation unless VoIP traffic is given priority.

  - A private connection with no other traffic is typically the most reliable and secure connection type (for example, a leased fiber-optic connection or T1 line). This connection type provides the highest call-carrying capacity, but is typically the most expensive. VPN is not required. Private connections are appropriate for organizations with high call volumes or stringent security and availability requirements.

  - The public Internet is the least expensive connection type, but also the least reliable, and the one with the lowest call-carrying capacity. Your Internet Telephony Service Provider (ITSP) can help secure this SIP trunk connection type if it supports Transport Layer Security (TLS) and Secure Real-Time Transport Protocol (SRTP) to encrypt signaling and media traffic. If you cannot configure a SIP trunk connection through the Internet to use TLS and SRTP, we strongly recommend that you use a VPN tunnel to provide a more secure connection. Contact your ITSP to determine whether it provides support for TLS with SRTP.

<div>

## Selecting a Connection Type

The most appropriate SIP trunking connection type for your enterprise depends on your needs and your budget.

  - For a mid-size or larger enterprise, an MPLS network generally provides the most value. It can provide the necessary bandwidth at a cheaper rate than a specialized private network.

  - Large enterprises may require a private fiber-optic or T1 connection.

  - For a small enterprise or branch site with low call volume, SIP trunking through the Internet may be the best choice. However, this connection type is not recommended for mid-size or larger sites.

</div>

</div>

<div>

## Codec Support

The service provider proxy must support the following codecs:

  - G.711 a-law (used primarily outside North America)

  - G.711 µ-law (used in North America)

</div>

</div>

<span> </span>

</div>

</div>

</div>

