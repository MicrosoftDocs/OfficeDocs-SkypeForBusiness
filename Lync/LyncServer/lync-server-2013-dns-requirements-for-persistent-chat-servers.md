---
title: 'Lync Server 2013: DNS requirements for Persistent Chat Servers'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: DNS requirements for Persistent Chat Servers
ms:assetid: f7531374-d7ed-4b63-ae81-02294cb4496a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205391(v=OCS.15)
ms:contentKeyID: 48185857
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# DNS requirements for Persistent Chat Servers in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-28_

This section describes the Domain Name System (DNS) records that are required for deployment of Persistent Chat Servers.

<div>

## DNS Records for Persistent Chat Servers

The following table specifies DNS requirements for Persistent Chat Server deployment.

### DNS Requirements for a Persistent Chat Server

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
<td><p>One Persistent Chat Server</p></td>
<td><p>An internal A record that resolves the fully qualified domain name (FQDN) of the server to its IP address.</p></td>
</tr>
<tr class="even">
<td><p>Persistent Chat pool</p></td>
<td><p>An internal A record that resolves the fully qualified domain name (FQDN) of the servers to its IP address.</p>
<p><strong>Example</strong></p>
<p>PersistentChatServer01.contoso.com     10.10.10.1</p>
<p>PersistentChatServer02.contoso.com     10.10.10.2</p>
<p>An internal A record that resolves the fully qualified domain name (FQDN) of the servers to its IP address.</p>
<p><strong>Example</strong></p>
<p>PersistentChatPool.contoso.com    10.10.10.1</p>
<p>PersistentChatPool.contoso.com    10.10.10.2</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

