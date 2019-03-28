---
title: 'DNS summary - Single consolidated edge with public IP addresses'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: DNS summary - Single consolidated edge with public IP addresses
ms:assetid: 7b83eae4-aa1a-4cc6-8077-42176d56cab5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205025(v=OCS.15)
ms:contentKeyID: 48184601
ms.date: 03/09/2017
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# DNS summary - Single consolidated edge with public IP addresses in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2017-03-09_

DNS record requirements for remote access to Lync Server 2013 are fairly straightforward compared to those for certificates and ports. Also, many records are optional, depending on how you configure clients running Lync 2013 and whether you enable federation.

For details about Lync 2013 DNS requirements, see [Determine DNS requirements for Lync Server 2013](lync-server-2013-determine-dns-requirements.md).

For details about automatic configuration of clients running Lync 2013 if split-brain DNS is not configured, see “Automatic Configuration without Split-Brain DNS” in [Determine DNS requirements for Lync Server 2013](lync-server-2013-determine-dns-requirements.md).

The following table contains a summary of the DNS records that are required to support the single consolidated edge topology shown in the Single Consolidated Edge Topology figure. Note that certain DNS records are required only for automatic configuration of Lync 2013 and Lync 2010 clients. If you plan to use group policy objects (GPOs) to configure Lync clients, the associated automatic configuration records are not necessary.

<div>

## IMPORTANT: Edge Server Network Adapter Requirements

To avoid routing issues, verify that there are at least two network adapters in your Edge Servers and that the default gateway is set only on the network adapter associated with the external interface. For example, as shown in the Single Consolidated Edge Topology with Public IP Addresses figure in [Single consolidated edge with public IP addresses in Lync Server 2013](lync-server-2013-single-consolidated-edge-with-public-ip-addresses.md), the default gateway would point to the external router at your Internet perimeter or firewall that can provide a public IP addresses. The network relationship for Edge Server interfaces is a route relationship instead of a NAT relationship.

You can configure two network adapters in your Edge Server as follows:

  - **Network adapter 1 (Internal Interface)**
    
    Internal interface with 172.25.33.10 assigned.
    
    No default gateway is defined.
    
    Ensure that there is a route from the network containing the Edge internal interface to any networks that contain servers running Lync Server 2013 or Lync Server 2013 clients (for example, from 172.25.33.0 to 192.168.10.0).

  - **Network adapter 2 (External Interface)**
    
    Three public IP addresses are assigned to this network adapter, for example 131.107.155.10 for Access Edge, 131.107.155.20 for Web Conferencing Edge, 131.107.155.30 for AV Edge.
    
    <div>
    

    > [!NOTE]
    > It is possible, though not recommended, to use a single IP address for all three Edge service interfaces. Though this does save IP addresses, it requires different port numbers for each service. The default port number is 443/TCP, which ensures that most remote firewalls will allow the traffic. Changing the port values to (for example) 5061/TCP for the Access Edge, 444/TCP for the Web Conferencing Edge and 443/TCP for the AV Edge might cause problems for remote users where a firewall that they are behind does not allow the traffic over 5061/TCP and 444/TCP. Additionally, three distinct IP addresses makes troubleshooting easier due to being able to filter on IP address.

    
    </div>
    
    The Access Edge public IP address is primary with default gateway set to the public router (131.107.155.1).
    
    Web conferencing and A/V Edge public IP addresses are additional IP addresses in the **Advanced** section of the properties of **Internet Protocol Version 4 (TCP/IPv4)** and **Internet Protocol Version 6 (TCP/IPv6)** of the **Local Area Connection Properties** in Windows Server.

<div>


> [!TIP]
> Configuring the Edge Server with two network adapters is one of two options. The other option is to use one network adapter for the internal side and three network adapters for the external side of the Edge Server. The main benefit of this option is a distinct network adapter per Edge Server service, and potentially more concise data collection when troubleshooting is necessary



