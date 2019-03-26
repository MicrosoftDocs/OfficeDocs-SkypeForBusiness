---
title: 'Lync Server 2013: Defining your requirements for call admission control'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Defining your organization's requirements for call admission control
ms:assetid: 5122171a-a5b0-4059-b033-846caec10d1e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398334(v=OCS.15)
ms:contentKeyID: 48184104
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Defining your requirements for call admission control in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-10-28_

Planning for call admission control (CAC) requires detailed information about your enterprise network topology. To help plan your call admission control policies, follow these steps.

1.  Identify the hubs/backbones (called *network regions*) within your enterprise network.

2.  Identify the offices or locations (called *network sites*) within each network region.

3.  Determine the network route between every pair of network regions.

4.  Determine the bandwidth limits for each WAN link.
    
    <div>
    

    > [!NOTE]  
    > Bandwidth limits refer to how much of the bandwidth on a WAN link is allocated to Enterprise Voice and audio/video traffic. When a WAN link is described as “bandwidth-constrained,” the WAN link has a bandwidth limit that is lower than the expected peak traffic over the link.

    
    </div>

5.  Identify the IP subnets that are assigned to each network site.

To explain these concepts, we’ll use the example network topology shown in the following figure.

**Example topology for call admission control**

![Litware Inc. Network Topology Example](images/Gg398334.477f3b52-2973-4026-9bc0-b1c6bf9f4803(OCS.15).jpg "Litware Inc. Network Topology Example")

<div>


> [!NOTE]  
> All network sites are associated with a network region. For example, Portland, Reno, and Albuquerque are included in the North America region. In this figure, only WAN links that have CAC policies applied are shown, with bandwidth limits. The network sites of Chicago, New York, and Detroit are shown inside the North America region oval because they are not bandwidth-constrained, and therefore do not require CAC policies.



</div>

The components of this example topology are explained in the following sections. For details about how this topology was planned, including the bandwidth limits, see [Example: Gathering your requirements for call admission control in Lync Server 2013](lync-server-2013-example-of-gathering-your-requirements-for-call-admission-control.md).

<div>

## Identify Network Regions

A network region represents a network backbone or a network hub.

A network backbone or hub is a part of computer network infrastructure that interconnects different parts of the network, providing a path for the exchange of information between different LANs or subnets. A backbone can tie together diverse networks from a small location to a wide geographic area. The backbone's capacity is typically greater than that of the networks that connect to it.

Our example topology has three network regions: North America, EMEA, and APAC. A network region contains a collection of network sites (see the definition of network sites later in this topic). Work with your network operations team to identify your network regions.

</div>

<div>

## Associating a Central Site with each Network Region

CAC requires that a Lync Server central site is defined for each network region. The central site is selected with the best network connectivity and highest bandwidth to all the other sites within that network region. The preceding example of network topology shows three network regions, each with a central site that manages CAC decisions. From the preceding example, the appropriate association is shown in the following table.

<div>


> [!NOTE]  
> Central sites do not necessarily correspond to network sites. In the examples in this documentation, some central sites—Chicago, London, and Beijing—share the same name as the network sites. However, even if a central site and network site share the same name, the central site is an element of the Lync Server topology, whereas the network site is a part of the overall network in which the Lync Server topology resides.



</div>

### Network regions, central sites, and network sites

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Network Region</th>
<th>Central Site</th>
<th>Network Sites</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>North America</p></td>
<td><p>Chicago</p></td>
<td><p>Chicago</p>
<p>New York</p>
<p>Detroit</p>
<p>Portland</p>
<p>Reno</p>
<p>Albuquerque</p></td>
</tr>
<tr class="even">
<td><p>EMEA</p></td>
<td><p>London</p></td>
<td><p>London</p>
<p>Cologne</p></td>
</tr>
<tr class="odd">
<td><p>APAC</p></td>
<td><p>Beijing</p></td>
<td><p>Beijing</p>
<p>Manila</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Identify Network Sites

A network site represents a location where your organization has a physical venue—for example, offices, a set of buildings, or a campus. A physical venue with a LAN and has WAN connectivity to other sites is considered a network site. Start by inventorying all of your organization’s offices. In our example topology, the North America network region consists of the following network sites: New York, Chicago, Detroit, Portland, Reno, and Albuquerque.

