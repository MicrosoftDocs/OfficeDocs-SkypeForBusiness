---
title: 'Lync Server 2013: Diagnostic Report'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Diagnostic Report
ms:assetid: b389dbd9-f2e8-4184-93d0-2e504796ac16
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg615445(v=OCS.15)
ms:contentKeyID: 48185159
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Diagnostic Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-07_

The Diagnostic Report provides diagnostic and troubleshooting information for a failed session. This information includes both the Diagnostic ID and the Diagnostic header that were reported when the session failed. The Diagnostic ID is a unique identifier (in the form of an ms-diagnostics header) that gets attached to a SIP message, while the Diagnostic header provides an accompanying description for the Diagnostic ID. The report might also contain valuable troubleshooting details that are known by the reporting component. For example:

  - The cause code provided by the PSTN gateway that generated the failure. When an outgoing call fails on the PSTN network, an ISDN User Part (ISUP) cause code is automatically generated. For example, a PSTN gateway might send cause code 34 to indicate that no circuit or channel was available for completing the call.

  - Peer FQDN, port, and Winsock errors for connectivity failures.

  - Names being looked up for DNS resolution failures. DNS resolution takes place any time a client contacts a name server and requests the IP address that corresponds to specified device name.

<div>

## Accessing the Diagnostic Report

The Diagnostic Report can be accessed by clicking the Diagnostic Report (Detail) metric on either the [Peer-to-Peer Session Detail Report in Lync Server 2013](lync-server-2013-peer-to-peer-session-detail-report.md) or the Conference Detail Report.

</div>

<div>

## Filters

None. You cannot filter the Diagnostic Report.

</div>

<div>

## Metrics

The following table lists the information provided in the Diagnostic Report for each session.

### Diagnostic Report Metrics

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Can you sort on this item?</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Report time</strong></p></td>
<td><p>No</p></td>
<td><p>Date and time that the report was recorded.</p></td>
</tr>
<tr class="even">
<td><p><strong>Response code</strong></p></td>
<td><p>No</p></td>
<td><p>SIP response code sent when the session failed.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Request type</strong></p></td>
<td><p>No</p></td>
<td><p>SIP request type that failed. For example, INVITE, BYE, or SERVICE.</p></td>
</tr>
<tr class="even">
<td><p><strong>Source</strong></p></td>
<td><p>No</p></td>
<td><p>Source of the error.</p></td>
</tr>
<tr class="odd">
<td><p><strong>From user URI</strong></p></td>
<td><p>No</p></td>
<td><p>SIP address of the user who initiated the session.</p></td>
</tr>
<tr class="even">
<td><p><strong>From user agent</strong></p></td>
<td><p>No</p></td>
<td><p>Software used by the endpoint of the user who initiated the session.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Diagnostic ID</strong></p></td>
<td><p>No</p></td>
<td><p>Unique identifier (in the form of an ms-diagnostics header) attached to a SIP message that often provides information useful in troubleshooting errors.</p></td>
</tr>
<tr class="even">
<td><p><strong>Content type</strong></p></td>
<td><p>No</p></td>
<td><p>Type of media content that failed. For example, a common content type is Application/sdp. Session Description Protocol (SDP) is a standard Internet protocol used for session announcements, session invitations, and other forms of multimedia session initiation.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Application</strong></p></td>
<td><p>No</p></td>
<td><p>Application involved in the error.</p></td>
</tr>
<tr class="even">
<td><p><strong>To user URI</strong></p></td>
<td><p>No</p></td>
<td><p>SIP address of the user who was invited to the session.</p></td>
</tr>
<tr class="odd">
<td><p>Conference join times (ms)</p></td>
<td><p>No</p></td>
<td><p>Amount of time (in milliseconds) it took for the user to join the conference.</p></td>
</tr>
<tr class="even">
<td><p><strong>Diagnostic header</strong></p></td>
<td><p>No</p></td>
<td><p>Diagnostic ID description.</p></td>
</tr>
</tbody>
</table>


A list of diagnostic errors can be found on the [Ms-Diagnostics Header page](http://msdn.microsoft.com/en-us/library/gg132446\(v=office.12\).aspx).

</div>

</div>

<span> </span>

</div>

</div>

</div>

