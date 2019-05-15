---
title: 'Lync Server 2013: SQL Server data and log file placement'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: SQL Server data and log file placement
ms:assetid: 67aa525b-8aa3-474f-827e-8e1d4697f30f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398479(v=OCS.15)
ms:contentKeyID: 48184395
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# SQL Server data and log file placement for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

During the planning and deployment of Microsoft SQL Server 2012 or Microsoft SQL Server 2008 R2 SP1 for your Lync Server 2013 Front End pool, an important consideration is the placement of data and log files onto physical hard disks for performance. The recommended disk configuration is to implement a 1+0 RAID set using 6 spindles. Placing all database and log files that are used by the Front End pool and associated server roles and services (that is, Archiving and Monitoring Server, Lync Server Response Group service, Lync Server Call Park service) onto the RAID drive set using the Lync Server Deployment Wizard will result in a configuration that has been tested for good performance. The database files and what they are responsible for is detailed in the following table.

<div>


> [!NOTE]  
> If your policies and SQL Server configurations require a more specialized installation, the database and log files can be installed to any pre-defined location using the Lync Server Management Shell. See <A href="lync-server-2013-database-installation-using-lync-server-management-shell.md">Database installation using Lync Server Management Shell in Lync Server 2013</A> for more details.



</div>

### Data and Log Files for Central Management Store

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Central Management store database files</th>
<th>Data file or log purpose</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Xds.ldf</p></td>
<td><p>Transaction log file for the Central Management store</p></td>
</tr>
<tr class="even">
<td><p>Xds.mdf</p></td>
<td><p>Maintains the configuration of the current Lync Server 2013 topology, as defined and published by Topology Builder</p></td>
</tr>
<tr class="odd">
<td><p>Lis.mdf</p></td>
<td><p>Location Information service data file</p></td>
</tr>
<tr class="even">
<td><p>Lis.ldf</p></td>
<td><p>Transaction log for the Location Information service data file</p></td>
</tr>
</tbody>
</table>


### Data and Log files for User, Conferencing, and Address Book

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Core Lync Server 2013 database files</th>
<th>Data file or log purpose</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Rtc.mdf</p></td>
<td><p>Persistent user data (for example, access control lists (ACLs), contacts, scheduled conferences)</p></td>
</tr>
<tr class="even">
<td><p>Rtc.ldf</p></td>
<td><p>Transaction log for Rtc data</p></td>
</tr>
<tr class="odd">
<td><p>Rtcdyn.mdf</p></td>
<td><p>Maintains transient user data (presence runtime data)</p></td>
</tr>
<tr class="even">
<td><p>Rtcdyn.ldf</p></td>
<td><p>Transaction log for Rtcdyn data</p></td>
</tr>
<tr class="odd">
<td><p>Rtcab.mdf</p></td>
<td><p>Real-time communications (RTC) address book database is the SQL Server repository where Address Book service information is stored</p></td>
</tr>
<tr class="even">
<td><p>Rtcab.ldf</p></td>
<td><p>Transaction log for Address Book Service</p></td>
</tr>
<tr class="odd">
<td><p>Rtclocal.mdb</p></td>
<td><p>Hosts the conference directory</p></td>
</tr>
<tr class="even">
<td><p>Rtcxds.mdf</p></td>
<td><p>Maintains the backup for user data</p></td>
</tr>
<tr class="odd">
<td><p>Rtcxds.ldf</p></td>
<td><p>Transaction log for Rtcxds data</p></td>
</tr>
</tbody>
</table>


### Data and Log Files for Call Park and Response Group

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Application database</th>
<th>Data file or log purpose</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Cpsdyn.mdf</p></td>
<td><p>Dynamic information database for the Call Park application</p></td>
</tr>
<tr class="even">
<td><p>Cpsdyn.ldf</p></td>
<td><p>Transaction log for Call Park application data file</p></td>
</tr>
<tr class="odd">
<td><p>Rgsconfig.mdf</p></td>
<td><p>Lync Server Response Group service data file for the configuration of the services</p></td>
</tr>
<tr class="even">
<td><p>Rgsconfig.ldf</p></td>
<td><p>Transaction log file for the Response Group application configuration</p></td>
</tr>
<tr class="odd">
<td><p>Rgsdyn.mdf</p></td>
<td><p>Response Group service data file for runtime operations</p></td>
</tr>
<tr class="even">
<td><p>Rgsdyn.ldf</p></td>
<td><p>Transaction log for the Response Group service runtime data file</p></td>
</tr>
</tbody>
</table>


### Data and Log Files for Archiving and Monitoring Server

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Archiving and Monitoring database files</th>
<th>Data file or log purpose</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>LcsCdr.mdf</p></td>
<td><p>Data store for the call detail recording (CDR) process of the Monitoring Server</p></td>
</tr>
<tr class="even">
<td><p>LcsCdr.ldf</p></td>
<td><p>Transaction log for call detail recording (CDR) data</p></td>
</tr>
<tr class="odd">
<td><p>QoEMetrics.mdf</p></td>
<td><p>Quality of Experience data file stored from the Monitoring Server</p></td>
</tr>
<tr class="even">
<td><p>QoEMetrics.ldf</p></td>
<td><p>Transaction log for Monitoring data</p></td>
</tr>
<tr class="odd">
<td><p>Lcslog.mdf</p></td>
<td><p>Data file for the retention of instant messaging and conferencing data on an Archiving Server</p></td>
</tr>
<tr class="even">
<td><p>Lcslog.ldf</p></td>
<td><p>Transaction log for Archiving data</p></td>
</tr>
</tbody>
</table>


In this topic, references are made to disk and to RAID set. Note that in the configuration of SQL Server resources, referring to a disk means a single hardware device. A hard disk drive with two partitions, one holding log files and the other partition holding data files, is not the same as two disks, each dedicated to either log or data files.

In reference to RAID sets, there are a number of different RAID technologies from various vendors. And, with the proliferation of storage area networks (SAN), RAID sets dedicated to a single system are rarer. You should consult with your RAID or SAN vendor to determine what the best configuration is for your disk layout when configuring for SQL Server performance with Lync Server 2013.

Note also that not all disk drives are created equally; some perform better than others. Even drives from the same manufacturer can vary in performance because of rotational speed, hardware cache size, and other factors.

</div>

<span> </span>

</div>

</div>

</div>

