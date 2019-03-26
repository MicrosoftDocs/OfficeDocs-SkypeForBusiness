---
title: 'Lync Server 2013: Monitoring back end Lync Server storage performance'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Monitoring back end Lync Server 2013 storage performance
ms:assetid: 71627c70-1953-4ac2-afbe-f3ad85be0f44
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn720917(v=OCS.15)
ms:contentKeyID: 63969619
ms.date: 01/27/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Monitoring back end Lync Server 2013 storage performance

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-05-02_

The Lync Server 2013 back-end databases are a very important part of the Lync Server 2013 deployment. We recommend constantly monitoring the databases and respective transaction logs to help to make sure that the Lync Server 2013 back end is performing optimally.

The following table identifies performance counters that should be monitored to learn information about Storage Performance. The baseline values for these counters must be determined first (when system is at its normal, expected load) to understand the performance changes when system is stressed.

### Performance counters to be monitored

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Performance Counter</th>
<th>Baseline thresholds</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Transactions/sec (RTC)</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Transactions/sec (rtcdyn)</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Transactions/sec (tempdb)</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Log Flushes/sec (RTC)</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Log Flushes/sec (rtcdyn)</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Log Flushes/sec (tempdb)</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Disk Transfers/sec (read+write) - RTC db</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Disk Transfers/sec - RTC log</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Disk Transfers/sec - rtcdyn db</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Disk Transfers/sec - rtcdyn log</p></td>
<td></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

