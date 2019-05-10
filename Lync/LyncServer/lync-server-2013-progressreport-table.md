---
title: 'Lync Server 2013: ProgressReport table'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: ProgressReport table
ms:assetid: 38e5f060-5e9b-4185-87b2-7ef61c4bb75f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425864(v=OCS.15)
ms:contentKeyID: 48183847
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# ProgressReport table in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-28_

Progress reports are based on data uploaded by the client to the database after a call or session is completed. Progress reports will be written only for calls and sessions that Lync Server 2013 determines might be useful for diagnostic purposes.

The ErrorTime, ErrorReportSeq and ProgressReportSeq fields don’t necessarily refer to errors but to messages that indicate the status of calls or messages.


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
<td><p>Primary, Foreign</p></td>
<td><p>Date and time of the progress error report that contains this progress report. See the <a href="lync-server-2013-errorreport-table.md">ErrorReport table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="even">
<td><p><strong>ErrorId</strong></p></td>
<td><p>int</p></td>
<td><p>Primary, Foreign</p></td>
<td><p>ID number used in conjunction with ErrorTime, ProgressReportSeq to uniquely identify a progress report. See the <a href="lync-server-2013-errorreport-table.md">ErrorReport table in Lync Server 2013</a> for more information.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ErrorReportSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primary, Foreign</p></td>
<td><p>ID number that identifies the error report. ErrorReporSeq is used in conjunction with ErrorTime to uniquely identify an error report. See the <a href="lync-server-2013-errorreport-table.md">ErrorReport table in Lync Server 2013</a> for more information</p>
<p>This field was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>ProgressReportSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primary</p></td>
<td><p>ID number to identify the progress report. Used in conjunction with ErrorTime and ErrorReportSeq to uniquely identify a progress report.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MsDiagId</strong></p></td>
<td><p>int</p></td>
<td></td>
<td><p>Diagnostic ID of the progress report.</p>
<p>This field was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>SourceId</strong></p></td>
<td><p>int</p></td>
<td><p>Foreign</p></td>
<td><p>Server that sent the error report (if the report was sent from a server component). See the <a href="lync-server-2013-servers-table.md">Servers table in Lync Server 2013</a> for more information.This field was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ApplicationId</strong></p></td>
<td><p>int</p></td>
<td></td>
<td><p>The Lync Server process that the report is about. See the Application Table for more information.</p></td>
</tr>
<tr class="even">
<td><p><strong>Detail</strong></p></td>
<td><p>image</p></td>
<td></td>
<td><p>Progress report details, stored in binary format to save space.This data can be converted to text format using this syntax:</p>
<p>cast(cast(Detail as varbinary(max)) as varchar(max))</p></td>
</tr>
<tr class="odd">
<td><p><strong>TelemetryId</strong></p></td>
<td><p>uniqueIdentifier</p></td>
<td></td>
<td><p>Unique identifier that correlates join time information for the different components involved in a conference.</p>
<p>This field was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionSetupTime</strong></p></td>
<td><p>int</p></td>
<td></td>
<td><p>Time (in milliseconds) for a specific component to join a conference.</p>
<p>This field was introduced in Microsoft Lync Server 2013.</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

