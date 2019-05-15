---
title: 'Lync Server 2013: ErrorReport table'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: ErrorReport table
ms:assetid: ae0287b4-e8ca-4f8c-84ef-502897dcaa2a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412826(v=OCS.15)
ms:contentKeyID: 48185129
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# ErrorReport table in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-28_

The ErrorReport table stores information about errors that have occurred. Each record is one error occurrence. The errors are captured either by the CDR agent running on the front-end server or sent from the client.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Column</th>
<th>Data Type</th>
<th>Key/Index</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ErrorTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Primary</p></td>
<td><p>Date and time the error occurred.</p></td>
</tr>
<tr class="even">
<td><p><strong>ErrorReportSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primary</p></td>
<td><p>ID number to identify the error report. Used in conjunction with <strong>ErrorTime</strong> to uniquely identify an error report.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ErrorId</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Unique ID of the error type. See the <a href="lync-server-2013-errordef-table.md">ErrorDef table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="even">
<td><p><strong>FromUserId</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>User who originated the request that caused the error. See the <a href="lync-server-2013-users-table.md">Users table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ToUserId</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Destination user for the request that caused the error. See the <a href="lync-server-2013-users-table.md">Users table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="even">
<td><p><strong>ConferenceUriId</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Conference URI related to the error. See the <a href="lync-server-2013-conferenceuris-table.md">ConferenceUris table in Lync Server 2013</a> for more information. Typically, if ConferenceUriId is not null, then either FromUserId or ToUserId will be null.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SessionIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Foreign</p></td>
<td><p>Used in conjunction with <strong>SessionIdSeq</strong> to uniquely identify a session. See the <a href="lync-server-2013-dialogs-table.md">Dialogs table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>ID number to identify the session. Used in conjunction with <strong>SessionIdTime</strong> to uniquely identify a session. See the <a href="lync-server-2013-dialogs-table.md">Dialogs table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SourceId</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Server that sent the error report (if the report is being sent from a server component). See the <a href="lync-server-2013-servers-table.md">Servers table in Lync Server 2013</a> for more information.</p>
<p>This field was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>ApplicationId</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Server that sent the error report (if the report is being sent from a server component). See the <a href="lync-server-2013-application-table.md">Application table in Lync Server 2013</a> for more information.</p>
<p>This field was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MsDiagHeader</strong></p></td>
<td><p>image</p></td>
<td><p> </p></td>
<td><p>More information about the error.</p>
<p>This data can be converted to text format by using this syntax:</p>
<p><code>cast(cast(Detail as varbinary(max)) as varchar(max)) </code></p></td>
</tr>
<tr class="even">
<td><p><strong>ClientVersionId</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>The client version of endpoint that sends the error report. See the <a href="lync-server-2013-clientversions-table.md">ClientVersions table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IsCapturedByServer</strong></p></td>
<td><p>bit</p></td>
<td></td>
<td><p>Is the error report captured by the CDR agent running on the front-end server, or sent by the client.</p></td>
</tr>
<tr class="even">
<td><p><strong>Flag</strong></p></td>
<td><p>smallint</p></td>
<td></td>
<td><p>Reserved for future use.</p></td>
</tr>
<tr class="odd">
<td><p><strong>TelemetryId</strong></p></td>
<td><p>uniqueIdentifier</p></td>
<td></td>
<td><p>Unique identifier correlating join time information for the different components involved in a conference.</p>
<p>This field was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionSetupTime</strong></p></td>
<td><p>int</p></td>
<td></td>
<td><p>Time (in milliseconds) required for a specific component to join a conference.</p>
<p>This field was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ServerId</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Represents the fully qualified domain name of the server that generated the error report.</p></td>
</tr>
<tr class="even">
<td><p><strong>PoolId</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Represents the fully qualified domain name of the pool where the error report was generated.</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

