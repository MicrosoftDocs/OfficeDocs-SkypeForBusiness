---
title: 'Lync Server 2013: tblPrincipalAffiliations'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: tblPrincipalAffiliations
ms:assetid: 45fd8484-5837-44d2-85bb-45c83546607c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg558642(v=OCS.15)
ms:contentKeyID: 48183993
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# tblPrincipalAffiliations in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-12_

tblPrincipalAffiliations contains the principal affiliations that describe memberships in locations, including Active Directory Domain Services security groups, in Active Directory containers, in domains.

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
<td><p>principalID</p></td>
<td><p>int, not null</p></td>
<td><p>ID of the affiliated principal.</p></td>
</tr>
<tr class="even">
<td><p>affiliationID</p></td>
<td><p>int, not null</p></td>
<td><p>ID of the principal representing the affiliation. Each principal (except system-user-types) has a self-affiliation as well.</p></td>
</tr>
<tr class="odd">
<td><p>index</p></td>
<td><p>int, not null</p></td>
<td><p>Index. The value for self-affiliations is -1, and for the other affiliations it increases sequentially from 1 within each &lt;principalID, affiliationId&gt; bucket.</p></td>
</tr>
<tr class="even">
<td><p>updatedBy</p></td>
<td><p>int, not null</p></td>
<td><p>Principal that did the latest update. This is usually 1, which means Active Directory Sync.</p></td>
</tr>
</tbody>
</table>


### Keys

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Columns</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>&lt;principalID, index, affiliationID&gt;</p></td>
<td><p>Primary key.</p></td>
</tr>
<tr class="even">
<td><p>principalID</p></td>
<td><p>Foreign key with lookup in tblPrincipal.prinID table.</p></td>
</tr>
<tr class="odd">
<td><p>affiliationID</p></td>
<td><p>Foreign key with lookup in tblPrincipal.prinID table.</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

