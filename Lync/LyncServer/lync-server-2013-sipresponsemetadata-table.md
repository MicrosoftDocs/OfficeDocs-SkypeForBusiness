---
title: 'Lync Server 2013: SIPResponseMetaData table'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: SIPResponseMetaData table
ms:assetid: cf723737-4a75-4352-829b-f4954aa59716
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205294(v=OCS.15)
ms:contentKeyID: 48185510
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# SIPResponseMetaData table in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-28_

The SIPResponseMetaDataTable contains a list of SIP response codes and the classification and definition of each of those codes. These codes are generated in response to events affecting SIP devices and SIP communication sessions; for example, the response code 403 is generated when a SIP device makes a request, but the server declines to honor that request.

This table was introduced in Microsoft Lync Server 2013.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Column</th>
<th>Data Type</th>
<th>Key/Index</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ResponseCode</strong></p></td>
<td><p>int</p></td>
<td><p>Primary</p></td>
<td><p>Numeric value that represents the SIP response code.</p></td>
</tr>
<tr class="even">
<td><p><strong>Class</strong></p></td>
<td><p>int</p></td>
<td></td>
<td><p>General classification for the response code. Classifications include:</p>
<ul>
<li><p>1 – Informational Responses</p></li>
<li><p>2 – Successful Responses</p></li>
<li><p>3 – Redirection Responses</p></li>
<li><p>4 – Client Failure Responses</p></li>
<li><p>5 -- Server Failure Responses</p></li>
<li><p>6 – Global Failure Response</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Description</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td></td>
<td><p>Description of the SIP response code. For example, response code 181 has the following description:</p>
<p>Call Is Being Forwarded</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

