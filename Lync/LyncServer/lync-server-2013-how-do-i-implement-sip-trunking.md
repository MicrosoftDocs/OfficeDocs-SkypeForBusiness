---
title: 'Lync Server 2013: How do I implement SIP trunking?'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: How do I implement SIP trunking?
ms:assetid: 273a22b1-8a4c-4187-acf8-c57d5c6598ce
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425743(v=OCS.15)
ms:contentKeyID: 48183666
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# How do I implement SIP trunking in Lync Server 2013?

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-18_

To implement SIP trunking, you must route the connection through a Mediation Server, which acts as a proxy for communications sessions between Lync Server 2013 clients and the service provider and transcodes media, when necessary.

Each Mediation Server has an internal network interface and an external network interface. The internal interface connects to the Front End Servers. The external interface is commonly called the gateway interface because it has traditionally been used to connect the Mediation Server to a public switched telephone network (PSTN) gateway or an IP-PBX. To implement a SIP trunk, you connect the external interface of the Mediation Server to the external edge component of the ITSP.

<div>


> [!NOTE]  
> The external edge component of the ITSP could be a Session Border Controller (SBC), a router, or a gateway.



</div>

For details about Mediation Servers, see [Mediation Server component in Lync Server 2013](lync-server-2013-mediation-server-component.md).

<div>

## Centralized vs. Distributed SIP Trunking

*Centralized* SIP trunking routes all Voice over Internet Protocol (VoIP) traffic, including branch site traffic, through your central site. The centralized deployment model is simple, cost-effective, and is generally the recommended approach for implementing SIP trunks with Lync Server 2013.

*Distributed* SIP trunking is a deployment model in which you implement a local SIP trunk at one or more branch sites. VoIP traffic is then routed from the branch site directly to a service provider without going through the central site.

Distributed SIP trunking is required only in the following cases:

  - The branch site requires survivable phone connectivity (for example, if the WAN goes down). This requirement should be analyzed for each branch site; some of your branches may require redundancy and failover, whereas others may not.

  - Resiliency is required between two central sites. You need to make sure that a SIP trunk terminates at each central site. For example, if you have Dublin and Tukwila central sites and both use only one site’s SIP trunk, if the trunk goes down, the other site’s users cannot make PSTN calls.

  - The branch site and central site are in different countries/regions. For compatibility and legal reasons, you need at least one SIP trunk per country/region. For example, in the European Union, communications cannot leave a country/region without terminating locally at a centralized point.

Depending on the geographical location of sites and how much traffic you anticipate within your enterprise, you may not want to route all users through the central SIP trunk, or you may opt to route some users through a SIP trunk at their branch site. To analyze your needs, answer the following questions:

  - How big is each site (that is, how many users are enabled for Enterprise Voice)?

  - Which direct inward dialing (DID) numbers at each site get the most phone calls?

The decision whether to deploy centralized or distributed SIP trunking requires a cost-benefit analysis. In some cases, it may be advantageous to opt for the distributed deployment model even if it is not required. In a completely centralized deployment, all branch site traffic is routed over WAN links. Instead of paying for the bandwidth required for WAN linking, you may want to use distributed SIP trunking. For example, you may want to deploy a Standard Edition server at a branch site with federation to the central site, or you may want to deploy a Survivable Branch Appliance or a Survivable Branch Server with a small gateway.

<div>


> [!NOTE]  
> For details about distributed SIP trunking, see <A href="lync-server-2013-branch-site-sip-trunking.md">Branch site SIP trunking in Lync Server 2013</A>.



</div>

</div>

<div>

## Supported SIP Trunking Connection Types

Lync Server supports the following connection types for SIP trunking:

  - Multiprotocol Label Switching (MPLS) is a private network that directs and carries data from one network node to the next. The bandwidth in an MPLS network is shared with other subscribers, and each data packet is assigned a label to distinguish one subscriber’s data from another’s. This connection type does not require a virtual private network (VPN). A potential drawback is that excessive IP traffic can interfere with VoIP operation unless VoIP traffic is given priority.

  - A private connection with no other traffic—for example, a leased fiber-optic connection or T1 line—is typically the most reliable and secure connection type. This connection type provides the highest call-carrying capacity, but it is typically the most expensive. VPN is not required. Private connections are appropriate for organizations with high call volumes or stringent security and availability requirements.

  - The Internet is the least expensive connection type, but it is also the least reliable. Internet connection is the only Lync Server SIP trunking connection type that requires VPN.

<div>

## Selecting a Connection Type

The most appropriate SIP trunking connection type for your enterprise depends on your needs and your budget.

  - For a mid-size or larger enterprise, an MPLS network usually provides the greatest value. It can provide the necessary bandwidth at a cheaper rate than a specialized private network.

  - Large enterprises may require a private fiber-optic, T1, T3 or higher connection (E1, E3 or higher in the European Union).

  - For a small enterprise or branch site with low call volume, SIP trunking through the Internet may be the best choice. This connection type is not recommended for mid-size or larger sites.

</div>

</div>

<div>

## Bandwidth Requirements

The amount of bandwidth your implementation requires depends on call capacity (the number of concurrent calls you must be able to support). You need to consider bandwidth availability, so that you can take full advantage of the peak capacity that you have paid for. Use the following formula to calculate SIP trunk peak bandwidth requirement:

SIP Trunk Peak Bandwidth = Max Simultaneous Calls x (64 kbps + header size)

<div>


> [!NOTE]  
> Header size is 20 bytes maximum.



</div>

</div>

<div>

## Codec Support

Lync Server 2013 supports only the following codecs:

  - G.711 a-law (used primarily outside North America)

  - G.711 µ-law (used in North America)

</div>

<div>

## Internet Telephony Service Provider

How you implement the service provider side of a SIP trunk connection varies from one ITSP to another. For deployment information, contact your service provider. For a list of certified SIP trunking service providers, see [Microsoft Unified Communications Open Interoperability Program website](http://go.microsoft.com/fwlink/?linkid=287029).

For details about Microsoft certified SIP trunking providers, contact your Microsoft representative.

<div>


> [!IMPORTANT]  
> You must use a Microsoft certified service provider to ensure that your ITSP supports all of the functionality that traverses the SIP trunk (for example, setting up and managing sessions and supporting all of the extended VoIP services). Microsoft technical support does not extend to configurations that use noncertified providers. If you currently use an Internet service provider that is not certified for SIP trunking, you can opt to continue using that provider as your ISP and use a provider certified by Microsoft for SIP trunking.



</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

