---
title: 'Lync Server 2013: DNS requirements for Front End pool'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: DNS requirements for Front End pool
ms:assetid: 02d2aa6b-9e01-437b-a2df-00590280150d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398082(v=OCS.15)
ms:contentKeyID: 48183249
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# DNS requirements for Front End pool in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-07_

To successfully complete this procedure, you should be logged on to the server or domain minimally as a member of the Domain Admins group or a member of the DnsAdmins group.

You need to configure the required Domain Name System (DNS) records prior to publishing your topology in Topology Builder. Additionally, some of the fully qualified domain names (FQDNs) used in the configuration of a Lync Server 2013 deployment are logical and not physical server FQDNs, so additional DNS configuration is required prior to publishing.

<div>


> [!WARNING]  
> Lync Server 2013 does not support single-labeled domains. For example, a forest with a root domain named <STRONG>contoso.local</STRONG> is supported, but a root domain named <STRONG>local</STRONG> is not supported. For details, see Microsoft Knowledge Base article 300684, “Information about configuring Windows for domains with single-label DNS names,” at <A class=uri href="http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=300684">http://go.microsoft.com/fwlink/p/?linkid=3052&amp;kbid=300684</A>.



</div>

<div>


> [!IMPORTANT]  
> The name you specify must be identical to the computer name configured on the server. By default the computer name of a computer that is not joined to a domain is a short name, not an FQDN. Topology Builder uses FQDNs, not short names. <STRONG>Use only standard characters</STRONG> (including A–Z, a–z, 0–9, and hyphens) when assigning FQDNs of your servers running Lync Server, Edge Servers, and pools. Do not use Unicode characters or underscores. Nonstandard characters in an FQDN are often not supported by external DNS and public certification authorities (CAs) (when the FQDN must be assigned to the SN in the certificate).



</div>

Prior to operating the topology after it has been deployed, ensure that the following Active Directory and DNS records are created (as your needs for specific features dictate):

  - Each server role that will exist in the topology is published as an Active Directory object (joining the computer to the domain will accomplish this).

  - A DNS A Record exists for each server.

  - A DNS SRV Record exists for each SIP domain if you plan to use automatic logon for clients in the form of \_sipinternaltls\_tcp.\<SIP domain\>. If you will use manual configuration for clients, this record is not necessary.

  - A DNS A Record for each configured simple URL, of which there are typically four: meet, dialin, lwa, and scheduler. Additionally, there is the admin simple URL which is a special URL for access to the Lync Server 2013 Control Panel.

  - The server running SQL Server must be joined to the domain, and reachable by the computer that Topology Builder is publishing from.

The table follows the reference architectures presented in the Planning section. For details, see [Scenarios for external user access in Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md) in the Planning documentation.

<div id="sectionSection0" class="section">

### DNS Records Required for the Front End pool

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Location</th>
<th>Type</th>
<th>FQDN</th>
<th>Maps to/Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Internal DNS</p></td>
<td><p>A</p></td>
<td><p>pool01.contoso.net</p></td>
<td><p>Pool01 (DNS load balancing). Requires a DNS A record for the IP address of each Front End Server within the pool, mapping to the pool FQDN.</p></td>
</tr>
<tr class="even">
<td><p>Internal DNS</p></td>
<td><p>A</p></td>
<td><p>pool01.contoso.net</p></td>
<td><p>Pool01 (virtual IP (VIP) of hardware load balancer).</p></td>
</tr>
<tr class="odd">
<td><p>Internal DNS</p></td>
<td><p>A</p></td>
<td><p>fe01.contoso.net</p>
<p>fe02.contoso.net</p>
<p>fe03.contoso.net</p>
<p>…</p></td>
<td><p>Pool01 Front End Server (NODE 1).</p>
<p>Pool01 Front End Server (NODE 2).</p>
<p>Pool01 Front End Server (NODE 3).</p>
<p>…</p></td>
</tr>
<tr class="even">
<td><p>Internal DNS</p></td>
<td><p>A</p></td>
<td><p>fe02.contoso.net</p></td>
<td><p>Pool01 Front End Server (NODE 2).</p></td>
</tr>
<tr class="odd">
<td><p>Internal DNS</p></td>
<td><p>A</p></td>
<td><p>lsweb.contoso.net</p></td>
<td><p>Pool01 (VIP) for client-to-server web traffic.</p></td>
</tr>
<tr class="even">
<td><p>Internal DNS</p></td>
<td><p>A</p></td>
<td><p>sqlbe.contoso.net</p></td>
<td><p>Pool01 Back End Server running SQL Server 2008 R2.</p></td>
</tr>
<tr class="odd">
<td><p>Internal DNS</p></td>
<td><p>A</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>Required for Lync Phone Edition, or automatic logon of clients without DNS SRV records, and for strict domain matching. Not required in all cases.</p></td>
</tr>
<tr class="even">
<td><p>Internal DNS</p></td>
<td><p>A</p></td>
<td><p>sip.fabrikam.com</p></td>
<td><p>Assumes a second SIP domain. Required for Lync Phone Edition, automatic logon of clients without DNS SRV records, and for strict domain matching. Not required in all cases.</p></td>
</tr>
<tr class="odd">
<td><p>Internal DNS</p></td>
<td><p>A</p></td>
<td><p>dialin.contoso.com</p></td>
<td><p>Simple URL for dial-in conferencing published internally – Front End Server (or Director, if installed) responds to simple URL queries.</p></td>
</tr>
<tr class="even">
<td><p>Internal DNS</p></td>
<td><p>A</p></td>
<td><p>meet.contoso.com</p></td>
<td><p>Simple URL for conferences published internally – Front End Server (or Director, if installed) responds to simple URL queries.</p></td>
</tr>
<tr class="odd">
<td><p>Internal DNS</p></td>
<td><p>A</p></td>
<td><p>admin.contoso.com</p>
<p>admin</p></td>
<td><p>Optional record, simple URL for Lync Server 2013 Control Panel published internally - Front End Server (or Director, if installed) responds to simple URL queries. Host name only (no domain name) is recommended.</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> VIP = Virtual IP address for hardware load balancer



</div>

</div>

<div>

## DNS SRV Records for the Front End pool


<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Location</th>
<th>Type</th>
<th>FQDN</th>
<th>Target FQDN</th>
<th>Port</th>
<th>Maps to/Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Internal DNS</p></td>
<td><p>SRV</p></td>
<td><p>_sipinternaltls._tcp.contoso.com</p></td>
<td><p>pool01.contoso.com</p></td>
<td><p>5061</p></td>
<td><p>Required for automatic configuration of Lync 2013 clients to work internally.</p></td>
</tr>
<tr class="even">
<td><p>Internal DNS</p></td>
<td><p>SRV</p></td>
<td><p>_sipinternaltls._tcp.fabrikam.com</p></td>
<td><p>pool01.fabrikam.com</p></td>
<td><p>5061</p></td>
<td><p>Required for automatic configuration of Lync 2013 clients to work internally.</p></td>
</tr>
<tr class="odd">
<td><p>Internal DNS</p></td>
<td><p>SRV</p></td>
<td><p>_ntp._udp.contoso.com</p></td>
<td><p>dc01.contoso.com</p></td>
<td><p>123</p></td>
<td><p>Network Time Protocol (NTP) source required for devices running Lync Phone Edition. Internally, this should point to the domain controller. If the domain controller is not defined, it will try to use the NTP server time.windows.com.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

