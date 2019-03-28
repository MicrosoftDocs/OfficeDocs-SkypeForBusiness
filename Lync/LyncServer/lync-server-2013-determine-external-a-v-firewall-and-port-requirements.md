---
title: 'Lync Server 2013: Determine external A/V firewall and port requirements'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Determine external A/V firewall and port requirements
ms:assetid: 3b849dc7-175d-40d1-820d-80e6ade6d332
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425882(v=OCS.15)
ms:contentKeyID: 48183872
ms.date: 07/23/2014
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

## NAT Requirements for External User Access

NAT has typically been a routing function, but newer devices such as firewalls and even hardware load balancers can be configured for NAT. Rather than focusing on which device is performing NAT, this topic describes the required NAT behavior instead.

Lync Server 2013 communications software does not support NAT for traffic to or from the Edge internal interface, but for the Edge external interface, the following NAT behavior is required.

<div>


> [!IMPORTANT]  
> You must configure symmetric NAT for incoming and outgoing traffic. Symmetric NAT is the NAT technology described in this topic.



</div>

This documentation uses the acronyms ChangeDST and ChangeSRC in tables and drawings to define the following required behavior:

  - **ChangeDST**   The process of changing the destination IP address on packets destined for the network that is using NAT. This is also known as transparency, port forwarding, destination NAT mode, or half-NAT mode.

  - **ChangeSRC**   the process of changing the source IP address on packets leaving the network that is using NAT. This is also known as proxy, secure NAT, stateful NAT, source NAT or full-NAT mode.

Regardless of the naming convention used, the NAT behavior required for the external interface of the Edge Server is as follows:

  - For traffic from the Internet to the Edge external interface:
    
      - Change the destination IP address of the incoming packet from the Edge external interface public IP address to the translated IP address of the Edge external interface.
    
      - Leave the source IP address intact so that there is a return route for the traffic.

  - For traffic from the Edge external interface to the Internet:
    
      - Change the source IP address of the packet leaving the Edge external interface, from the translated IP address to the public IP address of the Edge external interface so that the internal Edge IP address is not exposed and because it is a non-routable IP address.
    
      - Leave the destination IP address intact on the outgoing packets.

The following figure shows the distinction between changing the destination IP address (ChangeDST) for inbound traffic and changing the source IP Address (ChangeSRC) for outbound traffic using the A/V edge as an example.

**Changing the destination IP address (ChangeDST) for inbound traffic and changing the source IP Address (ChangeSRC)**

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

