---
title: 'Lync Server 2013: Understanding firewall requirements for SQL Server'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Understanding firewall requirements for SQL Server
ms:assetid: 31d7df2c-589f-465e-be74-cf6767db190d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425818(v=OCS.15)
ms:contentKeyID: 48183781
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Understanding firewall requirements for SQL Server with Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

For a Standard Edition deployment, firewall exceptions are created automatically during Lync Server 2013 Setup. However, for Enterprise Edition deployments, you must configure the firewall exceptions manually on the SQL Server Back End Server. The TCP/IP protocol allows for a given port to be used once for a given IP address. This means that for the SQL Server-based server you can assign the default database instance the default TCP port 1433. For any other instances you will need to use the SQL Server Configuration Manager to assign unique and unused ports. This topic covers:

  - Requirements for a firewall exception when using the default instance

  - Requirements for a firewall exception for the SQL Server Browser service

  - Requirements for static listening ports when using named instances

<div>

## Requirements for a Firewall Exception When Using the Default Instance

If you are using the SQL Server default instance for any database when deploying Lync Server 2013, the following firewall rule requirements are used to help ensure communication from the Front End pool to the SQL Server default instance.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Protocol</th>
<th>Port</th>
<th>Direction</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>TCP</p></td>
<td><p>1433</p></td>
<td><p>Inbound to SQL Server</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Requirements for a Firewall Exception for the SQL Server Browser Service

The SQL Server Browser service will locate database instances and communicate the port that the instance (named or default) is configured to use.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Protocol</th>
<th>Port</th>
<th>Direction</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>UDP</p></td>
<td><p>1434</p></td>
<td><p>Inbound</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Requirements for Static Listening Ports When Using Named Instances

When using named instances in the SQL Server configuration for databases supporting Lync Server 2013, you configure static ports by using SQL Server Configuration Manager. After the static ports have been assigned to each named instance, you create exceptions for each static port in the firewall.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Protocol</th>
<th>Port</th>
<th>Direction</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>TCP</p></td>
<td><p>Statically defined</p></td>
<td><p>Inbound</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## SQL Server Documentation

Microsoft SQL Server 2012 documentation provides detailed guidance on how to configure firewall access for databases. For details about Microsoft SQL Server 2012, see “Configuring the Windows Firewall to Allow SQL Server Access” at [http://go.microsoft.com/fwlink/p/?linkId=218031](http://go.microsoft.com/fwlink/p/?linkid=218031).

</div>

</div>

<span> </span>

</div>

</div>

</div>

