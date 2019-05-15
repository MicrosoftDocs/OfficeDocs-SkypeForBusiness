---
title: 'Lync Server 2013: List of CDR tables'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: List of CDR tables
ms:assetid: 031843fd-c7ff-4534-9b02-8847aad70807
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398084(v=OCS.15)
ms:contentKeyID: 48183254
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# List of CDR tables in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-18_

The call detail recording (CDR) database schema consists of the following tables.

<div>

## Static Tables


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Table</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-callpriorities-table.md">CallPriorities table in Lync Server 2013</a></p></td>
<td><p>Stores the list of possible call priorities, such as emergency, urgent, normal, non-urgent, and more.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-conferencejointimethresholds-table.md">ConferenceJoinTimeThresholds table in Lync Server 2013</a></p></td>
<td><p>Stores the classification boundaries used by the Conference Join Time Summary Report.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-deregistertype-table.md">DeRegisterType table in Lync Server 2013</a></p></td>
<td><p>Stores the list of possible user de-register reasons, such as &quot;client initiated,&quot; &quot;registration expired,&quot; &quot;client crash,&quot; and more.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-medialist-table.md">MediaList table in Lync Server 2013</a></p></td>
<td><p>Stores the list of media types that can generate entries in the database (for example, IM, audio, video, and file transfer).</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-purgesettings-table.md">PurgeSettings table in Lync Server 2013</a></p></td>
<td><p>Stores information that specifies if (and when) outdated call detail records will automatically be deleted from the CDR database.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-roles-table.md">Roles table in Lync Server 2013</a></p></td>
<td><p>Stores the list of possible conference roles (for example, attendee and presenter).</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-sipresponsemetadata-table.md">SIPResponseMetaData table in Lync Server 2013</a></p></td>
<td><p>Stores a list of SIP response codes and the classification and definition of each of those codes.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Supporting Tables


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Table</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-clientversions-table.md">ClientVersions table in Lync Server 2013</a></p></td>
<td><p>Stores the clients (both client type and version number) of each client involved in a call with information captured in this database.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-conferenceuris-table.md">ConferenceUris table in Lync Server 2013</a></p></td>
<td><p>Stores a list of ConferenceURIs that are used in conference related calls.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-contenttypes-table.md">ContentTypes table in Lync Server 2013</a></p></td>
<td><p>Stores a list of Session Initiation Protocol (SIP) content types that are used in both peer-to-peer calls and conference calls.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-devices-table.md">Devices table in Lync Server 2013</a></p></td>
<td><p>Stores a list of devices, including their manufacturer, hardware version, and MAC address.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-dialogs-table.md">Dialogs table in Lync Server 2013</a></p></td>
<td><p>Stores information about the Dialog ID for each session in the database.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-edgeservers-table.md">EdgeServers table in Lync Server 2013</a></p></td>
<td><p>Stores a list of Edge Servers that are used for external calls.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-gateways-table.md">Gateways table in Lync Server 2013</a></p></td>
<td><p>Stores a list of Gateways that are used for Voice over Internet Protocol (VoIP) calls.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-hardwareversions-table.md">HardwareVersions table in Lync Server 2013</a></p></td>
<td><p>Stores a list of hardware versions of devices (desk phone).</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-manufacturers-table.md">Manufacturers table in Lync Server 2013</a></p></td>
<td><p>Stores a list of manufacturers of devices (desk phone).</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-mcus-table.md">Mcus table in Lync Server 2013</a></p></td>
<td><p>Stores information about the various A/V Conferencing Servers and their URIs.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-mediationservers-table.md">MediationServers table in Lync Server 2013</a></p></td>
<td><p>Stores a list of Mediation Servers that are used for VoIP calls.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-phones-table.md">Phones table in Lync Server 2013</a></p></td>
<td><p>Stores all the phone numbers used in VoIP calls that were archived or whose call details were recorded.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-pools-table.md">Pools table in Lync Server 2013</a></p></td>
<td><p>Stores the names of the pool on which IM messages are captured.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-servers-table.md">Servers table in Lync Server 2013</a></p></td>
<td><p>Stores the name of servers involved in calls.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tenants-table.md">Tenants table in Lync Server 2013</a></p></td>
<td><p>Stores the tenants supported by current deployment. There some build-in tenants for Enterprise user, Federated User, public IM connectivity user, and Anonymous users.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-useragentdef-table.md">UserAgentDef table in Lync Server 2013</a></p></td>
<td><p>Maps user agent identifiers to the agent’s descriptive names.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-users-table.md">Users table in Lync Server 2013</a></p></td>
<td><p>Stores the user URIs of users who have participated in sessions recorded or archived in this database.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-userstatistics-table.md">UserStatistics table in Lync Server 2013</a></p></td>
<td><p>Stores information about an individual user’s usage of the system.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Tables Specific to Conference CDR Records


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Table</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-conferences-table.md">Conferences table in Lync Server 2013</a></p></td>
<td><p>Stores information about all conferences that were archived or whose details were recorded, including ConferenceURI, and start and end time.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-conferencesessiondetails-table.md">ConferenceSessionDetails table in Lync Server 2013</a></p></td>
<td><p>Stores information about every SIP-based conference session, including start and end time, user ID, response code, and diagnostic ID for each session.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-focusjoinsandleaves-table.md">FocusJoinsAndLeaves table in Lync Server 2013</a></p></td>
<td><p>Stores information about conference joins and leaves, including users’ role and client version.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-mcujoinsandleaves-table.md">McuJoinsAndLeaves table in Lync Server 2013</a></p></td>
<td><p>Stores information about the A/V Conferencing Servers that are involved in a conference and the user join and leave times.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Tables for Messages in IM Conferences


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Table</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-conferencemessagecount-table.md">ConferenceMessageCount table in Lync Server 2013</a></p></td>
<td><p>For each IM conference, stores the number of messages that were sent by each user.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-imreportsummary-table.md">IMReportSummary table in Lync Server 2013</a></p></td>
<td><p>Provides an overall report on the instant messaging sessions held in an organization.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Tables for Peer-to-Peer Sessions


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Table</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-sessiondetails-table.md">SessionDetails table in Lync Server 2013</a></p></td>
<td><p>Stores information about every peer-to-peer session, including start and end time, user ID, response code, and message count for each user.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-filetransfers-table.md">FileTransfers table in Lync Server 2013</a></p></td>
<td><p>Stores information about file transfer sessions, including file name and result (accepted, rejected, or canceled).</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-media-table.md">Media table in Lync Server 2013</a></p></td>
<td><p>Stores information about the different media types involved in peer-to-peer sessions.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Table for VoIP Call Details


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Table</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-voipdetails-table.md">VoipDetails table in Lync Server 2013</a></p></td>
<td><p>For each two-party VoIP/PSTN call, stores information about the call, such as the phone ID of VoIP phone, gateway used, and which party disconnected. Refers to the <a href="lync-server-2013-sessiondetails-table.md">SessionDetails table in Lync Server 2013</a> for call start/end times and response code.</p>
<div>

