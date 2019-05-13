---
title: 'Lync Server 2013: Determine external A/V firewall and port requirements'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Determine external A/V firewall and port requirements
ms:assetid: 3b849dc7-175d-40d1-820d-80e6ade6d332
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425882(v=OCS.15)
ms:contentKeyID: 48183872
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Determine external A/V firewall and port requirements for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-29_

Audio/Video (A/V) communication can be a complex. Because of the nature of protocols used in A/V and how clients and servers use the protocols, a special section is warranted to explain the differences between client and server versions.

Use the following A/V Firewall and Port table to determine firewall requirements and which ports to open. Then, review the network address translation (NAT) terminology because NAT can be implemented in many different ways. For a detailed example of firewall port settings, see the reference architectures in [Scenarios for external user access in Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md).

### General Protocol Usage for UDP and TCP in Audio/Video and Media Traffic

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Audio/Video Transport</th>
<th>Usage</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>UDP</p></td>
<td><p>Preferred transport layer protocol for audio and video</p></td>
</tr>
<tr class="even">
<td><p>TCP</p></td>
<td><p>Fallback transport layer protocol for audio and video</p>
<p>Required transport layer protocol for application sharing to Office Communications Server 2007 R2, Lync Server 2010 and Lync Server 2013</p>
<p>Required transport layer protocol for file transfer to Lync Server 2010 and Lync Server 2013</p></td>
</tr>
</tbody>
</table>


<div>

## External A/V Firewall Port Requirements for External User Access

The firewall port requirements for external (and internal) SIP and conferencing interfaces are consistent, regardless of the version of your client or the version of the federation partner.

The same is not true for the Audio/Video Edge external interface. For federation with Office Communications Server 2007, the A/V Edge service requires that external firewall rules allow RTP/TCP and RTP/UDP traffic in the 50,000 through 59,999 port range to flow in both directions. The previous table assumes that Lync Server 2013 is the primary federation partner and it is being configured to communicate with one of the other federation partner types listed.

Configuring the Audio/Video port range of 50,000-59,999 must take into account that the port range will contain the source ports for communications to federation partners. In detail, consider that a communication is initiated from a federation partner. The communication from the A/V Edge service ports in the 50,000-59,999 range will connect to the expected port TCP 443 of the partner’s A/V Edge service. Conversely, inbound traffic to your A/V Edge service port TCP 443 will have a source port in the range of 50,000-59,999.

Different firewalls and policies for firewall administration may require only destination rules to be configured, or they may require both source and destination to be configured. If your requirements are for destination ports only, the Audio/Video requirements are:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Source IP</th>
<th>Destination IP</th>
<th>Destination Port</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>A/V Edge service interface</p></td>
<td><p>Any</p></td>
<td><p>TCP 443</p></td>
</tr>
<tr class="even">
<td><p>A/V Edge service interface</p></td>
<td><p>Any</p></td>
<td><p>UDP 3478</p></td>
</tr>
<tr class="odd">
<td><p>Any</p></td>
<td><p>A/V Edge service interface</p></td>
<td><p>TCP 443</p></td>
</tr>
<tr class="even">
<td><p>Any</p></td>
<td><p>A/V Edge service interface</p></td>
<td><p>UDP 3478</p></td>
</tr>
</tbody>
</table>


If your policies require both inbound and outbound firewall rule definitions, the Audio/Video requirements are:


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Source IP</th>
<th>Destination IP</th>
<th>Source Port</th>
<th>Destination Port</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>A/V Edge service interface</p></td>
<td><p>Any</p></td>
<td><p>TCP 50,000-59,999</p></td>
<td><p>TCP 443</p></td>
</tr>
<tr class="even">
<td><p>A/V Edge service interface</p></td>
<td><p>Any</p></td>
<td><p>UDP 3478</p></td>
<td><p>UDP 3478</p></td>
</tr>
<tr class="odd">
<td><p>Any</p></td>
<td><p>A/V Edge service interface</p></td>
<td><p>Any</p></td>
<td><p>TCP 443</p></td>
</tr>
<tr class="even">
<td><p>Any</p></td>
<td><p>A/V Edge service interface</p></td>
<td><p>Any</p></td>
<td><p>UDP 3478</p></td>
</tr>
</tbody>
</table>


<div>


> [!IMPORTANT]  
> Microsoft Office Communications Server 2007 requires a slightly different configuration. The TCP and UDP port range of 50,000-59,999 must be open inbound and outbound. This requirement is only for Office Communicator 2007. Office Communications Server 2007 R2, Lync Server 2010 and Lync Server 2013 only require TCP range 50,000-59,999 open outbound.



</div>

</div>

<div>

## NAT requirements for the Edge service

The following NAT requirements apply if you choose to configure non-routable private IP addresses for the Edge service:

  - NAT can only be used with DNS load-balancing. NAT is not supported with a hardware load balancing (HLB) Edge topology.

  - NAT can only be used on the external Edge interface. NAT is not supported on the internal Edge interface.

  - NAT must be symmetric for incoming and outgoing traffic.
    
  - For traffic from the Internet, NAT must change the destination IP address from the NAT-enabled public IP address of the A/V Edge service to its external IP address. The source IP address must remain intact, so that the A/V Edge service can find the optimal media path.
  
  For example, in the inbound direction in the figure below, the public IP address 131.107.155.30 was changed to the external (private) IP address 10.45.16.10. The source IP address remained unchanged.
  
  - For traffic from the A/V Edge service to the Internet, NAT must change the source IP address from the external IP address of the A/V Edge service to the NAT-enabled public IP address.

For example, in the outbound direction in the figure below, the external (private) IP address 10.45.16.10 was changed to the public IP address 131.107.155.30.

**The figure below shows how NAT changes the destination IP address for inbound traffic and the source IP Address for outbound traffic.**

![Changing destination/source IP addresses](images/Gg425882.0fee7ec5-4cb8-4aff-9164-e7fbab73336d(OCS.15).jpg "Changing destination/source IP addresses")

The key points are:

  - Traffic that is inbound to the server running the A/V Edge service, the source IP address does not change but the destination IP address changes from 131.107.155.30 to the translated IP address of 10.45.16.10.

  - Traffic that is outbound from the server running the A/V Edge service back to the workstation, the source IP address changes from the server’s public IP address to the public IP address of the server running the A/V Edge service. The destination IP remains the workstation’s public IP address. After the packet leaves the first NAT device outbound, the rule on the NAT device changes the source IP address of the server running the A/V Edge service external interface IP address (10.45.16.10) to its public IP address (131.107.155.30).

</div>

</div>

<span> </span>

</div>

</div>

</div>

