---
title: 'Lync Server 2013: Poster: Key Health Indicators'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: 'Poster: Key Health Indicators'
ms:assetid: 8367dccf-adaa-4a0b-a4ed-bc9570cc5e24
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn593599(v=OCS.15)
ms:contentKeyID: 61084873
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Key Health Indicators in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-10_

This article is a companion to the [Key Health Indicators: The Foundation for Maintaining Healthy Lync Servers](http://go.microsoft.com/fwlink/?linkid=391838) poster, which you can download from the Download Center.

![Poster describing troubleshooting using KHI data](images/Dn594589.b6fe82bd-d70f-4c1f-a812-b615ac5fa7d7(OCS.15).jpg "Poster describing troubleshooting using KHI data")

You can use this poster to learn about Key Health Indicators (KHIs), performance counters with thresholds aimed at revealing user experience issues. Gathering KHI data is usually the first step to implementing the Call Quality Methodology (CQM), which is focused on ensuring a quality audio experience for Lync users.

If you have questions about how to use CQM, you can submit your questions to cqmfeedback@microsoft.com.

The poster explains the following areas:

  - What are Key Health Indicators?

  - To Collect KHI Data

  - Remediation Flow for all Server Roles

  - Glossary

  - Front-end Servers

  - Backend SQL Servers

  - Mediation Servers

  - Edge Servers

<span id="WhatIs"></span>

<div>

## What are Key Health Indicators?

Key Health Indicators are performance counters with thresholds aimed at revealing user experience issues. Gathering KHI data is usually the first step to implementing the Call Quality Methodology (CQM), which is focused on ensuring a quality audio experience for Lync users.

KHIs are used in addition to standard Lync Monitoring Solutions (e.g. System Center Operations Manager, Synthetic Transactions, Monitoring Server) and not instead of those solutions.

Collect the KHI performance counters and populate the KHI spreadsheet accompanying the Networking Guide to produce a scorecard that will help you determine the server health of a Lync deployment. Once populated, it guides you in repairing the environment and gives additional insight to other stakeholders. Evaluate KHIs on a monthly basis and incorporate them into any deployment’s ongoing operational processes.

Download the [Lync Server Networking Guide](http://go.microsoft.com/fwlink/p/?linkid=390677) to see the full list of KHIs and to get the related spreadsheets.

</div>

<span id="ToCollect"></span>

<div>

## To Collect KHI Data

1.  Run the KHI script included with the Lync Server Networking Guide on each Lync Server. This will create a Data Collector inside of Performance Monitor and name it KHI. By default, data will be polled every 15 seconds.

2.  Before the start of your company's business day, go to each Lync Server and start the KHI Data Collector.

3.  At the end of that day, stop the KHI Data Collector and copy the data to a central location.

4.  After using Performance Monitor to fill in the KHI spreadsheet included with the Lync Server Networking Guide download, compare the results to the recommended targets.

</div>

<span id="Remidiation"></span>

<div>

## Remediation Flow for all Server Roles

For each server in your Lync implementation, begin by verifying that the server’s component health and system performance is at or above the desired level. Only after that should you look at the indicators relating to the server’s role in the overall Lync implementation.

Begin by collecting KHI  Performance Data for all servers. For each of the system roles (details discussed later in this document) determine whether the basic system components meet the recommended targets. If they do not, remediate the system performance then re-collect KHI data and ensure system health before looking at the metrics specific to the server’s role in the Lync implementation. Component health for all roles is defined as:

  - CPU Utilization \< 80%

  - Avg. Disk Write \< 10 ms

  - Avg. Disk Read \< 10 ms

  - Available memory  \>20% System Total MB

  - Network Queue Length \< 2

  - Discarded Packets (in / out) = 0

</div>

<span id="Glossary"></span>

<div>

## Glossary

The following terms and acronyms are used in this poster:

AS MCU = Application Sharing Multi-point Control Unit

AV MCU = Audio/Video MCU

IM MCU = Instant Messaging MCU

UCWA = Unified Communications Web API

AV Edge = Traversal of audio/video via edge

AV Auth = Audio/Video Authentication

SIP Stack = Contains Lync’s core SIP implementation

Data Proxy = Used for edge conferencing

LySS = Lync Storage Service

</div>

<span id="Front"></span>

<div>

## Front-end Servers

The following recommended KHI targets are specific to front-end servers in addition to basic component health:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Functional area</th>
<th>Target Metrics</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AS/AV/IM MCU</p></td>
<td><p>MCU Health State &lt;2</p></td>
</tr>
<tr class="even">
<td><p>Web Components</p></td>
<td><p>Distribution List expansion AD timeouts &lt;0</p>
<p>ABWQ failures = 0</p>
<p>LIS failures = 0</p>
<p>Authentication Errors &lt; 1/sec</p>
<p>ASP.NET v4 Requests Rejected = 0</p></td>
</tr>
<tr class="odd">
<td><p>SIP Stack</p></td>
<td><p>Avg. Incoming Message Processing &lt; 1 sec</p>
<p>Incoming Responses Dropped &lt; 1/sec Incoming Requests Dropped &lt; 1/sec</p>
<p>Queue Latency &lt; 100 ms</p>
<p>Sproc Latency &lt; 100 ms</p>
<p>Throttled Requests = 0</p>
<p>Authentication Errors &lt; 1/sec</p>
<p>Incoming Messages Timed Out &lt; 2</p>
<p>Avg. Incoming Message Hold &lt; 1 sec</p>
<p>Flow Controlled Connections &lt; 2</p>
<p>Avg. Out Queue Delay &lt; 2 sec</p></td>
</tr>
<tr class="even">
<td><p>LySS</p></td>
<td><p>% of space used by Storage Service DB &lt; 80</p>
<p># of replica replication failures = 0</p>
<p># of data loss events = 0</p></td>
</tr>
<tr class="odd">
<td><p>SQL</p></td>
<td><p>Page life expectancy &gt; 300 Sec.</p>
<p>Batch requests / sec &lt; 2500</p></td>
</tr>
</tbody>
</table>


</div>

<span id="BackEnd"></span>

<div>

## Backend SQL Servers

The following recommended KHI targets are specific to SQL servers in addition to basic component health:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Functional area</th>
<th>Target Metrics</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>SQL</p></td>
<td><p>Page life expectancy &gt; 300 Sec.</p>
<p>Batch requests / sec &lt; 2500</p></td>
</tr>
</tbody>
</table>


</div>

<span id="Mediation"></span>

<div>

## Mediation Servers

The following recommended KHI targets are specific to mediation servers in addition to basic component health:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Functional area</th>
<th>Target Metrics</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Mediation Server Service</p></td>
<td><p>Load Call Failure Index = 0</p>
<p>Failed Calls due to Proxy &lt;10</p>
<p>Failed Calls due to Gateway &lt;10</p>
<p>Calls (in or out) rejected = 0</p>
<p>Media Candidates missing = 0</p>
<p>Media Connectivity Check Failures = 0</p></td>
</tr>
</tbody>
</table>


</div>

<span id="Edge"></span>

<div>

## Edge Servers

The following recommended KHI targets are specific to edge servers in addition to basic component health:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Functional area</th>
<th>Target Metrics</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AV Auth</p></td>
<td><p>Bad Requests &lt; 20/sec</p></td>
</tr>
<tr class="even">
<td><p>AV Edge</p></td>
<td><p>Auth. Failures &lt;20/sec</p>
<p>Allocation Failures &lt;20/sec</p>
<p>Packets Dropped &lt;300/sec</p></td>
</tr>
<tr class="odd">
<td><p>Data Proxy</p></td>
<td><p>Throttled Server connections &lt; 3</p>
<p>System is Throttling &lt;1</p></td>
</tr>
<tr class="even">
<td><p>SIP Stack</p></td>
<td><p>Connections over limit dropped &lt; 1</p>
<p>Sends timed out &lt;10</p>
<p>Flow Controlled Connections &lt;100</p>
<p>Incoming requests dropped &lt; 1/sec</p>
<p>Avg. Message Processing &lt; 3 sec</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## See Also


[Lync Server Networking Guide](http://go.microsoft.com/fwlink/p/?linkid=390677)  
[Key Health Indicators: The Foundation for Maintaining Healthy Lync Servers](http://go.microsoft.com/fwlink/?linkid=391838)  
[Lync Call Quality Methodology](http://go.microsoft.com/fwlink/?linkid=391841)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

