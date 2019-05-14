---
title: 'Lync Server 2013: Deployment process for the Announcement application'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Deployment process for the Announcement application
ms:assetid: 72c66249-c4ce-48ce-b1b9-90ebf77d7805
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398545(v=OCS.15)
ms:contentKeyID: 48184500
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deployment process for the Announcement application in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-12_

This section provides an overview of the steps involved in deploying the Announcement application. You must deploy Enterprise Voice before you configure announcements. The components required by the Announcement application are installed and enabled when you deploy Enterprise Voice.

### Announcement Deployment Process

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
<th>Roles</th>
<th>Deployment documentation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configure Announcement settings</p></td>
<td><ul>
<li><p>Create the announcement by recording and uploading audio files or by using text-to-speech (TTS).</p></li>
<li><p>Configure the unassigned number ranges in the unassigned number table and associate them with the appropriate announcement.</p></li>
</ul></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p>
<p>CsViewOnlyAdministrator</p></td>
<td><p><a href="lync-server-2013-create-an-announcement.md">Create an announcement in Lync Server 2013</a></p>
<p><a href="lync-server-2013-configure-the-unassigned-number-table.md">Configure the unassigned number table in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Verify your Announcement deployment</p></td>
<td><p>Test by listening to announcements to verify that your configuration works as expected.</p></td>
<td><p>-</p></td>
<td><p><a href="lync-server-2013-optional-verify-announcement-deployment.md">(Optional) Verify Announcement deployment in Lync Server 2013</a></p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

