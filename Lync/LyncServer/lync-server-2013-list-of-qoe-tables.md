---
title: 'Lync Server 2013: List of QoE tables'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: List of QoE tables
ms:assetid: 176194d7-d184-4e23-94bb-cb62b4db47f5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398236(v=OCS.15)
ms:contentKeyID: 48183512
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# List of QoE tables in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-02_

The database schema consists of the following tables.

**Supporting Tables**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Table</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-appsharingmetricsthreshold-table.md">AppSharingMetricsThreshold table in Lync Server 2013</a></p></td>
<td><p>Stores optimal and acceptable values for the Quality of Experience metrics used with application sharing.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-codecdescription-table.md">CodecDescription table in Lync Server 2013</a></p></td>
<td><p>Maps unique codec identifiers to their corresponding codec.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-ipaddress-table.md">IPAddress table in Lync Server 2013</a></p></td>
<td><p>Maps IP addresses to the unique IP address identifiers used elsewhere in the Quality of Experience database.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-networkconnectiondetail-table.md">NetworkConnectionDetail table in Lync Server 2013</a></p></td>
<td><p>Maps network connection types to the network connection identifiers used elsewhere in the Quality of Experience database.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-purgesettings-table-qoe.md">PurgeSettings table (QoE) in Lync Server 2013</a></p></td>
<td><p>Stores information that specifies if (and when) outdated Quality of Experience records will automatically be deleted from the QoE database.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-traceroute-table.md">TraceRoute table in Lync Server 2013</a></p></td>
<td><p>Stores routing information for calls.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-useragentdef-table-qoe.md">UserAgentDef table (QoE) in Lync Server 2013</a></p></td>
<td><p>Maps user agent identifiers to the agent’s descriptive names.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-videometricsthreshold-table.md">VideoMetricsThreshold table in Lync Server 2013</a></p></td>
<td><p>Stores optimal and acceptable values for the Quality of Experience metrics used with video calls.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-useragent-table.md">UserAgent table in Lync Server 2013</a></p></td>
<td><p>Stores Session Initiation Protocol (SIP) User Agent (UA) strings and UA types used in audio and video sessions.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-user-table.md">User table in Lync Server 2013</a></p></td>
<td><p>Stores user, conference, and phone URIs used in audio and video sessions.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-endpoint-table.md">Endpoint table in Lync Server 2013</a></p></td>
<td><p>Stores FQDN computer names of endpoints participating in audio and video sessions.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-pool-table.md">Pool table in Lync Server 2013</a></p></td>
<td><p>Stores the names of pools to which metrics data belongs.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-device-table.md">Device table in Lync Server 2013</a></p></td>
<td><p>Stores capture devices and render devices which are used in an audio/video calls.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-devicedriver-table.md">DeviceDriver table in Lync Server 2013</a></p></td>
<td><p>Stores driver for the capture device and the render device which are used in audio/video calls.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-conference-table.md">Conference table in Lync Server 2013</a></p></td>
<td><p>Stores Conference URIs for conference scenarios or DialogID for other scenarios.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-sessioncorrelation-table.md">SessionCorrelation table in Lync Server 2013</a></p></td>
<td><p>Stores CorrelationID for PSTN calls.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-payloaddescription-table.md">PayloadDescription table in Lync Server 2013</a></p></td>
<td><p>Stores the Codec used in audio/video calls.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-appliedbandwidthsource-table.md">AppliedBandwidthSource table in Lync Server 2013</a></p></td>
<td><p>Stores the bandwidth source used in audio/video calls.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-macaddress-table.md">MacAddress table in Lync Server 2013</a></p></td>
<td><p>Stores the MAC address of the endpoints participating in audio and video sessions.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-dialog-table.md">Dialog table in Lync Server 2013</a></p></td>
<td><p>Stores the Dialog ID of audio and video sessions.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-region-table.md">Region table in Lync Server 2013</a></p></td>
<td><p>Stores the network region defined in NCS setting.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-usersite-table.md">UserSite table in Lync Server 2013</a></p></td>
<td><p>Stores the network site defined in NCS setting.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-subnet-table.md">Subnet table in Lync Server 2013</a></p></td>
<td><p>Stores the subnet defined in NCS setting.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-monitoredregionlink-table.md">MonitoredRegionLink table in Lync Server 2013</a></p></td>
<td><p>Stores the region link defined in NCS setting.</p></td>
</tr>
<tr class="odd">
<td><p><a href="monitoredusersitelink-table.md">MonitoredUserSiteLink table</a></p></td>
<td><p>Stores the network site links defined in NCS setting.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-endpointsubnet-table.md">EndpointSubnet table in Lync Server 2013</a></p></td>
<td><p>Stores the subnet of the endpoint participating in an audio and video session.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-server-table.md">Server table in Lync Server 2013</a></p></td>
<td><p>Stores the FQDN or IP address of the server the media goes through.</p></td>
</tr>
</tbody>
</table>


