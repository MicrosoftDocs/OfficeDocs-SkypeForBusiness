---
title: 'Lync Server 2013: Mobility performance counters'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Mobility performance counters
ms:assetid: d18ed85a-673d-4695-aa3f-ac83a38ab90a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh690046(v=OCS.15)
ms:contentKeyID: 48185441
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Mobility performance counters in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

The following tables list the names and descriptions of performance counters that you can use to monitor servers running the Unified Communications Web API (UCWA) and the Lync Server 2013 Mcx Mobility Service.

The category name for the counters in the UCWA table is **LS:WEB – UCWA**.

The category name for the counters in the Mcx Mobility Service table is **LS:WEB - Mobile Communication Service**.

<div>

## Performance Counters for UCWA


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Counter</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Active Application Count</p></td>
<td><p>The current number of applications</p></td>
</tr>
<tr class="even">
<td><p>Active Application Sharing Modality Count</p></td>
<td><p>The current number of Application Sharing modality</p></td>
</tr>
<tr class="odd">
<td><p>Active Audio Modality Count</p></td>
<td><p>The current number of Audio modality</p></td>
</tr>
<tr class="even">
<td><p>Active Data Collaboration Modality Count</p></td>
<td><p>The current number of Data Collaboration modality</p></td>
</tr>
<tr class="odd">
<td><p>Active Directory Photo Get Latency (ms)</p></td>
<td><p>This counter shows the average time (in milliseconds) to retrieve a photo from active directory</p></td>
</tr>
<tr class="even">
<td><p>Active Messaging Modality Count</p></td>
<td><p>The current number of Messaging modality</p></td>
</tr>
<tr class="odd">
<td><p>Active Panoramic Video Modality Count</p></td>
<td><p>The current number of Panoramic Video modality</p></td>
</tr>
<tr class="even">
<td><p>Active Pending Get Count</p></td>
<td><p>The number of currently active pending gets; long-held connections to the server</p></td>
</tr>
<tr class="odd">
<td><p>Active Session Count</p></td>
<td><p>The current number of endpoints registered in UCWA per application and total</p></td>
</tr>
<tr class="even">
<td><p>Active User Instance Count</p></td>
<td><p>The current number of user instances</p></td>
</tr>
<tr class="odd">
<td><p>Active User Instances without Application</p></td>
<td><p>The current number of user instances without application</p></td>
</tr>
<tr class="even">
<td><p>Active Video Modality Count</p></td>
<td><p>The current number of Video modality</p></td>
</tr>
<tr class="odd">
<td><p>Application Creation Requests Received/Second</p></td>
<td><p>The per second rate of received application creation requests</p></td>
</tr>
<tr class="even">
<td><p>AS MCU Join Failures</p></td>
<td><p>The number of AS MCU Join Failures</p></td>
</tr>
<tr class="odd">
<td><p>AV MCU Join Failures</p></td>
<td><p>The number of AV MCU Join Failures</p></td>
</tr>
<tr class="even">
<td><p>Average Application Startup Time (ms)</p></td>
<td><p>The average application startup time in Milliseconds</p></td>
</tr>
<tr class="odd">
<td><p>Average Lifetime for Session (ms)</p></td>
<td><p>The average lifetime for a session in milliseconds</p></td>
</tr>
<tr class="even">
<td><p>Data MCU Join Failures</p></td>
<td><p>The number of Data MCU Join Failures</p></td>
</tr>
<tr class="odd">
<td><p>Exchange Contact Search Latency (ms)</p></td>
<td><p>This counter shows the average time (in milliseconds) to search contact in Exchange</p></td>
</tr>
<tr class="even">
<td><p>Exchange HD Photo Get Latency (ms)</p></td>
<td><p>This counter shows the average time (in milliseconds) to retrieve a photo from Exchange</p></td>
</tr>
<tr class="odd">
<td><p>HTTP 4xx Responses/Second</p></td>
<td><p>The per second rate of responses with HTTP 4xx code</p></td>
</tr>
<tr class="even">
<td><p>HTTP 5xx Responses/Second</p></td>
<td><p>The per second rate of responses with HTTP 5xx code</p></td>
</tr>
<tr class="odd">
<td><p>IM MCU Join Failures</p></td>
<td><p>The number of IM MCU Join Failures</p></td>
</tr>
<tr class="even">
<td><p>Number of Active Directory Photo Get Failures</p></td>
<td><p>The total number of failures to retrieve photos from Active Directory</p></td>
</tr>
<tr class="odd">
<td><p>Number of Contact Search failures</p></td>
<td><p>The total number of failures to search contacts in Exchange</p></td>
</tr>
<tr class="even">
<td><p>Number of Deserialization Failures</p></td>
<td><p>The total number of deserialization failures</p></td>
</tr>
<tr class="odd">
<td><p>Number of HD Photo Get Failures</p></td>
<td><p>The total number of failures to retrieve HD photos from Exchange</p></td>
</tr>
<tr class="even">
<td><p>Over The Maximum Subscriptions Per Application</p></td>
<td><p>The number of Subscription requests over the maximum allowed per application</p></td>
</tr>
<tr class="odd">
<td><p>Over The Maximum Subscriptions Per Batch</p></td>
<td><p>The number of Subscription requests over the maximum allowed per batch</p></td>
</tr>
<tr class="even">
<td><p>Presence Subscription Failures</p></td>
<td><p>The number of failures to subscribe presence</p></td>
</tr>
<tr class="odd">
<td><p>Registering Endpoint Failures</p></td>
<td><p>The number of failures to register endpoints</p></td>
</tr>
<tr class="even">
<td><p>Requests Received/Second</p></td>
<td><p>The per second rate of received requests</p></td>
</tr>
<tr class="odd">
<td><p>Requests Succeeded/Second</p></td>
<td><p>The per second rate of successful requests (HTTP 2xx/3xx response codes)</p></td>
</tr>
<tr class="even">
<td><p>Succeeded Create Application Requests/Second</p></td>
<td><p>The per second rate of successful application creation requests</p></td>
</tr>
<tr class="odd">
<td><p>Timed Out Pending Get Count</p></td>
<td><p>The number of pending gets that timed out</p></td>
</tr>
<tr class="even">
<td><p>Total Application Creation Requests Received</p></td>
<td><p>The total number of application creation requests received since the service was started</p></td>
</tr>
<tr class="odd">
<td><p>Total HTTP 4xx Responses</p></td>
<td><p>The total number of HTTP 4xx responses</p></td>
</tr>
<tr class="even">
<td><p>Total HTTP 5xx Responses</p></td>
<td><p>The total number of HTTP 5xx responses</p></td>
</tr>
<tr class="odd">
<td><p>Total Requests Received on the Command Channel</p></td>
<td><p>The total number of requests received on the command channel</p></td>
</tr>
<tr class="even">
<td><p>Total Requests Succeeded</p></td>
<td><p>The total number of requests that succeeded</p></td>
</tr>
<tr class="odd">
<td><p>Total Sessions Initiated</p></td>
<td><p>The total number of sessions that were initiated since the service was started</p></td>
</tr>
<tr class="even">
<td><p>Total Sessions Terminated Because of Idle Timeout</p></td>
<td><p>The total number of sessions that were terminated because of user idle timeout</p></td>
</tr>
<tr class="odd">
<td><p>Total Throttled Applications</p></td>
<td><p>The number of throttled applications</p></td>
</tr>
</tbody>
</table>


