---
title: 'Lync Server 2013: DNS requirements for Standard Edition servers'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: DNS requirements for Standard Edition servers
ms:assetid: 3d6bbe65-e7ce-491b-a0bd-d2f7197f240d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425900(v=OCS.15)
ms:contentKeyID: 48183920
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# DNS requirements for Standard Edition servers in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-19_

This section describes the Domain Name System (DNS) records that are required for deployment of Standard Edition servers.

<div>

## DNS Records for Standard Edition Servers

The following table specifies DNS requirements for Lync Server 2013 Standard Edition server deployment.

### DNS Requirements for a Standard Edition Server

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
<td><p>Standard Edition server</p></td>
<td><p>An internal A record that resolves the fully qualified domain name (FQDN) of the server to its IP address.</p></td>
</tr>
<tr class="even">
<td><p>Automatic client sign-in</p></td>
<td><p>For each supported SIP domain, an SRV record for _sipinternaltls._tcp.&lt;domain&gt; over port 5061 that maps to the FQDN of the Standard Edition server that authenticates and redirects client requests for sign-in. For details, see <a href="lync-server-2013-dns-requirements-for-automatic-client-sign-in.md">DNS requirements for automatic client sign-in in Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Device Update Web service discovery by unified communications (UC) devices</p></td>
<td><p>An internal A record with the name ucupdates-r2.&lt;SIP domain&gt; that resolves to the IP address of the Standard Edition server hosting Device Update Web service. In the situation where a UC device is turned on, but a user has never logged into the device, the A record allows the device to discover the server hosting Device Update Web service and obtain updates. Otherwise, devices obtain the server information though in-band provisioning the first time a user logs in.</p></td>
</tr>
<tr class="even">
<td><p>A reverse proxy to support HTTP traffic</p></td>
<td><p>An external A record that resolves the external web farm FQDN to the external IP address of the reverse proxy. Clients and UC devices use this record to connect to the reverse proxy. For details, see <a href="lync-server-2013-determine-dns-requirements.md">Determine DNS requirements for Lync Server 2013</a> in the Planning documentation.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

