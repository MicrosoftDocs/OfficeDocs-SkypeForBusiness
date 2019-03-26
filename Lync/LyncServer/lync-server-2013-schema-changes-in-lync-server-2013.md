---
title: 'Lync Server 2013: Schema changes in Lync Server 2013'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Schema changes in Lync Server 2013
ms:assetid: d760cb93-77d4-4d64-adb7-416b808f36f8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398944(v=OCS.15)
ms:contentKeyID: 48185575
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Schema changes in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-18_

Before you deploy and operate Lync Server 2013, you must prepare Active Directory Domain Services by extending the schema. The schema extensions add the classes and attributes that are required by Lync Server 2013.

Lync Server 2013 requires several new classes and attributes and modifies some existing classes and attributes. In addition, much configuration information for Lync Server 2013 is stored in the Central Management store instead of in AD DS as in previous versions. The following information is still stored in AD DS in Lync Server 2013:

  - **Schema extensions**:
    
      - User object extensions
    
      - Extensions for Office Communications Server 2007 and Office Communications Server 2007 R2 classes to maintain backward compatibility with supported previous versions

<!-- end list -->

  - **Data** (stored in Lync Server extended schema and in existing schema classes):
    
      - User SIP Uniform Resource Identifier (URI) and other user settings
    
      - Contact objects for applications such as Response Group and Conferencing Attendant
    
      - A pointer to the Central Management store
    
      - Kerberos Authentication Account (an optional computer object)

This topic describes the Active Directory schema changes required by Lync Server 2013. It does not describe schema changes that were introduced by previous versions of Office Communications Server. For a list of classes and their descriptions, see [Schema classes and descriptions in Lync Server 2013](lync-server-2013-schema-classes-and-descriptions.md). For a list of attributes and their descriptions, see [Schema attributes and descriptions in Lync Server 2013](lync-server-2013-schema-attributes-and-descriptions.md). For a list of classes with the attributes they may contain, see [Schema attributes by class in Lync Server 2013](lync-server-2013-schema-attributes-by-class.md).

The msRTCSIP prefix identifies classes and attributes that are specific to Lync Server.

<div>

## New Active Directory Attributes

The following table describes the Active Directory attributes that are added by Lync Server 2013.

### Attributes Added by Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Attribute</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>msExchUserHoldPolicies</p></td>
<td><p>This multi-value attribute holds identifiers for hold policies that apply to the user. Hold policies preserve mailbox items for the user for the duration of the hold. This attribute is shared with Exchange 2013.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-UserRoutingGroupId</p></td>
<td><p>This is the SIP routing group ID. Users in the same group will register to the same Front End Server.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MirrorBackEndServer</p></td>
<td><p>This attribute is used to store the mirrored SQL Server backend used by the Front End pool.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Modified Active Directory Classes

The following table describes the Active Directory classes that are modified by Lync Server 2013.

### Classes Modified by Lync Server 2013

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Class</th>
<th>Change</th>
<th>Class or Attribute</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>User</p></td>
<td><p>add: mayContain</p>
<p>add: mayContain</p></td>
<td><p>ProxyAddresses</p>
<p>msRTCSIP-UserRoutingGroupId</p></td>
</tr>
<tr class="even">
<td><p>Contact</p></td>
<td><p>add: mayContain</p>
<p>add: mayContain</p></td>
<td><p>ProxyAddresses</p>
<p>msRTCSIP-UserRoutingGroupId</p></td>
</tr>
<tr class="odd">
<td><p>Mail-Recipient</p></td>
<td><p>add: mayContain</p></td>
<td><p>msExchUserHoldPolicies</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-GlobalTopologySetting</p></td>
<td><p>add: mayContain</p></td>
<td><p>msRTCSIP-MirrorBackEndServer</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

