---
title: Interpreting the Results
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Interpreting the Results
ms:assetid: dd7f199f-7075-4d88-bb84-49a7e05eb593
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945608(v=OCS.15)
ms:contentKeyID: 51541433
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Interpreting the Results

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-24_

The Lync Server 2013 Stress and Performance Tool (LyncPerfTool.exe) has many counters that you can use to understand what the client is doing and whether it is encountering issues.

<div>

## Client Counters

Each instance of LyncPerfTool.exe that is running has a separate instance of the counters. Each instance is named by its process ID.

If the clients are overloaded, issues can occur. To prevent these issues, do the following:

1.  Monitor the CPU and the memory usage on the client computers. If the CPU is consistently above 90 percent, reduce the number of users.

2.  If the memory footprint is high, you could run into issues if the page file is not big enough. Verify that the Commit Charge is not hitting the limit on the computer. If you are running into memory limits, consider increasing the page file size or reducing the number of users

The following tables list the key LyncPerfTool performance counters.

**General Information**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Performance Counter</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Time Spent in Minutes</p></td>
<td><p>Time spent since the process was started.</p></td>
</tr>
<tr class="even">
<td><p>Active Endpoints</p></td>
<td><p>Number of endpoints currently connected to the server.</p></td>
</tr>
<tr class="odd">
<td><p>Failed Logons</p></td>
<td><p>Total number of endpoint sign-in failures.</p></td>
</tr>
<tr class="even">
<td><p>Logon Attempts</p></td>
<td><p>Total number of endpoint sign-in attempts.</p></td>
</tr>
<tr class="odd">
<td><p>Endpoints Disconnected</p></td>
<td><p>Total number of endpoints that have been disconnected.</p></td>
</tr>
<tr class="even">
<td></td>
<td></td>
</tr>
</tbody>
</table>


**Presence Information**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Performance Counter</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>SetPresence Calls</p></td>
<td><p>Total number of presence change attempts. For different types of presence changes, see the SetPresence (Presence Type) Calls Performance Counter.</p></td>
</tr>
<tr class="even">
<td><p>NNN Responses for SetPresence</p></td>
<td><p>Total number of nnn response codes received from the server.</p></td>
</tr>
<tr class="odd">
<td><p>GetPresence Calls</p></td>
<td><p>Total number of get presence request attempts.</p></td>
</tr>
<tr class="even">
<td><p>NNN Responses for GetPresence</p></td>
<td><p>Total number of nnn response codes received from the server.</p></td>
</tr>
</tbody>
</table>


**Address Book service Information**

This category includes counters used to monitor Address Book service (ABS) file downloads and Address Book Web Query service requests.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Performance Counter</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ABS Full/Delta File Downloads Attempted</p></td>
<td><p>Total number of full or delta file download requests attempted.</p></td>
</tr>
<tr class="even">
<td><p>ABS Full/Delta File Downloads Succeeded</p></td>
<td><p>Total number of full or delta file download requests attempted.</p></td>
</tr>
<tr class="odd">
<td><p>Address Book Web Query service related counters</p></td>
<td><p>Address book file download related counters.</p></td>
</tr>
<tr class="even">
<td><p>ABS WS Calls attempted</p></td>
<td><p>Total number of Address Book Web Query service requests attempted.</p></td>
</tr>
<tr class="odd">
<td><p>ABS WS Calls Succeeded</p></td>
<td><p>Total number of Address Book Web Query service requests that returned a successful response code.</p></td>
</tr>
<tr class="even">
<td><p>ABS WS Calls Failed</p></td>
<td><p>Total number of Address Book Web Query service requests that returned an error response code.</p></td>
</tr>
</tbody>
</table>


**Distribution List (DL) Information**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Performance Counter</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Calls Attempted</p></td>
<td><p>Total number of distribution list expansion (DLX) web service requests attempted.</p></td>
</tr>
<tr class="even">
<td><p>Calls Succeeded</p></td>
<td><p>Total number of DLX web service requests that returned a successful response code.</p></td>
</tr>
<tr class="odd">
<td><p>Calls Failed</p></td>
<td><p>Total number of DLX web service requests that returned an error response code.</p></td>
</tr>
</tbody>
</table>


**VoIP Basic Information**

The performance counters listed below report numbers for all Voice over IP (VoIP) calls, including calls to Mediation Server, A/V Conferencing Server, Edge Server, Response Group application, and Conference Auto Attendant, when these scenarios are enabled.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Performance Counter</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Calls Active</p></td>
<td><p>Total number of incoming/outgoing voice calls ongoing currently.</p></td>
</tr>
<tr class="even">
<td><p>Calls Terminated</p></td>
<td><p>Total number of incoming/outgoing voice calls already terminated.</p></td>
</tr>
<tr class="odd">
<td><p>Calls Declined</p></td>
<td><p>Total number of incoming voice calls declined.</p></td>
</tr>
<tr class="even">
<td><p>Incoming/Outgoing Calls Attempted</p></td>
<td><p>Total number of incoming/outgoing voice calls attempted.</p></td>
</tr>
<tr class="odd">
<td><p>Incoming/Outgoing Calls Established</p></td>
<td><p>Total number of incoming/outgoing voice calls established.</p></td>
</tr>
<tr class="even">
<td><p>Calls Received NNN</p></td>
<td><p>Total number of nnn response codes received from the server.</p></td>
</tr>
<tr class="odd">
<td><p>VoIP Pass Rate (%)</p></td>
<td><p>Total calls established/Total calls attempted.</p></td>
</tr>
</tbody>
</table>


