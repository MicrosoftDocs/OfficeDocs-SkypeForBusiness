---
title: 'Port summary -  Extensible messaging and presence protocol (XMPP) federation'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Port summary -  Extensible messaging and presence protocol (XMPP) federation
ms:assetid: 62e98fab-7add-4983-a3fa-dbe74e1c3849
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ618371(v=OCS.15)
ms:contentKeyID: 49105658
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Port summary - Extensible messaging and presence protocol (XMPP) federation in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-20_

The ports and protocols defined for the extensible messaging and presence protocol (XMPP) proxy deployed on the Edge Server allow communications from the XMPP federated partner to the Edge Server, and also allows communication from your Edge Server to the XMPP federated partner. A rule is also defined on the internal-facing firewall from the Front End Server or Front End pool to the Edge Server or Edge pool.

<div>

## Firewall Summary for Extensible Messaging and Presence Protocol


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Protocol/TCP or UDP/Port</th>
<th>Source (IP address)</th>
<th>Destination (IP address)</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>XMPP/TCP/5269</p></td>
<td><p>Any</p></td>
<td><p>Access Edge service interface IP address</p></td>
<td><p>Standard server-to-server communication port for XMPP. Allows communication to the Edge Server XMPP proxy from federated XMPP partners</p></td>
</tr>
<tr class="even">
<td><p>XMPP/TCP/5269</p></td>
<td><p>Access Edge service interface IP address</p></td>
<td><p>Any</p></td>
<td><p>Standard server-to-server communication port for XMPP. Allows communication from the Edge Server XMPP proxy to federated XMPP partners</p></td>
</tr>
<tr class="odd">
<td><p>XMPP/MTLS/23456</p></td>
<td><p>Any</p></td>
<td><p>Internal Edge Server Interface IP</p></td>
<td><p>Internal XMPP traffic from the XMPP Gateway on the Front End Server or Front End pool to the Edge Server</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## See Also


[Example XMPP configuration in Lync Server 2013 – XMPP federation with Google Talk](lync-server-2013-example-xmpp-configuration-–-xmpp-federation-with-google-talk.md)  


[Manage XMPP federated partners in Lync Server 2013](lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