> [!NOTE]  
> If one party on a call is a VoIP user or if a Mediation Server was involved in the call, a record will be created in this table. Information about VoIP/VoIP calls not involving a public switched telephone network (PSTN) phone is captured in the <A href="lync-server-2013-sessiondetails-table.md">SessionDetails table in Lync Server 2013</A>.


</div></td>
</tr>
</tbody>
</table>


</div>

<div>

## Table for E9-1-1 Call Auditing


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Table</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-locations-table.md">Locations table in Lync Server 2013</a></p></td>
<td><p>For each emergency call, such as an Enhanced 9-1-1 (E9-1-1) call, stores location information about the call. Refers to the <a href="lync-server-2013-sessiondetails-table.md">SessionDetails table in Lync Server 2013</a> for call start/end times and response code.</p>
<div>

> [!NOTE]  
> This table only contains the location blob for the E9-1-1 call. Refers to the SessionDetails table for other detailed information about the call.


</div></td>
</tr>
</tbody>
</table>


</div>

<div>

## Tables for Troubleshooting


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Table</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-application-table.md">Application table in Lync Server 2013</a></p></td>
<td><p>Stores information about various processes within Lync Server 2013 that are involved in routing and connections.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-calltype-table.md">CallType table in Lync Server 2013</a></p></td>
<td><p>Stores information about types of the call, such as, “audio”, “Instant Messaging”, “audio and video” and “application sharing”.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-errorcategory-table.md">ErrorCategory table in Lync Server 2013</a></p></td>
<td><p>Stores the friendly name for each Microsoft Lync Server 2013 diagnostic classification.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-errordef-table.md">ErrorDef table in Lync Server 2013</a></p></td>
<td><p>Stores information about types of errors and their definitions.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-errorreport-table.md">ErrorReport table in Lync Server 2013</a></p></td>
<td><p>Stores information about errors that have occurred.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-progressreport-table.md">ProgressReport table in Lync Server 2013</a></p></td>
<td><p>Stores information about the progress reports of various steps involved in Lync Server 2013 processes.</p></td>
</tr>
</tbody>
</table>


The tables in the following list are used internally by Lync Server. Their details are not described in this document.

</div>

<div>

## Tables for Internal Use by Lync Server


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Table</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>DbConfigDateTime</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="even">
<td><p><strong>DbConfigInt</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DbErrorMessage</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="even">
<td><p><strong>FrontEnd Table</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MSMQProcessing Table</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="even">
<td><p><strong>SummaryTableConfiguration</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Syndicators Table</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="even">
<td><p><strong>SyndicatorsTenantMap Table</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Task Table</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserStatistics</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UsageSummary_UQ</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="even">
<td><p><strong>UsageSummary</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DaylightSavingYears</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="even">
<td><p><strong>TimeZoneConfiguration</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="odd">
<td><p><strong>TimeZones</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="even">
<td><p><strong>FailureSummary_UQ</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="odd">
<td><p><strong>FailureSummary</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="even">
<td><p><strong>ServerSummary</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MsDiagMetaData</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

