---
title: 'Lync Server 2013: AppliedBandwidthSource table'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: AppliedBandwidthSource table
ms:assetid: 24fb3caf-19b3-4c0a-90d7-ca5d53de32ad
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425725(v=OCS.15)
ms:contentKeyID: 48183638
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# AppliedBandwidthSource table in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-02_

The AppliedBandwidthSource table is a supporting table. Each record represents one source.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Column</strong></th>
<th><strong>Data Type</strong></th>
<th><strong>Key/Index</strong></th>
<th><strong>Details</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>AppliedBandwidthSourceKey</strong></p></td>
<td><p>int</p></td>
<td><p>Primary</p></td>
<td><p>Unique number identifying the source.</p></td>
</tr>
<tr class="even">
<td><p><strong>AppliedBandwidthSource</strong></p></td>
<td><p>varchar(256)</p></td>
<td><p>Unique</p></td>
<td><p>This is the source of the bandwidth cap being imposed. It describes where the bandwidth limit is coming from (for example, “Policy Server”, “TURN Server”, or “Modality”).</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