</div>

<div id="sectionSection1" class="section">

### Performance Counters for Mcx Mobility Service

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Counter</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Average Lifetime for a Session in Milliseconds</p></td>
<td><p>The average lifetime for a session in milliseconds</p></td>
</tr>
<tr class="even">
<td><p>Current Push Notification Subscriptions</p></td>
<td><p>The current number of push notification subscriptions. This number, in conjunction with Currently Active Session Count, represents the subset of currently active sessions that are registered for Windows Mobile or iPhone devices.</p></td>
</tr>
<tr class="odd">
<td><p>Currently Active Network Timeout Poll Count</p></td>
<td><p>The number of network polls that timed out</p></td>
</tr>
<tr class="even">
<td><p>Currently Active Poll Count</p></td>
<td><p>The number of currently active polls (long-held connections to the server)</p></td>
</tr>
<tr class="odd">
<td><p>Currently Active Session Count</p></td>
<td><p>Current number of endpoints registered in the Mobility Service</p></td>
</tr>
<tr class="even">
<td><p>Currently Active Session Count with Active Presence Subscriptions</p></td>
<td><p>The number of currently active sessions with active presence subscriptions</p></td>
</tr>
<tr class="odd">
<td><p>Push Notification Requests Failed/Second</p></td>
<td><p>The per second rate of failed push notifications</p></td>
</tr>
<tr class="even">
<td><p>Push Notification Requests Succeeded/Second</p></td>
<td><p>The per second rate of successful push notifications</p></td>
</tr>
<tr class="odd">
<td><p>Push Notification Requests Throttled/Second</p></td>
<td><p>The per second rate of throttled push notifications</p></td>
</tr>
<tr class="even">
<td><p>Push Notification Requests/Second</p></td>
<td><p>The per second rate of sent push notifications</p></td>
</tr>
<tr class="odd">
<td><p>Requests Failed/Second</p></td>
<td><p>The per second rate of failed requests</p></td>
</tr>
<tr class="even">
<td><p>Requests Received/Second</p></td>
<td><p>The per second rate of received requests</p></td>
</tr>
<tr class="odd">
<td><p>Requests Rejected/Second</p></td>
<td><p>The per second rate of rejected requests</p></td>
</tr>
<tr class="even">
<td><p>Requests Succeeded/Second</p></td>
<td><p>The per second rate of successful requests</p></td>
</tr>
<tr class="odd">
<td><p>Succeeded Initiate Session Requests/Second</p></td>
<td><p>The per second rate of successful Get Location requests. Requests to initiate a session consume the most CPU on the server. Peak supported load is 12/second. Sustainability depends on other loads on the server. Initiate a session typically means a sign-in for a user that has been signed out for an extended period of time.</p></td>
</tr>
<tr class="even">
<td><p>Total Declined Inbound Voice Calls</p></td>
<td><p>The total number of inbound voice calls that were declined</p></td>
</tr>
<tr class="odd">
<td><p>Total Failed Inbound Voice Calls</p></td>
<td><p>The total number of inbound voice calls that failed</p></td>
</tr>
<tr class="even">
<td><p>Total Failed Outbound Voice Calls</p></td>
<td><p>The total number of outbound voice calls that failed</p></td>
</tr>
<tr class="odd">
<td><p>Total number of sessions terminated by user</p></td>
<td><p>The total number of sessions terminated by users</p></td>
</tr>
<tr class="even">
<td><p>Total Push Notification Requests</p></td>
<td><p>The total number of push notification requests</p></td>
</tr>
<tr class="odd">
<td><p>Total Push Notification Requests Failed</p></td>
<td><p>The total number of push notification requests that failed</p></td>
</tr>
<tr class="even">
<td><p>Total Push Notification Requests Succeeded</p></td>
<td><p>The total number of push notification requests that were successful</p></td>
</tr>
<tr class="odd">
<td><p>Total Push Notification Requests Throttled</p></td>
<td><p>The total number of push notification requests that were throttled</p></td>
</tr>
<tr class="even">
<td><p>Total Requests Failed</p></td>
<td><p>The total number of requests that failed</p></td>
</tr>
<tr class="odd">
<td><p>Total Requests received on the Command Channel</p></td>
<td><p>The total number of requests received on the command channel</p></td>
</tr>
<tr class="even">
<td><p>Total Requests Rejected</p></td>
<td><p>The total number of requests that were rejected</p></td>
</tr>
<tr class="odd">
<td><p>Total Requests Succeeded</p></td>
<td><p>The total number of requests made to the Mobility Service that succeeded</p></td>
</tr>
<tr class="even">
<td><p>Total Session Initiated Count</p></td>
<td><p>The total number of sessions that were initiated since the Mobility Service was started</p></td>
</tr>
<tr class="odd">
<td><p>Total Sessions Terminated Because of User Idle Timeout</p></td>
<td><p>The total number of sessions that were terminated because of user idle timeout</p></td>
</tr>
<tr class="even">
<td><p>Total Successful Inbound Voice Calls</p></td>
<td><p>The total number of inbound voice calls that were successful</p></td>
</tr>
<tr class="odd">
<td><p>Total Successful Outbound Voice Calls</p></td>
<td><p>The total number of outbound voice calls that were successful</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

