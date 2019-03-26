---
title: 'Lync Server 2013: Configuring a watcher node to run synthetic transactions'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configuring a watcher node to run synthetic transactions
ms:assetid: cedda508-8881-4079-88d5-49798f342ddf
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205314(v=OCS.15)
ms:contentKeyID: 48185578
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring a watcher node to run synthetic transactions in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-07_

After the System Center agent files have been installed, you must next configure the watcher node itself. The steps you take to configure a watcher node will vary depending on whether your watcher node computer lies inside your perimeter network or outside your perimeter network.

When you configure a watcher node, you must also choose the type of authentication method to be employed by that node. Lync Server 2013 enables you to choose one of two authentication methods: Trusted Server or Credential Authentication. The differences between these two methods are outlined in the following table:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Configuration</th>
<th>Description</th>
<th>Locations Supported</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Trusted Server</p></td>
<td><p>Uses a certificate to impersonate an internal server and bypass authentication challenges.</p>
<p>This is useful for administrators who would prefer to manage a single certificate instead of many user passwords on each watcher node.</p></td>
<td><p>Inside the enterprise.</p>
<p>Note that, with this method, the watcher node must be in the same domain as the pools being monitored. If the watcher node and the monitored pools are in different domains, use Credential Authentication instead.</p></td>
</tr>
<tr class="even">
<td><p>Credential Authentication</p></td>
<td><p>Stores user names and passwords securely in Windows Credential Manager on each watcher node.</p>
<p>This mode requires more password management, but is the only option for watcher nodes located outside of the enterprise. These watcher nodes cannot be treated as an endpoint trusted for authentication.</p></td>
<td><p>Outside the enterprise.</p>
<p>Inside the enterprise.</p></td>
</tr>
</tbody>
</table>


You should also verify that your firewall has inbound rules for both MonitoringHost.exe and PowerShell.exe. If these processes are blocked by the firewall then your synthetic transactions will fail with a 504 (server timeout) error.

</div>

<span> </span>

</div>

</div>

</div>

