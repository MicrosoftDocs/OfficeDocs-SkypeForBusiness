---
title: 'Lync Server 2013: Failure List Report'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Failure List Report
ms:assetid: b6f3a605-e0c6-461e-b17a-41d8039ace9d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg615446(v=OCS.15)
ms:contentKeyID: 48185194
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Failure List Report in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-07-02_

The Failure List report provides information about the individual participants who took part in a failed peer-to-peer or conferencing session. This information includes the URI of the user who experienced the problem, as well as the SIP Response code and Diagnostic ID associated with the failure.

<div>

## Accessing the Failure List Report

The Failure List Report is accessed by clicking any of the following metrics on the [Failure Distribution Report in Lync Server 2013](lync-server-2013-failure-distribution-report.md):

  - Top diagnostic reasons (sessions)

  - Top modalities (sessions)

  - Top pools (sessions)

  - Top sources (sessions)

  - Top components (sessions)

  - Top from users (sessions)

  - Top to users (sessions)

  - Top from user agents (sessions)

From the Failure List Report you can access the [Peer-to-Peer Session Detail Report in Lync Server 2013](lync-server-2013-peer-to-peer-session-detail-report.md) by clicking the Session detail metric for a peer-to-peer session. You can also access the Conference Detail Report by clicking the Conference metric for a conference.

</div>

<div>

## Making the Best Use of the Failure List Report

In the Failure List Report, you can view a description for each Response code or each Diagnostic ID simply by holding your mouse over that value. For example, if you hold your mouse over Diagnostic ID 7025 you'll see the following displayed in a tooltip:

Internal server error creating media for user.

It's important to note that the Failure List Report does not provide a straightforward way to directly retrieve a list of all the users who participated in at least one failed session, nor does it provide a way to determine which users were most-often involved in a failed session. (For one thing, the Failure List Report has no filtering capabilities.) However, if you export the data and then convert it to a comma-separated values file, you can use Windows PowerShell to find the answers to questions like those. For example, suppose you save the data to a .CSV file named C:\\Data\\Failure\_List.csv. Based on the data saved in that file, this command lists all the users who were involved in at least one failed session:

    $failures = Import-Csv -Path " C:\Data\Failure_List.csv"
    $failure |Sort-Object "From user" | Select-Object "From user" -Unique

That command will return a list similar to this:

    From user
    ----
    Pilar.Ackerman@litwareinc.com
    Henrik.Jensen@litwareinc.com
    Gilead.Amosnino@litwareinc.com
    David.Ahs@litwareinc.com
    Ken.Myer@litwareinc.com

These two commands report back the total number of failed sessions that each user was involved in:

    $failures = Import-Csv -Path "C:\Data\Failure_List.csv"
    $failures | Group-Object "From user" | Select-Object Count, Name | Sort-Object -Property Count -Descending

That will return data similar to this:

    Count    Name
     -----    ----
        20    Pilar.Ackerman@litwareinc.com
        20    David.Ahs@litwareinc.com
        16    Gilead.Amosnino@litwareinc.com
        16    Ken.Myero@litwareinc.com
        14    Henrik.Jensen@litwareinc.com

</div>

<div>

## Filters

None. You cannot filter the Failure List Report.

</div>

<div>

## Metrics

The following table lists the information provided in the Failure List Report for each failed call.

### Failure List Report Metrics

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
<td><p><strong>Reported time</strong></p></td>
<td><p>No</p></td>
<td><p>Date and time the report was recorded.</p></td>
</tr>
<tr class="even">
<td><p><strong>Request</strong></p></td>
<td><p>No</p></td>
<td><p>SIP request type that failed. For example, INVITE or BYE.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Response code</strong></p></td>
<td><p>No</p></td>
<td><p>SIP response code sent when the conference failed.</p></td>
</tr>
<tr class="even">
<td><p><strong>Diagnostic ID</strong></p></td>
<td><p>No</p></td>
<td><p>Unique identifier (in the form of an ms-diagnostics header) attached to a SIP message that often provides information useful in troubleshooting errors.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Join cost time (ms)</strong></p></td>
<td><p>No</p></td>
<td><p>Amount of time (in milliseconds) required for the user to join the conference.</p></td>
</tr>
<tr class="even">
<td><p><strong>From user</strong></p></td>
<td><p>No</p></td>
<td><p>SIP address of the user who initiated the call.</p></td>
</tr>
<tr class="odd">
<td><p><strong>From user agent</strong></p></td>
<td><p>No</p></td>
<td><p>Software used by the endpoint of the user who initiated the call.</p></td>
</tr>
<tr class="even">
<td><p><strong>To user</strong></p></td>
<td><p>No</p></td>
<td><p>SIP address of the user who was being called.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