</div>

### DNS Records Required for Single Consolidated Edge with Public IP Addresses (Example)

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
<td><p>Access Edge external interface (Contoso) Repeat as necessary for all SIP domains with Lync enabled users</p></td>
</tr>
<tr class="even">
<td><p>External DNS/A</p></td>
<td><p>webcon.contoso.com</p></td>
<td><p>131.107.155.20</p></td>
<td><p>Web Conferencing Edge external interface</p></td>
</tr>
<tr class="odd">
<td><p>External DNS/A</p></td>
<td><p>av.contoso.com</p></td>
<td><p>131.107.155.30</p></td>
<td><p>A/V Edge external interface</p></td>
</tr>
<tr class="even">
<td><p>External DNS/SRV/443</p></td>
<td><p>_sip._tls.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>Access Edge external interface. Required for automatic configuration of Lync 2013 and Lync 2010 clients to work externally. Repeat as necessary for all SIP domains with Lync enabled users.</p></td>
</tr>
<tr class="odd">
<td><p>External DNS/SRV/5061</p></td>
<td><p>_sipfederationtls._tcp.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>SIP Access Edge external interface Required for automatic DNS discovery of federated partners known as “Allowed SIP Domain” (called enhanced federation in previous releases).Repeat as necessary for all SIP domains with Lync enabled users</p></td>
</tr>
<tr class="even">
<td><p>Internal DNS/A</p></td>
<td><p>lsedge.contoso.net</p></td>
<td><p>172.25.33.10</p></td>
<td><p>Consolidated Edge internal interface</p></td>
</tr>
</tbody>
</table>


<div>


> [!IMPORTANT]
> The records listed in the previous table are shown with either a <EM>.net</EM> extension or a <EM>.com</EM> extension to highlight which zone they need to reside in if you are not using split-brain DNS. If you are using split-brain DNS, all records would be in the same zone, with the only distinction being whether they are in the internal or external version. For details, see “Split-Brain DNS” in <A href="lync-server-2013-determine-dns-requirements.md">Determine DNS requirements for Lync Server 2013</A>.



</div>

</div>

<div>

## Records Required for Federation


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
<th>FQDN</th>
<th>IP address/FQDN host record</th>
<th>Maps to/Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>External DNS/SRV/5061</p></td>
<td><p>_sipfederationtls._tcp.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>SIP Access Edge external interface Required for automatic DNS discovery of your federation to other potential federation partners, and is known as “Allowed SIP Domains” (called enhanced federation in previous releases).Repeat as necessary for all SIP domains with Lync enabled users</p>



> [!IMPORTANT]
> This SRV record is required for mobility and the push notification clearing house

</td>
</tr>
</tbody>
</table>


</div>

<div>

## DNS Summary for Extensible Messaging and Presence Protocol


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
<th>FQDN</th>
<th>IP address/FQDN host record</th>
<th>Maps to/Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>External DNS/SRV/5269</p></td>
<td><p>_xmpp-server._tcp.contoso.com</p></td>
<td><p>xmpp.contoso.com</p></td>
<td><p>XMPP proxy external interface on the Access Edge service or Edge pool.Repeat as necessary for all internal SIP domains with Lync enabled users where contact with XMPP contacts is allowed through the configuration of the External Access Policy through a global policy, site policy where the user is located, or user policy applied to the Lync-enabled user. An allowed XMPP domain must also be configured in the XMPP Federated Partners policy. See topics in <strong>See Also</strong> for additional details</p></td>
</tr>
<tr class="even">
<td><p>External DNS/A</p></td>
<td><p>xmpp.contoso.com (for example)</p></td>
<td><p>IP address of Access Edge service on your Edge Server or Edge pool hosting XMPP proxy</p></td>
<td><p>Points to the Access Edge service or Edge pool that hosts the XMPP proxy service. Typically, the SRV record that you create will point to this host (A or AAAA) record</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

