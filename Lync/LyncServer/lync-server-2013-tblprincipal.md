---
title: 'Lync Server 2013: tblPrincipal'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: tblPrincipal
ms:assetid: 79a24502-b4ce-41f0-8979-8caddf535338
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg558667(v=OCS.15)
ms:contentKeyID: 48184571
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# tblPrincipal in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-12_

tblPrincipal contains all principals, including users, folders, and groups.

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
<td><p>prinID</p></td>
<td><p>int, not null</p></td>
<td><p>Principal ID.</p></td>
</tr>
<tr class="even">
<td><p>prinGuid</p></td>
<td><p>GUID, not null</p></td>
<td><p>Principal GUID. This is broadly used as an alternate primary key because its meaning crosses over into the Active Directory Domain Services space. (The GUID for a cached principal is equal to the corresponding Active Directory object GUID.)</p></td>
</tr>
<tr class="odd">
<td><p>prinUri</p></td>
<td><p>nvarchar (256), not null</p></td>
<td><p>Principal URI. The SIP scheme is used for users, and ma-grp is used for almost everything else.</p></td>
</tr>
<tr class="even">
<td><p>prinName</p></td>
<td><p>nvarchar (256)</p></td>
<td><p>Common name. Used only by user types.</p></td>
</tr>
<tr class="odd">
<td><p>prinDisplayName</p></td>
<td><p>Nvarchar (256)</p></td>
<td><p>Display name. Used only by user types.</p></td>
</tr>
<tr class="even">
<td><p>prinCompanyName</p></td>
<td><p>nvarchar (256)</p></td>
<td><p>Company name. Used only by user types.</p></td>
</tr>
<tr class="odd">
<td><p>prinEmail</p></td>
<td><p>nvarchar (256)</p></td>
<td><p>Email. Used only by user types.</p></td>
</tr>
<tr class="even">
<td><p>prinADPath</p></td>
<td><p>nvarchar (384)</p></td>
<td><p>Domain name of the Active Directory object that the principal is a cached version of. Can be Null for types that are not Active Directory objects (such as system users).</p></td>
</tr>
<tr class="odd">
<td><p>prinADUserPrincipalName</p></td>
<td><p>nvarchar (256)</p></td>
<td><p>User’s user principal name (UPN). Used only by regular user types.</p></td>
</tr>
<tr class="even">
<td><p>prinDisabled</p></td>
<td><p>smallint, not null</p></td>
<td><ul>
<li><p>0: Principal is active.</p></li>
<li><p>1: Principal is disabled because user’s SIP capabilities are disabled.</p></li>
<li><p>2: Principal is deleted because associated AD object has been deleted.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>prinTypeID</p></td>
<td><p>smallint, not null</p></td>
<td><p>Principal type (from tblPrincipalType table).</p></td>
</tr>
<tr class="even">
<td><p>prinPoolID</p></td>
<td><p>Int</p></td>
<td><p>Lync pool assignment for the principal.</p></td>
</tr>
<tr class="odd">
<td><p>prinPolicyID</p></td>
<td><p>Int</p></td>
<td><p>Persistent Chat Server policy value for user, if tag type policy is present.</p></td>
</tr>
<tr class="even">
<td><p>prinAddedBy</p></td>
<td><p>int</p></td>
<td><p>Principal ID of the creator.</p></td>
</tr>
<tr class="odd">
<td><p>prinAddedOn</p></td>
<td><p>bigint, not null</p></td>
<td><p>Time stamp for the creation time.</p></td>
</tr>
<tr class="even">
<td><p>prinUpdatedBy</p></td>
<td><p>int</p></td>
<td><p>ID of the principal that last updated this.</p></td>
</tr>
<tr class="odd">
<td><p>prinUpdatedOn</p></td>
<td><p>bigint, not null</p></td>
<td><p>Time stamp for the last update.</p></td>
</tr>
<tr class="even">
<td><p>prinVerifiedOn</p></td>
<td><p>datetime, not null</p></td>
<td><p>Date and time of the last Active Directory Sync refresh for the principal.</p></td>
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
<th>Column</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>prinID</p></td>
<td><p>Primary key.</p></td>
</tr>
<tr class="even">
<td><p>prinTypeID</p></td>
<td><p>Foreign key with lookup in tblPrincipalType.ptypeID table.</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

