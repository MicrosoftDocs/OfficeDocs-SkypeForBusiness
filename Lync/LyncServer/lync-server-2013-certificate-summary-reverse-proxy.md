---
title: 'Lync Server 2013: Certificate summary - Reverse proxy'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Certificate summary - Reverse proxy
ms:assetid: f2b9a53f-aead-413d-81e9-4a294a010fbb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205381(v=OCS.15)
ms:contentKeyID: 48185820
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Certificate summary - Reverse proxy in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-14_

Certificate requirements for the reverse proxy are much simpler than that for the Edge Servers. The provided flowchart presents the requirements necessary. The accompanying table presents typical certificate subject name and subject alternative names in relation to the scenarios that we have been reviewed in the Edge Server discussions. For more details on the Edge Server scenarios, see [Scenarios for external user access in Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md).

**Certificates Flow Chart for Reverse Proxy**

![Certificates Flow Chart for Edge Server](images/JJ205381.026045d7-1b4b-4651-b32f-2d43a7161198(OCS.15).jpg "Certificates Flow Chart for Edge Server")

### Reverse Proxy: External Interface

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Component</th>
<th>Subject name</th>
<th>Subject alternative name (SAN)/Order</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Reverse Proxy</p></td>
<td><p>webext.contoso.com</p></td>
<td><p>webext.contoso.com</p>
<p>webdirext.contoso.com</p>
<p>dialin.contoso.com</p>
<p>meet.contoso.com</p>
<p>officewebapps01.contoso.com</p>
<p>lyncdiscover.contoso.com</p>
<p>(Optional):*.contoso.com</p></td>
<td><p>Certificate must be issued by a public CA and with the server EKU. Services include Address Book Service, distribution group expansion Office Web Apps for conferencing, and Lync IP Device publishing rules. Subject alternative name includes:</p>
<ul>
<li><p>External Web Services FQDN for Front End Server or Front End pool</p></li>
<li><p>External Web Services FQDN for Director or Director pool</p></li>
<li><p>Dial-in conferencing</p></li>
<li><p>Online meeting publishing rule</p></li>
<li><p>Office Web Apps for conferencing</p></li>
<li><p>Lyncdiscover (Autodiscover)</p></li>
</ul>
<p>The optional wildcard replaces both meet and dialin SAN</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

