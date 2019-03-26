---
title: 'Lync Server 2013: Deployment checklist for monitoring'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Deployment checklist for monitoring
ms:assetid: 4e798370-277c-4391-84b4-13a972b45ca6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204874(v=OCS.15)
ms:contentKeyID: 48184080
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deployment checklist for monitoring in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-05_

Although monitoring is already installed and activated on each Front End server, there are still several steps that you must undertake before you can actually being to collect monitoring data for Microsoft Lync Server 2013. These steps are outlined in the following checklist:


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Phase</p></td>
<td><p>Steps</p></td>
<td><p>Role and group membership</p></td>
<td><p>Documentation</p></td>
</tr>
<tr class="even">
<td><p><strong>Install prerequisite hardware and software</strong></p></td>
<td><p>Install a supported version of Microsoft SQL Server on the computer that will act as the backend data store for monitoring.</p></td>
<td><p>Domain user who is also a member of the local administrators group.</p></td>
<td><p><a href="lync-server-2013-supported-hardware.md">Supported hardware for Lync Server 2013</a> in the Supportability guide</p>
<p><a href="lync-server-2013-server-software-and-infrastructure-support.md">Server software and infrastructure support in Lync Server 2013</a> in the Supportability Guide</p></td>
</tr>
<tr class="odd">
<td><p><strong>Create the appropriate internal topology to support monitoring</strong></p></td>
<td><p>Use Lync Server 2013 Topology Builder to add monitoring databases to the topology, then published the updated topology.</p></td>
<td><p>To define a topology, a user who is a member of the local users group.</p>
<p>To publish the topology, a user who is a member if the domain administrators group and the RTCUniversalServerAdmins group.</p></td>
<td><p><a href="lync-server-2013-associating-a-monitoring-store-with-a-front-end-pool.md">Associating a monitoring store with a Front End pool in Lync Server 2013</a> in the Deployment guide</p></td>
</tr>
<tr class="even">
<td><p><strong>Enable the appropriate monitoring settings</strong></p></td>
<td><p>Enable call detail recording (CDR) and/or Quality of Experience (QoE) monitoring at the global and/or the site scopes.</p></td>
<td><p>A user who is a member of the RTCUniversalServerAdmins group or who has been assigned an RBAC role that provides access to the CsCdrConfiguration and CsQoEConfiguration cmdlets.</p></td>
<td><p><a href="lync-server-2013-configuring-call-detail-recording-and-quality-of-experience-settings.md">Configuring call detail recording and Quality of Experience settings in Lync Server 2013</a> in the Operations guide</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