You must associate every network site with a network region. Depending on whether the network site has a constrained WAN link, a bandwidth policy is associated with the network site. For details about CAC policies and the bandwidth that you allocate by using them, see "Define Bandwidth Policies" later in this topic. To configure CAC, you associate network sites with network regions, and then you create bandwidth-allocating policies to apply to the bandwidth-constrained connections between a given site or region and the WAN connections between the sites and regions.

</div>

<div>

## Identify Network Links

Network links represent connections to the physical WAN that links different regions and sites. In our example topology, there are two regional network links, five network links between regions and sites, and one network link between two sites.

The two regional links are between North America and EMEA, represented as NA-EMEA-LINK, and between APAC and EMEA, represented as EMEA-APAC-LINK.

The site links are indicated by the lines connecting Portland, Reno, and Albuquerque to the North America region, Manila to the APAC region, and Cologne to the EMEA region. The line between Reno and Albuquerque shows a direct network link between these two sites.

</div>

<div>

## Define Bandwidth Policies

Work with your network operations team to determine how much WAN bandwidth is available for real-time audio and video traffic across the WAN links in your organization. Bandwidth policies are typically applied to WAN links if the bandwidth usage is constrained; that is, if it expected to be more than the bandwidth that can be allocated for audio and video modalities.

CAC *bandwidth policies* define the maximum bandwidth that can be reserved for real-time audio and video modalities. Since CAC does not limit the bandwidth of other traffic, it cannot prevent other data traffic such as a large file transfer, music streaming, from using up all of the network bandwidth.

CAC bandwidth policies can define any or all of the following:

  - Maximum total bandwidth allocated for audio.

  - Maximum total bandwidth allocated for video.

  - Maximum bandwidth allocated for a single audio call (session).

  - Maximum bandwidth allocated for a single video call (session).

<div>


> [!NOTE]  
> All CAC bandwidth values represent the maximum <EM>unidirectional</EM> bandwidth limits.



</div>

<div>


> [!NOTE]  
> The Lync Server 2013 Voice Policy features provide the ability to override bandwidth policy checks for incoming calls to the user (not for outgoing calls that are placed by the user). After the session is established, the bandwidth consumption will be accurately accounted for. This setting should be used sparingly. For details, see <A href="lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md">Create a voice policy and configure PSTN usage records in Lync Server 2013</A> or <A href="lync-server-2013-modify-a-voice-policy-and-configure-pstn-usage-records.md">Modify a voice policy and configure PSTN usage records in Lync Server 2013</A> in the Deployment documentation.



</div>

To optimize bandwidth utilization on a per-session basis, consider the type of audio and video codecs that will be used. In particular, avoid allocating insufficient bandwidth for a codec that you expect to be used frequently. Conversely, if you want to prevent media from using a codec that requires more bandwidth, you should set the maximum bandwidth per session low enough to discourage such use. For audio, not every codec is available for every scenario. For example:

  - Peer-to-peer audio calls between Lync endpoints will use either RTAudio (8kHz) or RTAudio (16kHz) when you factor in the bandwidth and prioritization of codecs.

  - Conference calls between Lync endpoints and the A/V Conferencing service will use either G.722 or Siren.

  - Calls to the public switched telephone network (PSTN) either to or from Lync endpoints will use either G.711 or RTAudio (8kHz).

Use the following table to help optimize the maximum per-session bandwidth settings.

### Bandwidth utilization by codecs

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Codec</th>
<th>Bandwidth requirement with no forward error correction (FEC)</th>
<th>Bandwidth requirement with forward error correction (FEC)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTAudio (8kHz)</p></td>
<td><p>49.8 kbps</p></td>
<td><p>61.6 kbps</p></td>
</tr>
<tr class="even">
<td><p>RTAudio (16kHz)</p></td>
<td><p>67 kbps</p></td>
<td><p>96 kbps</p></td>
</tr>
<tr class="odd">
<td><p>Siren</p></td>
<td><p>57.6 kbps</p></td>
<td><p>73.6 kbps</p></td>
</tr>
<tr class="even">
<td><p>G.711</p></td>
<td><p>102 kbps</p></td>
<td><p>166 kbps</p></td>
</tr>
<tr class="odd">
<td><p>G.722</p></td>
<td><p>105.6 kbps</p></td>
<td><p>169.6 kbps</p></td>
</tr>
<tr class="even">
<td><p>RTVideo (CIF 15 fps)</p></td>
<td><p>260 kbps</p></td>
<td><p>Not applicable</p></td>
</tr>
<tr class="odd">
<td><p>RTVideo (VGA 30 fps)</p></td>
<td><p>610 kbps</p></td>
<td><p>Not applicable</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> Bandwidth requirements take into account overhead for the following: Ethernet II, IP, User Datagram Protocol (UDP), RTP (real-time transport protocol), and SRTP (secure real-time transport protocol). They also include 10 kbps for RTCP overhead.



