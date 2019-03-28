---
title: 'DNS summary - Extensible messaging and presence protocol (XMPP) federation'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: DNS summary - Extensible messaging and presence protocol (XMPP) federation
ms:assetid: 0f720a2a-8ab5-43cc-882a-ab595ed3cec7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ618368(v=OCS.15)
ms:contentKeyID: 49105655
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# DNS summary - Extensible messaging and presence protocol (XMPP) federation in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-04-08_

To configure extensible messaging and presence protocol (XMPP) for your deployment, you create two Domain Name System (DNS) records in an external DNS server that will resolve the records to the Access Edge service of your Edge Server or Edge pool.

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

<div>

## See Also


[Setting up XMPP federation in Lync Server 2013](lync-server-2013-setting-up-xmpp-federation.md)  


[Determine DNS requirements for Lync Server 2013](lync-server-2013-determine-dns-requirements.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

