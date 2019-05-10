---
title: 'DNS summary - Scaled consolidated edge with hardware load balancers'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: DNS summary - Scaled consolidated edge with hardware load balancers
ms:assetid: 8453297c-da1d-4b9e-a37e-6721458c6feb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398670(v=OCS.15)
ms:contentKeyID: 48184700
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# DNS summary - Scaled consolidated edge with hardware load balancers in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-01-27_

DNS record requirements for remote access to Lync Server 2013 are fairly straightforward compared to those for certificates and ports. Also, many records are optional, depending on how you configure clients running Lync 2013 and whether you enable federation.

For details about Lync 2013 DNS requirements, see [Determine DNS requirements for Lync Server 2013](lync-server-2013-determine-dns-requirements.md).

For details about configuring automatic configuration of Lync 2013 clients if split-brain DNS is not configured, see the "Automatic Configuration without Split Brain DNS" section in [Determine DNS requirements for Lync Server 2013](lync-server-2013-determine-dns-requirements.md).

The following table contains a summary of the DNS records that are required to support the Scaled Consolidated Edge Topology (Hardware Load Balanced) figure. Note that certain DNS records are required only for automatic configuration for Lync clients. If you plan to use group policy objects (GPOs) to configure Lync clients, the associated records are not necessary.

<div>

## IMPORTANT: Edge Server Network Adapter Requirements

To avoid routing issues, verify that there are at least two network adapters in your Edge Servers and that the default gateway is set only on the network adapter associated with the external interface. For example, as shown in the Scaled Consolidated Edge Scenario figure in [Scaled consolidated edge with hardware load balancers in Lync Server 2013](lync-server-2013-scaled-consolidated-edge-with-hardware-load-balancers.md), the default gateway would point to the external firewall.

You can configure two network adapters in each of your Edge Servers as follows:

  - **Network adapter 1 (Internal Interface)**
    
    Internal interface with 172.25.33.10 assigned.
    
    No default gateway.
    
    Ensure there is a route from the network containing the Edge Server internal interface to any networks that contain Lync Server clients or servers running Lync Server (for example, from 172.25.33.0 to 192.168.10.0).

  - **Network adapter 2 (External Interface)**
    
    Three public IP addresses are assigned to this network adapter, for example 131.107.155.10 for Access Edge service, 131.107.155.20 for Web Conferencing Edge service, 131.107.155.30 for A/V Edge service.
    
    <div>
    

    > [!NOTE]
    > The IP addresses that are assigned to the actual external network interfaces of the Edge Server may depend on which hardware load balancer you choose. Refer to the documentation for your hardware load balancer to understand the actual IP address requirements.<BR>It is possible, though not recommended, to use a single IP address for all three Edge service interfaces. Though this does save IP addresses, it requires different port numbers for each service. The default port number is 443/TCP, which ensures that most remote firewalls will allow the traffic. Changing the port values to (for example) 5061/TCP for the Access Edge service, 444/TCP for the Web Conferencing Edge service and 443/TCP for the A/V Edge service might cause problems for remote users where a firewall that they are behind does not allow the traffic over 5061/TCP and 444/TCP. Additionally, three distinct IP addresses makes troubleshooting easier due to being able to filter on IP address.

    
    </div>
    
    Access Edge service IP address is primary with default gateway set to Internet-facing router (131.107.155.1).
    
    Web Conferencing Edge service and A/V Edge service IP addresses secondary.

<div>


> [!TIP]
> Configuring the Edge Server with two network adapters is one of two options. The other option is to use one network adapter for the internal side and three network adapters for the external side of the Edge Server. The main benefit of this option is a distinct network adapter per Edge Server service, and potentially more concise data collection when troubleshooting is necessary



</div>

### DNS Records Required for Scaled Consolidated Edge, Hardware Load Balanced (Example)

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Location/TYPE/Port</th>
<th>FQDN/DNS Record</th>
<th>IP Address/FQDN</th>
<th>Maps to/Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>External DNS/A</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>131.107.155.10</p></td>
<td><p>Access Edge service external interface (Contoso). Repeat as necessary for all SIP domains with Lync enabled users</p></td>
</tr>
<tr class="even">
<td><p>External DNS/A</p></td>
<td><p>webcon.contoso.com</p></td>
<td><p>131.107.155.20</p></td>
<td><p>Web Conferencing Edge service external interface</p></td>
</tr>
<tr class="odd">
<td><p>External DNS/A</p></td>
<td><p>av.contoso.com</p></td>
<td><p>131.107.155.30</p></td>
<td><p>A/V Edge service external interface</p></td>
</tr>
<tr class="even">
<td><p>External DNS/SRV/443</p></td>
<td><p>_sip._tls.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>Access Edge service external interface. Required for automatic configuration of Lync 2013 and Lync 2010 clients to work externally. Repeat as necessary for all SIP domains with Lync enabled users.</p></td>
</tr>
<tr class="odd">
<td><p>External DNS/SRV/5061</p></td>
<td><p>_sipfederationtls._tcp.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>SIP Access Edge service external interface Required for automatic DNS discovery of federated partners known as “Allowed SIP Domain” (called enhanced federation in previous releases). Repeat as necessary for all SIP domains with Lync enabled users and Microsoft Lync Mobile clients that use either the Push Notification Service or the Apple Push Notification service</p></td>
</tr>
<tr class="even">
<td><p>Internal DNS/A</p></td>
<td><p>lsedge.contoso.net</p></td>
<td><p>172.25.33.10</p></td>
<td><p>Consolidated Edge internal interface</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

