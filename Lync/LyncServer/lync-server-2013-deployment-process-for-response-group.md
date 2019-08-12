---
title: 'Lync Server 2013: Deployment process for Response Group'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Deployment process for Response Group
ms:assetid: d390c8a1-dc6e-44d8-b386-2be1fca9877c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205270(v=OCS.15)
ms:contentKeyID: 48185437
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deployment process for Response Group in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-27_

This section provides an overview of the phases and steps involved in deploying the Response Group application.

### Response Group Deployment Process

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
<th>Permissions</th>
<th>Deployment documentation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Install the Response Group application</p></td>
<td><p>The Response Group application is installed and activated by default when you deploy Enterprise Voice.</p></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-deploying-enterprise-voice.md">Deploying Enterprise Voice in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Install components for Response Group</p></td>
<td><p>Lync Server cmdlets, the Lync Server Control Panel, Response Group Configuration Tool, agents' sign-in and sign-out console, and Response Group Client Web service are installed as part of Web Services. Web Services is installed when you deploy an Enterprise Edition pool or a Standard Edition server.</p></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-deploying-lync-server.md">Deploying Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Enable users for Lync 2013 and for Enterprise Voice</p></td>
<td><p>Enable users who will be agents for Lync Server and Enterprise Voice. Users must be enabled before you can add them to agent groups. Typically, users are enabled for Lync Server during the Enterprise Edition or Standard Edition server deployment. Users are enabled for Enterprise Voice during the Enterprise Voice deployment.</p></td>
<td><p>RTCUniversalUserAdmins</p>
<p>CsUserAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-disable-or-re-enable-user-account-for-lync-server.md">Disable or re-enable user account for Lync Server 2013</a></p>
<p><a href="lync-server-2013-enable-users-for-enterprise-voice.md">Enable users for Enterprise Voice in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Create and configure response groups, which consist of agent groups, queues, and workflows</p></td>
<td><ol>
<li><p>Use the Lync Server Control Panel or Lync Server Management Shell to do the following:</p>
<ol>
<li><p>Create and configure agent groups.</p></li>
<li><p>Create and configure queues.</p></li>
</ol></li>
<li><p>Optionally, use Lync Server Management Shell to create predefined response group business hours and holidays.</p></li>
<li><p>Use the Response Group Configuration Tool or Lync Server Management Shell to create workflows (hunt groups or interactive voice response (IVR) call flows), including custom response group business hours and holidays.</p>
<div>

> [!NOTE]  
> You can access the Response Group Configuration Tool through Lync Server Control Panel.


</div></li>
</ol></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsResponseGroupAdministrator</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p>
<p>CsResponseGroupManager</p></td>
<td><p><a href="lync-server-2013-create-response-group-agent-groups.md">Create Response Group agent groups Lync Server 2013</a></p>
<p><a href="lync-server-2013-create-response-group-queues.md">Create Response Group queues in Lync Server 2013</a></p>
<p><a href="lync-server-2013-optional-define-response-group-business-hours.md">(Optional) Define Response Group business hours in Lync Server 2013</a></p>
<p><a href="lync-server-2013-optional-define-response-group-holiday-sets.md">(Optional) Define Response Group holiday sets in Lync Server 2013</a></p>
<p><a href="lync-server-2013-create-or-modify-a-workflow.md">Create or modify a workflow in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>(Optional) Customize application-level settings</p></td>
<td><p>Use Lync Server Management Shell to customize the default music-on-hold configuration, the default music-on-hold audio file, the agent ringback grace period, and the call context configuration.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsResponseGroupAdministrator</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-managing-application-level-response-group-settings.md">Managing application-level Response Group settings in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>(Optional) Delegate management of response groups</p></td>
<td><p>Assign users the CsResponseGroupManager role to delegate configuration of response groups. Response Group Managers can then configure the response groups assigned to them.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsResponseGroupAdministrator</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-planning-for-role-based-access-control.md">Planning for role-based access control in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Verify your Response Group deployment</p></td>
<td><p>Test answering calls to your hunt group and interactive voice response workflows to ensure that your configuration works as expected.</p></td>
<td><p>-</p></td>
<td><p>-</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

