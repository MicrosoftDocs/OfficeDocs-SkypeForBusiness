---
title: 'Lync Server 2013: Changes made by forest preparation'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Changes made by forest preparation
ms:assetid: 2e12613e-59f2-4810-a32d-24a9789a4a6e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425791(v=OCS.15)
ms:contentKeyID: 48183734
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Changes made by forest preparation in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-30_

This section describes the global settings and objects, and the universal service and administration groups that are created by the forest preparation step.

<div>

## Active Directory Global Settings and Objects

If you store global settings in the Configuration container (as is the case for all new Lync Server 2013 deployments), forest preparation uses the existing Services container and adds an **RTC Service** object under the Configuration\\Services object. Under the RTC Service object, forest preparation adds a **Global Settings** object of type msRTCSIP-GlobalContainer. The global settings object holds all the settings that apply to the Lync Server deployment. If you store global settings in the System container, forest preparation uses a Microsoft container under the root domain System container and an RTC Service object under the System\\Microsoft object.

Forest preparation also adds a new **msRTCSIP-Domain** object for the root domain in which the procedure is run.

</div>

<div>

## Active Directory Universal Service and Administration Groups

Forest preparation creates universal groups based on the domain that you specify and adds access control entries (ACEs) for these groups. This step creates the universal groups in the User containers of the domain that you specify.

Universal groups allow administrators to access and manage global settings and services. Forest preparation adds the following types of universal groups:

  - **Administrative groups**   These groups define administrator roles for a Lync Server network.

  - **Infrastructure groups**   These groups provide permission to access specific areas of the Lync Server infrastructure. They function as components of administrative groups. You should not modify these groups or add users directly to them.

  - **Service groups**   These groups are service accounts that are required to access various Lync Server services.

The following table describes the administrative groups.

### Administrative Groups Created During Forest Preparation

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Administrative group</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCUniversalServerAdmins</p></td>
<td><p>Allows members to manage server and pool settings, including all server roles, global settings, and users.</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>Allows members to manage user settings and move users from one server or pool to another.</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalReadOnlyAdmins</p></td>
<td><p>Allows members to read server, pool, and user settings.</p></td>
</tr>
</tbody>
</table>


The following table describes the infrastructure groups.

### Infrastructure Groups Created During Forest Preparation

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Infrastructure group</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCUniversalGlobalWriteGroup</p></td>
<td><p>Grants write access to global setting objects for Lync Server.</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalGlobalReadOnlyGroup</p></td>
<td><p>Grants read-only access to global setting objects for Lync Server.</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>Grants read-only access to Lync Server user settings.</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalServerReadOnlyGroup</p></td>
<td><p>Grants read-only access to Lync Server settings. This group does not have access to pool level settings, only to settings specific to an individual server.</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalSBATechnicians</p></td>
<td><p>Grants read-only access to Lync Server configuration and are placed in the Local Administrators group of the survivable branch appliances during installation.</p></td>
</tr>
</tbody>
</table>


The following table describes the service groups.

### Service Groups Created During Forest Preparation

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Service group</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCHSUniversalServices</p></td>
<td><p>Includes service accounts used to run Front End Server and Standard Edition servers. This group allows servers read/write access to Lync Server global settings and Active Directory user objects.</p></td>
</tr>
<tr class="even">
<td><p>RTCComponentUniversalServices</p></td>
<td><p>Includes service accounts used to run A/V Conferencing Servers, Web Services, Mediation Server, Archiving Server, and Monitoring Server.</p></td>
</tr>
<tr class="odd">
<td><p>RTCProxyUniversalServices</p></td>
<td><p>Includes service accounts used to run Lync Server Edge Servers.</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalConfigReplicator</p></td>
<td><p>Includes servers that can participate in Lync Server Central Management store replication.</p></td>
</tr>
<tr class="odd">
<td><p>RTCSBAUniversalServices</p></td>
<td><p>Grants read-only access to Lync Server settings, but allows for configuration for the installation of a survivable branch server and survivable branch appliance deployment.</p></td>
</tr>
</tbody>
</table>


Forest preparation then adds service and administration groups to the appropriate infrastructure groups, as follows:

  - RTCUniversalServerAdmins is added to RTCUniversalGlobalReadOnlyGroup, RTCUniversalGlobalWriteGroup, RTCUniversalServerReadOnlyGroup, and RTCUniversalUserReadOnlyGroup.

  - RTCUniversalUserAdmins is added as a member of RTCUniversalGlobalReadOnlyGroup, RTCUniversalServerReadOnlyGroup, and RTCUniversalUserReadOnlyGroup.

  - RTCHSUniversalServices, RTCComponentUniversalServices and RTCUniversalReadOnlyAdmins are added as members of RTCUniversalGlobalReadOnlyGroup, RTCUniversalServerReadOnlyGroup, and RTCUniversalUserReadOnlyGroup.

Forest preparation also creates the following role-based access control (RBAC) groups:

  - CSAdministrator

  - CSArchivingAdministrator

  - CSHelpDesk

  - CSLocationAdministrator

  - CSResponseGroupAdministrator

  - CSServerAdministrator

  - CSUserAdministrator

  - CSViewOnlyAdministrator

  - CSVoiceAdministrator

  - CsPersistentChatAdministator

  - CsResponseGroupManager

For details about RBAC roles and the tasks allowed for each, see [Planning for role-based access control in Lync Server 2013](lync-server-2013-planning-for-role-based-access-control.md) in the Planning documentation.

Forest preparation creates both private and public ACEs. It creates private ACEs on the global settings container used by Lync Server. This container is used only by Lync Server and is located either in the Configuration container or the System container in the root domain, depending on where you store global settings. The public ACEs created by forest preparation are listed in the following table.

### Public ACEs created by Forest Preparation

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>ACE</th>
<th>RTCUniversalGlobalReadOnlyGroup</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Read root domain System Container (not inherited)<strong>*</strong></p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Read Configuration’s DisplaySpecifiers container (not inherited)</p></td>
<td><p>X</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> <STRONG>*</STRONG>ACEs that are not inherited do not grant access to child objects under these containers. ACEs that are inherited grant access to child objects under these containers.



</div>

On the Configuration container, under the Configuration naming context, forest preparation performs the following tasks:

  - Adds an entry **{AB255F23-2DBD-4bb6-891D-38754AC280EF}** for the **RTC property** page under the adminContextMenu and adminPropertyPages attributes of the language display specifier for users, contacts, and InetOrgPersons (for example, CN=user-Display,CN=409,CN=DisplaySpecifiers).

  - Adds an **RTCPropertySet** object of type **controlAccessRight** under **Extended-Rights** that applies to the User and Contact classes.

  - Adds an **RTCUserSearchPropertySet** object of type **controlAccessRight** under **Extended-Rights** that applies to User, Contact, OU, and DomainDNS classes.

  - Adds **msRTCSIP-PrimaryUserAddress** under the **extraColumns** attribute of each language organizational unit (OU) display specifier (for example, CN=organizationalUnit-Display,CN=409,CN=DisplaySpecifiers) and copies the values of the **extraColumns** attribute of the default display (for example, CN=default-Display, CN=409,CN=DisplaySpecifiers).

  - Adds **msRTCSIP-PrimaryUserAddress**, **msRTCSIP-PrimaryHomeServer**, and **msRTCSIP-UserEnabled** filtering attributes under the **attributeDisplayNames** attribute of each language display specifier for Users, Contacts, and InetOrgPerson objects (for example, in English: CN=user-Display,CN=409,CN=DisplaySpecifiers).

</div>

</div>

<span> </span>

</div>

</div>

</div>

