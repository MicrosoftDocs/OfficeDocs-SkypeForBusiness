---
title: 'Lync Server 2013: Operational dependencies'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Operational dependencies
ms:assetid: 450b6be2-7fb3-47d7-8b0b-c05faa331e14
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn720559(v=OCS.15)
ms:contentKeyID: 63969597
ms.date: 05/16/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Operational dependencies in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-05-15_

The Reference Architecture discussed in this document will help ensure that you have a Lync Server 2013 deployment that not only scales to the organization’s requirements but is architected as per Microsoft best practices. Be that as it may the Lync Server 2013 implementation is a dynamic service and like any other service in the enterprise still requires monitoring and proactive management to maintain high level of service availability and service quality to the business.

As Lync Server 2013 becomes deeply ingrained in the organization’s everyday business it is important that the service be managed by accurate and tangible service level management. The Lync system architecture can become complex and very integrated and in order to maintain effective service level management and establish SLAs for Lync Server 2013 it becomes critical to understand the system’s dependencies on other platforms and servers. Equally important is to note which business services, such as voice and UC integrated applications, become dependent on Lync.

Lync Server 2013 must be established noting all the said dependencies. The service map will allow you to formulate a SLA between Lync and its dependent service and provide a starting place for SLA negotiation.

The following table lists the typical dependency services for a Lync infrastructure. Each of these technologies should have its own proactive monitoring.

### Typical dependency services

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Dependency Service</th>
<th></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Operating systems</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Server Hardware</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Active Directory</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Public Key Infrastructure</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Domain Naming Service</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Database Services</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Storage Services</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>System Management – Monitoring and distribution</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Security Services - Antivirus</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Network Infrastructure - Internet</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Network Infrastructure – Internal (LAN/WAN)</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Telephony Infrastructure – IP-PBX and Gateways</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Cloud Services</p></td>
<td></td>
</tr>
</tbody>
</table>


It is assumed that the organization is operationally mature in exercising basic service level management functions such as change, incident and release management as prescribed by the MOF. The Lync solution should be adopted by these functions and become subject to the same operational management processes.

Building on the information obtained above we now have a greater understanding of what can impact the Lync service in the enterprise. To help ensure Lync Server 2013 service availability and quality, the following monitoring tools must accompany the reference architecture deployment:

### Monitoring tools

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Component</th>
<th>Description</th>
<th>Applicable Site</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync Server 2013 Monitoring Server</p></td>
<td><p>Deploy at least one Lync Server 2013 Monitoring Server role per Central site and configure Quality of Experience (QoE) Reporting Pack.</p>
<p>Refer to the Lync Server 2013 Deployment documentation for further details:</p>
<p><a href="lync-server-2013-deploying-monitoring.md">Deploying monitoring in Lync Server 2013</a></p></td>
<td><p>Central sites</p></td>
</tr>
<tr class="even">
<td></td>
<td><p>Tether each pool to its nearest instance of the Monitoring Server role.</p></td>
<td><p>Central sites</p>
<p>Branch sites</p></td>
</tr>
<tr class="odd">
<td><p>System Center Operations Manager 2012</p></td>
<td><p>System Center Operations Manager 2012 with the Microsoft Lync Server 2013 Management Pack (MP) imported.</p>
<p>The Management Pack implements traditional Event Log and Performance counter based instrumentation is utilized as well as enabling newly available instrumentation in Lync Server 2013.</p></td>
<td><p>Central sites</p></td>
</tr>
<tr class="even">
<td></td>
<td><p>Make sure that Central Discovery to discovery of roles and components that need to be monitored are automatically completed based on a central discovery script that reads the topology document published in Central Management Database.</p></td>
<td><p>Central Site</p>
<p>Branch Site</p>
<p>Edge Site</p></td>
</tr>
<tr class="odd">
<td></td>
<td><p>Deploy System Centre Operations Manager 2007 agents to all deployed servers running Lync Server.</p></td>
<td><p>Central Site</p>
<p>Branch Site</p>
<p>Edge Site</p></td>
</tr>
<tr class="even">
<td></td>
<td><p>Make sure Prioritized Alerts are configured for notification:</p>
<p>High Priority Alerts</p>
<p>Medium Priority Alerts</p>
<p>Other Alerts.</p></td>
<td><p>Central Site</p>
<p>Branch Site</p>
<p>Edge Site</p></td>
</tr>
<tr class="odd">
<td></td>
<td><p>Configure Port monitoring for your deployment.</p></td>
<td><p>Central Site</p>
<p>Branch Site</p>
<p>Edge Site</p></td>
</tr>
<tr class="even">
<td></td>
<td><p>Configure URL monitoring for your deployment</p></td>
<td><p>Central Site</p></td>
</tr>
<tr class="odd">
<td><p>Lync and System Center Operations Manager integration</p></td>
<td><p>Deploy Call Reliability and Media Quality MonitoringCall reliability and media quality monitoring use the Monitoring Server computer as their watcher node to monitor call reliability and media quality of Lync Server. Both of these features query the Monitoring Server databases to do analysis.</p></td>
<td><p>Central Site</p>
<p>Branch Site</p></td>
</tr>
<tr class="even">
<td></td>
<td><p>Ensure Media Quality warning thresholds are accurately configured. The following table indicates the maximum Network Mean Opinion Scores by Codec. In production these scores should be monitored for a set period and acceptable thresholds must be established based on the organization specific NMOS scores.</p></td>
<td><p>Central Site</p>
<p>Branch Site</p></td>
</tr>
<tr class="odd">
<td><p>Lync Server 2013 Synthetic Transaction Watcher</p></td>
<td><p>Deploy a dedicated Lync Server to be a synthetic transaction watcher.</p>
<p>Synthetic transactions are Lync Server 2013 Windows PowerShell cmdlets that are automatically triggered by the management pack on a predefined interval. These are executed on a synthetic transaction watcher node which is an administrator designated server responsible for discovery and execution of STs for each pool.</p>
<p>We do not recommend that you use an existing Microsoft Lync Server 2013 server as a synthetic transaction watcher node. This is due to the high CPU/memory usage requirements for running STs. Use a new server computer (or a virtual server) for the synthetic transaction watcher node.</p></td>
<td><p>Central Site</p></td>
</tr>
<tr class="even">
<td></td>
<td><p>Deploying synthetic transactions watcher node.</p>
<p>Refer to the MonitoringCS_withSCOM.docx document from UCTAP connect documentation.</p></td>
<td><p>Central Site</p></td>
</tr>
</tbody>
</table>


### Maximum Network MOS scores per codec

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Scenario</th>
<th>Codec</th>
<th>Max NMOS</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>UC-UC call</p></td>
<td><p>RTAudio WB</p></td>
<td><p>4.10</p></td>
</tr>
<tr class="even">
<td><p>UC-UC call</p></td>
<td><p>RTAudio NB</p></td>
<td><p>2.95</p></td>
</tr>
<tr class="odd">
<td><p>Conference call</p></td>
<td><p>Siren</p></td>
<td><p>3.72</p></td>
</tr>
<tr class="even">
<td><p>UC-PSTN call</p></td>
<td><p>RTAudio NB</p></td>
<td><p>2.95</p></td>
</tr>
<tr class="odd">
<td><p>UC-PSTN call</p></td>
<td><p>G-711</p></td>
<td><p>3.61</p></td>
</tr>
</tbody>
</table>


Over and above the previous pro-active monitoring activities, maintenance tasks should be executed for Central, Edge and Branch sites on a recurring daily, weekly and monthly basis as defined in the Lync RA Operations Guide.

</div>

<span> </span>

</div>

</div>

</div>

