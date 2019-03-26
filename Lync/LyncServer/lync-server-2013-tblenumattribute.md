---
title: 'Lync Server 2013: tblEnumAttribute'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: tblEnumAttribute
ms:assetid: 17f8b87e-36a6-4f6a-8630-7c76b61a7595
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg558617(v=OCS.15)
ms:contentKeyID: 48183523
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# tblEnumAttribute in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-12_

tblEnumAttribute is a hardcoded table that contains the Visibility and Behavior attributes that are used in the Node table.

### Columns

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Column</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>attributeID</p></td>
<td><p>smallint, not null</p></td>
<td><p>ID of the attribute.</p></td>
</tr>
<tr class="even">
<td><p>attributeName</p></td>
<td><p>nvarchar (256), not null</p></td>
<td><p>Name of the attribute.</p></td>
</tr>
</tbody>
</table>


### Key

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Column</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>attributeID</p></td>
<td><p>Primary key.</p></td>
</tr>
</tbody>
</table>


### Table Values

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>attributeID</th>
<th>attributeName</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>Visibility.</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>Behavior.</p></td>
</tr>
</tbody>
</table>


<div>

## See Also


[tblNode in Lync Server 2013](lync-server-2013-tblnode.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