**Tables for metrics data**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Table</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-appsharingstream-table.md">AppSharingStream table in Lync Server 2013</a></p></td>
<td><p>Stores Quality of Experience metrics for the network streams used for application sharing. Quality of Experience metrics for the network streams used for application sharing.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-session-table.md">Session table in Lync Server 2013</a></p></td>
<td><p>Stores overall information about an audio or audio/video session. A session is defined as an audio or video SIP dialog between two endpoints.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-medialine-table.md">MediaLine table in Lync Server 2013</a></p></td>
<td><p>Stores information about each media line in a session. A media line is a collection of one or more audio and video streams. Typically, a single media line will have two streams, either audio or video.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-audiostream-table.md">AudioStream table in Lync Server 2013</a></p></td>
<td><p>Stores audio media quality metrics for each audio stream in the media line.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-audiosignal-table.md">AudioSignal table in Lync Server 2013</a></p></td>
<td><p>Stores audio media quality metrics in the media line. This includes acoustic echo cancellation (AEC) and automatic gain control (AGC) metrics.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-videostream-table.md">VideoStream table in Lync Server 2013</a></p></td>
<td><p>Stores video media quality metrics for each audio stream in the media line.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-audioclientevent-table.md">AudioClientEvent table in Lync Server 2013</a></p></td>
<td><p>Stores audio media quality metrics collected from the client event.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-videoclientevent-table.md">VideoClientEvent table in Lync Server 2013</a></p></td>
<td><p>Stores video media quality metrics collected from the client event.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DiagnosticData Table</strong></p></td>
<td><p>Stores diagnostic data which is for internal use only.</p></td>
</tr>
</tbody>
</table>


**Tables for summary data**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Table</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ServerSummary Table</strong></p></td>
<td><p>Stores summary data for the servers, these data is used for Quality of Experience (QoE) reporting only.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserSummary Table</strong></p></td>
<td><p>Stores summary data for users, these data is used for QoE reporting only.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallTypeSummary Table</strong></p></td>
<td><p>Store summary data for call types, these data is used for QoE reporting only.</p></td>
</tr>
</tbody>
</table>


**Tables for Internal Use by Monitoring Server**


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Table</strong></th>
<th><strong>Description</strong></th>
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
<td><p><strong>FrontEnd Table</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="even">
<td><p><strong>Task Table</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SummaryTableConfiguration</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="even">
<td><p><strong>DbErrorMessage</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MetricsThreshold</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="even">
<td><p><strong>DaylightSavingYears</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="odd">
<td><p><strong>TimeZoneConfiguration</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="even">
<td><p><strong>TimeZones</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallSummary Table</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceCallSumary Table</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Tenant Table</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="even">
<td><p><strong>VideoCallSummaryTable</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ASCallSummaryTable</strong></p></td>
<td><p>For internal use only.</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

