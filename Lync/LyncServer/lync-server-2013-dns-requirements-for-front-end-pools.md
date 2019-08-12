---
title: 'Lync Server 2013: DNS requirements for Front End pools'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: DNS requirements for Front End pools
ms:assetid: ba28919c-fbbe-4c54-8bf9-2b0cd3fa39c7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412910(v=OCS.15)
ms:contentKeyID: 48185228
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# DNS requirements for Front End pools in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-07_

This section describes the Domain Name System (DNS) records that are required for deployment of Front End pools.

<div>

## DNS Records for Front End Pools

The following table specifies DNS requirements for a Lync Server 2013 Front End pool deployment.

### DNS Requirements for a Front End Pool

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Deployment scenario</th>
<th>DNS requirement</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Front End pool with multiple Front End Servers and a hardware load balancer (whether or not DNS load balancing is also deployed on that pool)</p></td>
<td><p>When using both DNS load balancing and a hardware load balancer, you need to Host (A) records. Create an internal A record that resolves the fully qualified domain name (FQDN) of the Front End pool for DNS load balancing. Create an internal host (A) record for the internal Web services to the virtual IP (VIP) address of the load balancer. You must use the internal Web services name as defined in Topology Builder.</p>
<p>For example, if you use both DNS load balancing and hardware load balancing, you would have an A record for each Front End Server in a pool for DNS load balancing, and an A record for the internal Web services pointing to the virtual IP of the hardware load balancer:</p>
<ul>
<li><p>DNS load balancing:   Pool01.contoso.net   IP Address of pool   10.10.10.5</p>
<div>

> [!WARNING]  
> Each Front End Server will also have a distinct A record:


</div>
<ol>
<li><p>FE01.contoso.net    10.10.10.1</p></li>
<li><p>FE02.contoso.net    10.10.10.2</p></li>
<li><p>FE03.contoso.net    10.10.10.3</p></li>
<li><p>FE04.contoso.net    10.10.10.4</p></li>
</ol></li>
<li><p>Hardware load balancing:   WebInternal.contoso.net   IP Address of HLB VIP   192.168.10.5</p></li>
</ul>
<p>All traffic except for HTTP/HTTPS traffic will use the Pool01.contoso.net record. HTTP/HTTPS traffic will use the defined internal Web services address of 192.168.10.5</p></td>
</tr>
<tr class="even">
<td><p>Front End pool with DNS load balancing deployed</p></td>
<td><p>A set of internal A records that resolve the FQDN of the pool to the IP address of each server in the pool. There must one A record for each server in the pool.</p></td>
</tr>
<tr class="odd">
<td><p>Front End pool with DNS load balancing deployed</p></td>
<td><p>A set of internal A records that resolve the FQDN of each server in the pool to the IP address of that server. For details, see <a href="lync-server-2013-dns-load-balancing.md">DNS load balancing in Lync Server 2013</a> in the Planning documentation.</p></td>
</tr>
<tr class="even">
<td><p>Front End pool with a single Front End Server and a dedicated back-end database but no load balancer</p></td>
<td><p>An internal A record that resolves the FQDN of the Front End pool to the IP address of the single Enterprise Edition Front End Server.</p></td>
</tr>
<tr class="odd">
<td><p>Automatic client sign-in</p></td>
<td><p>For each supported SIP domain, an SRV record for _sipinternaltls._tcp.&lt;domain&gt; over port 5061 that maps to the FQDN of the Front End pool that authenticates and redirects client requests for sign-in. For details, see <a href="lync-server-2013-dns-requirements-for-automatic-client-sign-in.md">DNS requirements for automatic client sign-in in Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p>Device Update Web service discovery by unified communications (UC) devices</p></td>
<td><p>An internal A record with the name ucupdates-r2.&lt;SIP domain&gt; that resolves to the IP address of the Front End pool that hosts the Device Update Web service. In the situation where a UC device is turned on, but a user has never logged into the device, the A record allows the device to discover the Front End pool hosting Device Update Web service and obtain updates. Otherwise, devices obtain this information though in-band provisioning the first time a user logs in.</p>
<div>

> [!IMPORTANT]  
> If you have an existing deployment of Device Update Web service in Lync Server 2010, you have already created an internal A record with the name ucupdates.&lt;SIP domain&gt;. For Microsoft Office Communications Server 2007 R2, you must create an additional DNS A record with the name ucupdates-r2.&lt;SIP domain&gt;.


</div></td>
</tr>
<tr class="odd">
<td><p>A reverse proxy to support HTTP traffic</p></td>
<td><p>An external A record that resolves the external web farm FQDN to the external IP address of the reverse proxy. Clients and UC devices use this record to connect to the reverse proxy. For details, see <a href="lync-server-2013-determine-dns-requirements.md">Determine DNS requirements for Lync Server 2013</a> in the Planning documentation.</p></td>
</tr>
</tbody>
</table>


The following table shows an example of the DNS records required for the internal web farm FQDN.

### Example DNS Records for Internal Web Farm FQDN

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Internal web farm FQDN</th>
<th>Pool FQDN</th>
<th>DNS A record(s)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>webcon.contoso.com</p></td>
<td><p>ee-pool.contoso.com</p></td>
<td><p>DNS A record for the ee-pool.contoso.com that resolves to the VIP address of the load balancer used by the Front End Servers.</p>
<p>DNS A record for webcon.contoso.com that resolves to the VIP address of the load balancer used by the Front End Servers.</p></td>
</tr>
<tr class="even">
<td><p>ee-pool.contoso.com</p></td>
<td><p>ee-pool.contoso.com</p></td>
<td><p>DNS A record for ee-pool.contoso.com that resolves to the virtual IP (VIP) address of the load balancer used by the Enterprise Edition Front End Servers in the Front End pool.</p>
<p>Note that if you are using DNS load balancing on this pool, your Front End pool and internal web farm cannot have the same FQDN.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

