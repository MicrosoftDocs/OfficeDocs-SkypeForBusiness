---
title: 'Lync Server 2013: Deployment process for integrating hosted Exchange UM'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Deployment process for integrating hosted Exchange UM with Lync Server
ms:assetid: dbec9c38-7f66-419d-b8c3-c61380052cac
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398968(v=OCS.15)
ms:contentKeyID: 48185586
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deployment process for integrating hosted Exchange UM with Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-25_

Effective planning for integrating Lync Server 2013 with hosted Exchange Unified Messaging (UM) requires that you take into account the following:

  - Prerequisites for integrating Lync Server 2013 with hosted Exchange UM

  - Steps required during the integration process

<div>

## Deployment Prerequisites for Integrating with Hosted Exchange UM

Before you can begin the integration process, you must already have deployed Lync Server 2013 (at a minimum, a Front End pool or a Standard Edition server), an Edge Server, and Lync 2013 or Lync 2010 clients.

</div>

<div>

## Integration Process

The following table provides an overview of the hosted Exchange UM integration process. For details about deployment steps, see [Providing Lync Server 2013 users voice mail on hosted Exchange UM](lync-server-2013-providing-lync-server-users-voice-mail-on-hosted-exchange-um.md) in the Deployment documentation.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Phase</th>
<th>Steps</th>
<th>Rights and permissions</th>
<th>Deployment documentation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configure the Edge Server.</p></td>
<td><ol>
<li><p>Configure the Edge Server for federation.</p></li>
<li><p>Manually replicate data to the Edge Server.</p></li>
<li><p>Configure the hosting provider on the Edge Server.</p></li>
</ol></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-configure-the-edge-server-for-integration-with-hosted-exchange-um.md">Configure the Edge Server for integration with hosted Exchange UM</a></p></td>
</tr>
<tr class="even">
<td><p>Configure hosted voice mail policy.</p></td>
<td><ol>
<li><p>Either modify the global hosted voice mail policy or create a new hosted voice mail policy with Site or Per-User scope.</p></li>
<li><p>For policies with Per-User scope, assign the policy to users or groups.</p></li>
</ol></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-manage-hosted-voice-mail-policies.md">Manage hosted voice mail policies in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Enable users for hosted voice mail.</p></td>
<td><ul>
<li><p>Configure user accounts for users whose mailboxes are on a hosted Exchange service.</p></li>
</ul></td>
<td><p>RTCUniversalUserAdmins</p></td>
<td><p><a href="lync-server-2013-enable-users-for-hosted-voice-mail.md">Enable users for hosted voice mail in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Configure hosted contact objects.</p></td>
<td><ol>
<li><p>Create auto-attendant Contact objects for hosted Exchange UM.</p></li>
<li><p>Create Subscriber Access contact objects for hosted Exchange UM.</p></li>
</ol></td>
<td><p>RTCUniversalUserAdmins</p>
<div>

> [!NOTE]  
> To create, modify or remove contact objects, the user who runs the New-CsExUmContact, Set-CsExUmContact or Remove-CsExUmContact cmdlet must have the correct permission to the Active Directory organizational unit where the new contact objects are stored. This permission can be granted by running the Grant-CsOUPermission cmdlet. For details, see the Lync Server Management Shell documentation.


</div></td>
<td><p><a href="lync-server-2013-create-contact-objects-for-hosted-exchange-um.md">Create contact objects for hosted Exchange UM in Lync Server 2013</a></p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