**Response Group service Call Information**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Performance Counter</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Calls Active</p></td>
<td><p>Total number of active calls to the Response Group application.</p></td>
</tr>
<tr class="even">
<td><p>Calls Attempted</p></td>
<td><p>Total number of calls attempted.</p></td>
</tr>
</tbody>
</table>


**Instant Messaging (IM) Call Information**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Performance Counter</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Calls Active</p></td>
<td><p>Total number of ongoing incoming/outgoing instant messaging calls.</p></td>
</tr>
<tr class="even">
<td><p>Calls Terminated</p></td>
<td><p>Total number of incoming/outgoing instant messaging calls already terminated.</p></td>
</tr>
<tr class="odd">
<td><p>Calls Received NNN</p></td>
<td><p>Total number of nnn response codes received from the server.</p></td>
</tr>
<tr class="even">
<td><p>IM Messages Received/Sent</p></td>
<td><p>Total number of messages received or sent for all sessions.</p></td>
</tr>
<tr class="odd">
<td><p>Incoming/Outgoing Calls Attempted</p></td>
<td><p>Total number of incoming/outgoing instant messaging calls attempted.</p></td>
</tr>
<tr class="even">
<td><p>Incoming/Outgoing Calls Established</p></td>
<td><p>Total number of incoming/outgoing instant message calls established.</p></td>
</tr>
</tbody>
</table>


**App Sharing Call Information**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Performance Counter</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Calls Active</p></td>
<td><p>Total number of ongoing incoming/outgoing application sharing calls.</p></td>
</tr>
<tr class="even">
<td><p>Calls Terminated</p></td>
<td><p>Total number of incoming/outgoing application sharing calls already terminated.</p></td>
</tr>
<tr class="odd">
<td><p>Calls Received NNN</p></td>
<td><p>Total number of nnn response codes received from the server.</p></td>
</tr>
<tr class="even">
<td><p>Incoming/Outgoing Calls Attempted</p></td>
<td><p>Total number of incoming/outgoing application sharing calls attempted.</p></td>
</tr>
<tr class="odd">
<td><p>Incoming/Outgoing Calls Established</p></td>
<td><p>Total number of incoming/outgoing application sharing calls established.</p></td>
</tr>
<tr class="even">
<td></td>
<td></td>
</tr>
</tbody>
</table>


**CAA Call Information**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Performance Counter</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Calls Active</p></td>
<td><p>Total number of incoming/outgoing public switched telephone network (PSTN) calls ongoing currently.</p></td>
</tr>
<tr class="even">
<td><p>Calls Terminated</p></td>
<td><p>Total number of incoming/outgoing PSTN calls already terminated.</p></td>
</tr>
<tr class="odd">
<td><p>Incoming/Outgoing Calls Attempted</p></td>
<td><p>Total number of incoming/outgoing PSTN calls attempted.</p></td>
</tr>
<tr class="even">
<td><p>Incoming/Outgoing Calls Established</p></td>
<td><p>Total number of incoming/outgoing PSTN calls established.</p></td>
</tr>
</tbody>
</table>


**Conference Information**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Performance Counter</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Active Instant Messaging Conferences</p></td>
<td><p>Total number of ongoing instant messaging conferences.</p></td>
</tr>
<tr class="even">
<td><p>Active Audio/Video Conferences</p></td>
<td><p>Total number of ongoing audio/video (A/V) conferences.</p></td>
</tr>
<tr class="odd">
<td><p>Active Application Sharing Conferences</p></td>
<td><p>Total number of ongoing application sharing conferences.</p></td>
</tr>
<tr class="even">
<td><p>Number of Participants</p></td>
<td><p>Total number of participants currently connected to conferences.</p></td>
</tr>
<tr class="odd">
<td><p>Conference Schedule Failure</p></td>
<td><p>Total number of failures while trying to schedule a conference.</p></td>
</tr>
<tr class="even">
<td><p>Join Conference Failure</p></td>
<td><p>Total number of failures while trying to connect to a conference.</p></td>
</tr>
</tbody>
</table>


**UCWA Client Counters**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Performance Counter</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Total Number of IMMCU Joins Succeeded</p></td>
<td><p>Total number of instant messaging conferences joined.</p></td>
</tr>
<tr class="even">
<td><p>Total Number of DMCU Joins Succeeded</p></td>
<td><p>Total number of A/V conferences joined.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

