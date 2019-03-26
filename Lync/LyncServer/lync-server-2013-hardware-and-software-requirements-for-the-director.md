---
title: 'Lync Server 2013: Hardware and software requirements for the Director'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Hardware and software requirements for the Director
ms:assetid: 747b701e-7f97-46fe-91c5-1e8d9addf9f7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398560(v=OCS.15)
ms:contentKeyID: 48184517
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Hardware and software requirements for the Director in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-20_

This section details the hardware and software requirements for the Director, and the supported collocation scenarios for the Director.

<div>

## Hardware Requirements for the Director

The following table lists the hardware requirements for the Director:

### Hardware Requirements for the Director

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Hardware component</th>
<th>Minimum requirement</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPU</p></td>
<td><ul>
<li><p>64-bit processor, quad-core, 2.0 GHz or higher</p></li>
<li><p>64-bit dual processor, dual-core, 2.0 GHz or higher</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Memory</p></td>
<td><p>4 gigabytes (GB)</p></td>
</tr>
<tr class="odd">
<td><p>Disk</p></td>
<td><ul>
<li><p>10K RPM hard disk drive (HDD)</p></li>
<li><p>High-performance solid state drive (SSD) with performance equal to or better than 10K RPM HDD</p></li>
<li><p>2x RAID 10 (striped and mirrored) 15K RPM disks for database data files</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Network</p></td>
<td><ul>
<li><p>Dual 1 gigabit per second (Gbps) network adapters (recommended)</p></li>
<li><p>Single 1 Gbps network adapter (supported)</p></li>
</ul></td>
</tr>
</tbody>
</table>


</div>

<div>

## Software Requirements for the Director

The Director role can be deployed only on servers running Lync Server 2013 Enterprise Edition.

One of the following 64-bit operating systems is required for the Directors:

  - The Windows Server 2008 R2 Standard operating system with Service Pack 1

  - The Windows Server 2008 R2 Enterprise operating system with Service Pack 1

  - The Windows Server 2008 R2 Datacenter operating system with Service Pack 1

  - The Windows Server 2012 Standard operating system

  - The Windows Server 2012 Datacenter operating system

Lync Server 2013 also requires installation of the following programs and updates detailed in the topic [Additional server support and requirements in Lync Server 2013](lync-server-2013-additional-server-support-and-requirements.md).

</div>

<div>

## Supported Collocation

The Director server role cannot be collocated with any other server role in Lync Server 2013. However, if you do not deploy a Director, the Front End Servers will assume the role.

</div>

</div>

<span> </span>

</div>

</div>

</div>

