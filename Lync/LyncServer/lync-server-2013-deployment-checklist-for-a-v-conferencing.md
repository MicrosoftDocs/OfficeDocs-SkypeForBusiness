---
title: Lync Server 2013 deployment checklist for A/V conferencing
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Deployment checklist for A/V conferencing
ms:assetid: 6d47426f-6559-407b-9ac1-2453f0b7a2a2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ619183(v=OCS.15)
ms:contentKeyID: 49733684
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deployment checklist for A/V conferencing in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-30_

As with deployment of your other Lync Server 2013 components, deployment of A/V conferencing requires that you use Topology Builder to create and publish a topology that incorporates conferencing.

<div>

## Deployment Sequence

You can deploy conferencing at the same time that you deploy your initial topology or after you have deployed at least one Front End pool or Standard Edition server.

</div>

<div>

## Conferencing Deployment Process

The following table provides an overview of the steps required to deploy conferencing into an existing topology.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Phase</th>
<th>Steps</th>
<th>Roles and group memberships</th>
<th>Documentation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Install prerequisite hardware and software</strong></p></td>
<td><p>Conferencing runs on Front End Servers of a Front End pool and Standard Edition servers. It has no additional hardware or software requirements beyond what is required to install those servers.</p>
<div>

> [!NOTE]  
> Lync Server 2013 uses Office Web Apps and the Office Web Apps Server to handle sharing and rendering of PowerPoint presentations. For details about installing and configuring the Office Web Apps Server, see <A href="lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md">Configuring integration with Office Web Apps Server and Lync Server 2013</A>.


</div></td>
<td><p>Domain user who is a member of the local Administrators group</p></td>
<td><p><a href="lync-server-2013-supported-hardware.md">Supported hardware for Lync Server 2013</a> in the Supportability documentation</p>
<p><a href="lync-server-2013-server-software-and-infrastructure-support.md">Server software and infrastructure support in Lync Server 2013</a> in the Supportability documentation</p>
<p><a href="lync-server-2013-determining-your-system-requirements.md">Determining your system requirements for Lync Server 2013</a> in the Planning documentation.</p>
<p><a href="lync-server-2013-technical-requirements-for-archiving.md">Technical requirements for Archiving in Lync Server 2013</a> in the Planning documentation.</p></td>
</tr>
<tr class="even">
<td><p><strong>Create the appropriate internal topology to support conferencing</strong></p></td>
<td><p>Run Topology Builder to add conferencing to the topology, and then publish the topology.</p></td>
<td><p>To define a topology, an account that is a member of the local Users group</p>
<p>To publish the topology, an account that is a member of the Domain Admins group and RTCUniversalServerAdmins group, and that has full control permissions (read/write/modify) on the file share to be used for the Lync Server 2013 file store (so that Topology Builder can configure the required DACLs)</p></td>
<td><p><a href="lync-server-2013-define-and-configure-a-topology-in-topology-builder.md">Define and configure a topology in Topology Builder for Lync Server 2013</a> in the Deployment documentation.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Configure conferencing policies and support</strong></p></td>
<td><p>Use the Lync Server 2013 Control Panel or Lync Server Management Shell to configure conferencing settings.</p></td>
<td><p>RTCUniversalServerAdmins group (Windows PowerShell only) or assign users to the [] or CSAdministrator role</p></td>
<td><p><a href="lync-server-2013-conferencing-policies.md">Conferencing policies in Lync Server 2013</a> in the Operations documentation.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## See Also


[Overview of conferencing in Lync Server 2013](lync-server-2013-overview-of-conferencing.md)  
[Defining your requirements for conferencing in Lync Server 2013](lync-server-2013-defining-your-requirements-for-conferencing.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

