---
title: 'Lync Server 2013: Changes made by Grant-CsOUPermission'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Changes made by Grant-CsOUPermission
ms:assetid: d744d352-1ad9-4447-8e2b-28e768d2ed1b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205310(v=OCS.15)
ms:contentKeyID: 48185564
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Changes made by Grant-CsOUPermission in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-20_

To delegate Lync Server 2013 administration, you can add permissions to specified organizational units (OUs) so that members of the RTC universal groups created by forest preparation can access the OUs without being members of the Domain Admins group.

The **Grant-CsOuPermission** cmdlet grants permissions to objects in the specified OU as specified in the following tables.

<div>

## Granting Permission for User Objects

When you run the **Grant-CsOuPermission** cmdlet for User objects on an OU, groups are granted permissions as shown in the following table.

### Permissions Granted for User Objects

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Group</th>
<th>Permission</th>
<th>Applies to</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCHSUniversalServices</p></td>
<td><p>Replicating directory changes</p></td>
<td><p>This object only</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalServerReadOnlyGroup</p></td>
<td><p>List contents</p>
<p>Read all properties</p>
<p>Read permissions</p></td>
<td><p>This object only</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>List contents</p>
<p>Read all properties</p>
<p>Read permissions</p></td>
<td><p>This object only</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>Read RTCUserSearchPropertySet</p>
<p>Read RTCUserProvisioningPropertySet</p>
<p>Read RTCPropertySet</p>
<p>Read Public-Information</p>
<p>Read General-Information</p>
<p>Read User-Account-Restrictions</p></td>
<td><p>Descendant User objects</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>Write RTCUserSearchPropertySet</p>
<p>Write msExchUCVoiceMailSettings</p>
<p>Write RTCUserProvisioningPropertySet</p>
<p>Write RTCPropertySet</p>
<p>Write proxyAddresses</p></td>
<td><p>Descendant User objects</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Granting Permission for Computer Objects

When you run the **Grant-CsOuPermission** cmdlet for Computer objects on an OU, groups are granted permissions as shown in the following table.

### Permissions Granted for Computer Objects

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Group</th>
<th>Permission</th>
<th>Applies to</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCHSUniversalServices</p></td>
<td><p>Replicating directory changes</p></td>
<td><p>This object only</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalServerReadOnlyGroup</p></td>
<td><p>List contents</p>
<p>Read all properties</p>
<p>Read permissions</p></td>
<td><p>This object only</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>List contents</p>
<p>Read all properties</p>
<p>Read permissions</p></td>
<td><p>This object only</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>Read Public-Information</p>
<p>Read Validated-DNS-Host-Name</p></td>
<td><p>Descendant Computer objects</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>Read Public-Information</p>
<p>Read Validated-DNS-Host-Name</p></td>
<td><p>Descendant Computer objects</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Granting Permission for Contact or AppContact Objects

When you run the **Grant-CsOuPermission** cmdlet for Contact objects or AppContact objects on an OU, groups are granted permissions as shown in the following table.

### Permissions Granted for Contact or AppContact Objects

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Group</th>
<th>Permission</th>
<th>Applies to</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCHSUniversalServices</p></td>
<td><p>Replicating directory changes</p></td>
<td><p>This object only</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalServerReadOnlyGroup</p></td>
<td><p>List contents</p>
<p>Read all properties</p>
<p>Read permissions</p></td>
<td><p>This object only</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>List contents</p>
<p>Read all properties</p>
<p>Read permissions</p></td>
<td><p>This object only</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>Read RTCUserSearchPropertySet</p>
<p>Read RTCUserProvisioningPropertySet</p>
<p>Read RTCPropertySet</p>
<p>Read Public-Information</p>
<p>Read General-Information</p>
<p>Read Personal-Information</p>
<p>Read User-Account-Restrictions</p></td>
<td><p>Descendant Contact objects</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>Write RTCUserSearchPropertySet</p>
<p>Write otherIpPhone</p>
<p>Write displayName</p>
<p>Write description</p>
<p>Write telephoneNumber</p>
<p>Write msExchUCVoiceMailSettings</p>
<p>Write RTCUserProvisioningPropertySet</p>
<p>Write RTCPropertySet</p>
<p>Write proxyAddresses</p></td>
<td><p>Descendant Contact objects</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Granting Permission for Device Objects

When you run the **Grant-CsOuPermission** cmdlet for Device objects on an OU, groups are granted permissions as shown in the following table.

### Permissions Granted for Device Objects

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Group</th>
<th>Permission</th>
<th>Applies to</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCHSUniversalServices</p></td>
<td><p>Replicating directory changes</p></td>
<td><p>This object only</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalServerReadOnlyGroup</p></td>
<td><p>List contents</p>
<p>Read all properties</p>
<p>Read permissions</p></td>
<td><p>This object only</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>List contents</p>
<p>Read all properties</p>
<p>Read permissions</p></td>
<td><p>This object only</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>Read RTCUserSearchPropertySet</p>
<p>Read RTCUserProvisioningPropertySet</p>
<p>Read RTCPropertySet</p>
<p>Read Public-Information</p>
<p>Read Personal-Information</p>
<p>Read General-Information</p>
<p>Read User-Account-Restrictions</p></td>
<td><p>Descendant Contact objects</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>Create child</p>
<p>Delete child</p>
<p>Delete tree</p></td>
<td><p>Contact</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>Write displayName</p>
<p>Write description</p>
<p>Write telephoneNumber</p></td>
<td><p>Descendant User objects</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>Write RTCUserSearchPropertySet</p>
<p>Write otherIpPhone</p>
<p>Write displayName</p>
<p>Write description</p>
<p>Write telephoneNumber</p>
<p>Write msExchUCVoiceMailSettings</p>
<p>Write RTCUserProvisioningPropertySet</p>
<p>Write RTCPropertySet</p>
<p>Write proxyAddresses</p></td>
<td><p>Descendant Contact objects</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Granting Permission for InetOrgPerson Objects

When you run the **Grant-CsOuPermission** cmdlet for InetOrgPerson objects on an OU, groups are granted permissions as shown in the following table.

### Permissions Granted for InetOrgPerson Objects

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Group</th>
<th>Permission</th>
<th>Applies to</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCHSUniversalServices</p></td>
<td><p>Replicating directory changes</p></td>
<td><p>This object only</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalServerReadOnlyGroup</p></td>
<td><p>List contents</p>
<p>Read all properties</p>
<p>Read permissions</p></td>
<td><p>This object only</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>List contents</p>
<p>Read all properties</p>
<p>Read permissions</p></td>
<td><p>This object only</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>Read RTCUserSearchPropertySet</p>
<p>Read RTCUserProvisioningPropertySet</p>
<p>Read RTCPropertySet</p>
<p>Read Personal-Information</p>
<p>Read Public-Information</p>
<p>Read General-Information</p>
<p>Read User-Account-Restrictions</p></td>
<td><p>Descendant inetOrgPerson objects</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>Write RTCUserSearchPropertySet</p>
<p>Write RTCUserProvisioningPropertySet</p>
<p>Write RTCPropertySet</p>
<p>Write proxyAddresses</p></td>
<td><p>Descendant inetOrgPerson objects</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

