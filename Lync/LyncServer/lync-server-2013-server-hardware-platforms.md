---
title: Lync Server 2013 server hardware platforms
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Server hardware platforms
ms:assetid: c964c1c0-0153-472b-88ad-a38866e0df0c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398835(v=OCS.15)
ms:contentKeyID: 48185395
ms.date: 07/28/2016
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Server hardware platforms for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-07-28_

Lync Server 2013 server roles and computers running Lync Server administrative tools require 64-bit hardware.

The specific hardware used for Lync Server 2013 deployment can vary, depending on size and usage requirements. This section describes the recommended hardware. Although these are recommendations, not requirements, using hardware that does not meet these recommendations may result in significant performance issues and other issues.

<div>

## Recommended Hardware Platform

For best performance, we recommend that you run Lync Server on servers with hardware that meets the requirements in the following table. If you use less powerful hardware, you may experience functionality problems or poor performance. Note that these hardware requirements are higher than those of previous versions of Lync Server, primarily because in Lync Server 2013, all Front End Servers run SQL Server.

<div>


> [!NOTE]  
> NIC teaming is supported and should be transparent to Lync Server. For details, see <A href="http://go.microsoft.com/fwlink/p/?linkid=389910">Communications Server or Lync Server and network adapter teaming</A>.



</div>

### Recommended Hardware for Front End Servers, Back End Servers, Standard Edition Servers, Persistent Chat Servers, and Persistent Chat Store and Persistent Chat Compliance Store (Back End Server Roles for Persistent Chat Server)

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Hardware component</th>
<th>Recommended</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPU</p></td>
<td><p>64-bit dual processor, hex-core, 2.26 gigahertz (GHz) or higher.</p>
<p>Intel Itanium processors are not supported for Lync Server server roles.</p></td>
</tr>
<tr class="even">
<td><p>Memory</p></td>
<td><p>32 gigabytes (GB).</p></td>
</tr>
<tr class="odd">
<td><p>Disk</p></td>
<td><ul>
<li><p>8 or more 10,000 RPM hard disk drives with at least 72 GB free disk space.</p>
<p>Two of the disks should use RAID 1, and six should use RAID 10.</p>
<p>- OR -</p></li>
<li><p>Solid state drives (SSDs) which provide performance similar to 8 10,000-RPM mechanical disk drives.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Network</p></td>
<td><ul>
<li><p>1 dual-port network adapter, 1 Gbps or higher (2 recommended, which requires teaming with a single MAC address and single IP address).</p>
<div>

> [!NOTE]  
> Dual or multi-homed configurations are not supported for Front End Servers, Back End Servers, Standard Edition servers, and Persistent Chat Servers.<BR>ILO/DRAC/etc. connections not exposed to the Operating System and used to monitor and manage the server hardware do not constitute a multi-homed server and thus are supported.


</div></li>
</ul></td>
</tr>
</tbody>
</table>


### Recommended Hardware for Edge Servers, Standalone Mediation Servers, and Directors

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Hardware component</th>
<th>Recommended</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPU</p></td>
<td><ul>
<li><p>64-bit dual processor, quad-core, 2.0 gigahertz (GHz) or higher.</p>
<p>- OR -</p></li>
<li><p>64-bit 4-way processor, dual-core, 2.0 GHz or higher.</p></li>
</ul>
<p>Intel Itanium processors are not supported for Lync Server server roles.</p></td>
</tr>
<tr class="even">
<td><p>Memory</p></td>
<td><p>16 gigabytes (GB).</p></td>
</tr>
<tr class="odd">
<td><p>Disk</p></td>
<td><ul>
<li><p>4 or more 10,000 RPM hard disk drives with at least 72 GB free disk space.</p>
<p>The disks should be in a 2x RAID 1 configuration.</p>
<p>- OR -</p></li>
<li><p>Solid state drives (SSDs) which provide performance similar to 4 10,000-RPM mechanical disk drives.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Network</p></td>
<td><ul>
<li><p>1 dual-port network adapter, 1 Gbps or higher (2 recommended, which requires teaming with a single MAC address and single IP address). 2 network interfaces are required on Edge Servers, and are supported on standalone Mediation Servers.</p></li>
</ul>
<div>

> [!NOTE]  
> Dual or multi-homed configurations are not supported for Directors.<BR>ILO/DRAC/etc. connections not exposed to the Operating System and used to monitor and manage the server hardware do not constitute a multi-homed server and thus are supported.


</div>
<p>Edge Servers will require two network interfaces that are dual-port network adapters, 1 Gbps or higher (or two paired network adapters, for a total of four, each pair being teamed with a single MAC address and a single IP address, for a total of two pairs).</p>
<p>Installation of additional network interface cards (NICs) to allow the configuration of a specific PSTN IP address is supported on standalone Mediation Servers.</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