</div>

The G.722.1 and Siren codecs are similar, but they offer different bit rates.

G.722, the default codec for Lync Server conferencing, is completely different from the G.722.1 and Siren codecs.

The Siren codec is used in Lync Server in the following situations:

  - If the bandwidth policy is set too low for G.722 to be used.

  - If a Communications Server 2007 or Communications Server 2007 R2 client connects to a Lync Server conferencing service (because those clients do not support the G.722 codec).

### Bandwidth utilization by scenario

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Scenario</th>
<th>Bandwidth requirement optimized for quantity (kbps)</th>
<th>Bandwidth requirement for Balanced mode (kbps)</th>
<th>Bandwidth requirement optimized for quality (kbps)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Peer-to-peer audio calls</p></td>
<td><p>45 kbps</p></td>
<td><p>62 kbps</p></td>
<td><p>91 kbps</p></td>
</tr>
<tr class="even">
<td><p>Conference calls</p></td>
<td><p>53 kbps</p></td>
<td><p>101 kbps</p></td>
<td><p>165 kbps</p></td>
</tr>
<tr class="odd">
<td><p>PSTN calls (between Lync 2013 and PSTN gateway, with media bypass)</p></td>
<td><p>97 kbps</p></td>
<td><p>97 kbps</p></td>
<td><p>161 kbps</p></td>
</tr>
<tr class="even">
<td><p>PSTN calls (between Lync 2013 and Mediation Server, without media bypass)</p></td>
<td><p>45 kbps</p></td>
<td><p>97 kbps</p></td>
<td><p>161 kbps</p></td>
</tr>
<tr class="odd">
<td><p>PSTN calls (between Mediation Server and PSTN gateway, without media bypass)</p></td>
<td><p>97 kbps</p></td>
<td><p>97 kbps</p></td>
<td><p>161 kbps</p></td>
</tr>
<tr class="even">
<td><p>Lync - Polycom calls</p></td>
<td><p>101 Kbps</p></td>
<td><p>101 Kbps</p></td>
<td><p>101 Kbps</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Identify IP Subnets

For each network site, you will need to work with your network administrator to determine what IP subnets are assigned to each network site. If your network administrator has already organized the IP subnets into network regions and network sites, then your work is significantly simplified.

In our example, the New York site in the North America region is assigned the following IP subnets: 172.29.80.0/23, 157.57.216.0/25, 172.29.91.0/23, 172.29.81.0/24. Suppose Bob, who typically works in Detroit, travels to the New York office for training. When he turns on his computer and connects to the network, his computer will get an IP address in one of the four ranges reserved for New York, for example 172.29.80.103.

<div>


> [!WARNING]  
> The IP subnets specified during network configuration on the server must match the format provided by client computers in order to be properly used for media bypass. A Lync client takes its local IP address and masks the IP address with the associated subnet mask. When determining the bypass ID associated with each client, the Registrar will compare the list of IP subnets associated with each network site against the subnet provided by the client for an exact match. For this reason, it is important that subnets entered during network configuration on the server are actual subnets instead of virtual subnets. (If you deploy call admission control, but not media bypass, call admission control will function properly even if you configure virtual subnets.)<BR>For example, if a client signs in on a computer with an IP address of 172.29.81.57 with an IP subnet mask of 255.255.255.0, Lync 2013 will request the bypass ID associated with subnet 172.29.81.0. If the subnet is defined as 172.29.0.0/16, although the client belongs to the virtual subnet, the Registrar will not consider this a match because the Registrar is specifically looking for subnet 172.29.81.0. Therefore, it is important that the administrator enters subnets exactly as provided by Lync clients (which are provisioned with subnets during network configuration either statically or by DHCP.)



</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

