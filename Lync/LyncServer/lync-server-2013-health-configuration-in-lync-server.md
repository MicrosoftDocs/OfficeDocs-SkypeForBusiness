---
title: 'Lync Server 2013: Health configuration in Lync Server'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Health configuration in Lync Server 2013
ms:assetid: c00a8c8e-c2d2-4557-8c42-211c7cc96550
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205234(v=OCS.15)
ms:contentKeyID: 48185305
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Health configuration in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-22_

Between various websites, Microsoft Knowledge Base articles, and Lync Server Resource Kit tools, administrators who encounter problems when running Lync Server are never far from a way to solve those problems.

Obviously there is no way to guarantee that you will never encounter problems with Lync Server 2013 because Lync Server can be affected by many things—like network crashes and hardware failures—that the product itself cannot control. By implementing health monitoring, administrators can identify potential problems before they turn into actual problems. For example, administrators can use Lync Server monitoring to identify trends and tendencies. For example, a steady increase in the number of audio/video conferences might suggest a need to add capacity before the system becomes overloaded.

In a similar fashion, administrators can use System Center Operations Manager to do such things as issue real-time alerts when specified events occur, and to run synthetic transactions that proactively test the system. Synthetic transactions are used in Lync Server to verify that users are able to successfully complete common tasks such as logging on to the system, exchanging instant messages, or making calls to a phone located on the public switched telephone network (PSTN). For example, periodically running these tests can alert you to potential problems with users logging on to Lync Server, and give you a chance to correct the problem before your support team is flooded with calls from users unable to make a connection. By using System Center Operations Manager to run these synthetic transactions, administrators can routinely monitor their deployment of Lync Server continuously for 24 hours every day without having to do much of anything beyond responding to any alerts that might be issued.

<div>


> [!NOTE]  
> For Lync Server 2013, the Management Pack for System Center Operations Manager is also able to detect "external" issues that can adversely affect Lync Server. For example, administrators can be notified if Internet Information Services (IIS) goes offline, system resources on a Lync Server computer fall below a specified amount, or a Lync Server computer experiences a hardware failure.



</div>

Health configuration in Lync Server 2013 is built around System Center Operations Manager and the use of Lync Server Management Packs. These Management Packs include a number of new features and enhancements, including:

  - **Scenario availability from any location.** The Lync Server 2010 Management Pack introduced the concept of monitoring end user scenario availability with synthetic transactions. In Lync Server 2013, these agents have more synthetic transactions and can be run from a variety of locations inside the enterprise, from remote geographic locations outside of the enterprise, against branch office appliances and against Lync Server 2010 deployments to add coverage to legacy Edge deployments.

  - **Synthetic transaction logs.** When a synthetic transaction fails, administrators have access to HTML logs to help determine what failed. This includes understanding which action failed, the latency of each action, the command-line used to run the test, and the error that was encountered.

  - **Increased call reliability coverage.** The Lync Server 2010 Management Pack introduced call reliability alerting to detect severe connectivity issues that affect the audio calls of end users. The Lync Server 2013 Management Packs add coverage for peer-to-peer instant messaging (IM) and other basic conferencing features to maximize coverage while reducing noise.

  - **Dependency monitoring.** Lync Server scenarios can fail due to a variety of external factors such as IIS being offline, limited CPU and memory resources, and disk issues. The new management packs check several critical dependencies to ensure administrators are aware of their impact.

  - **Enhanced reporting.** A set of reports to help administrators estimate scenario availability, plan for capacity, and see which components are experiencing the most issues.

The Management Packs also include a variety of features to help detect and diagnose provide real-time visibility into the health your Lync Server deployment. These features are listed in the following table.

### Management Pack Features

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Synthetic Transactions</p></td>
<td><p>Windows PowerShell cmdlets that can be run from various locations to ensure that end user scenarios such as sign-in, presence, IM, and conferencing are readily available to end users.</p></td>
</tr>
<tr class="even">
<td><p>Call Reliability Alerts</p></td>
<td><p>Database queries for Call Detail Records (CDR). These records are written by Front End Servers to reflect whether end users were able to connect to a call or why a call was terminated. These queries result in alerts that indicate when a wide range of end users are experiencing connectivity issues for peer-to-peer calls or basic conferencing functionality.</p></td>
</tr>
<tr class="odd">
<td><p>Media Quality Alerts</p></td>
<td><p>Database queries that look at Quality of Experience (QoE) reports published by clients at the end of each call. These queries result in alerts that pinpoint scenarios where users are likely to be experiencing poor media quality during calls and conferences. The data is built upon key metrics such as packet latency and loss, metrics that are known to directly contribute to call quality.</p></td>
</tr>
<tr class="even">
<td><p>Component Health</p></td>
<td><p>Individual server components raise alerts by using event logs and performance counters. These alerts indicate failure conditions that can severely impact one or more end user scenarios. These alerts can also indicate a variety of other failure conditions, including services not running, high failure rates, high message latency, or connectivity issues.</p></td>
</tr>
<tr class="odd">
<td><p>Dependency Health</p></td>
<td><p>Failures can occur for a variety of external reasons. The management packs now monitor and collect data for some of the critical external dependencies that might indicate severe issues, including IIS availability, CPU and memory usage of servers and processes, and disk metrics.</p></td>
</tr>
</tbody>
</table>


The alerts issued by the system have been classified into three general categories:

  - **High-priority Alerts.** These alerts indicate conditions that will cause service outages for large groups of users. For example, a component failure on a single machine is not a high-priority alert because Lync Server 2013 has built-in high availability features. Instead, high-priority alerts represent problems serious enough “to wake up administrators at night.” Outages detected by synthetic transactions and offline services (for example, audio/video conferencing) qualify as high-priority alerts.

  - **Medium-priority alerts.**. These alerts indicate conditions that affect a subset of users or indicate call quality degradation. That includes problems such as component failures, latency in call establishment, or degraded audio quality in call. Alerts in this category are stateful and indicate the current status of the issue. For example, suppose your call establishment times exceed the alert threshold. If call establishment times return to normal, these alerts will be auto-resolved in System Center Operations Manager. The expectation for these alerts is that an administrator will look at them on the same business day.

  - **Other alerts.** These are alerts from components that might affect a specific user or subset of users. For example, perhaps the Address Book service could not parse the Active Directory entry of a given user. The expectation for these alerts is that administrators will get to them when they have time available.

<div>

## In This Section

  - [Configuring Lync Server 2013 to work with System Center Operations Manager](lync-server-2013-configuring-lync-server-to-work-with-system-center-operations-manager.md)

  - [Using rich logging for synthetic transactions in Lync Server 2013](lync-server-2013-using-rich-logging-for-synthetic-transactions.md)

  - [Using Microsoft SQL Server 2008 R2 as your System Center Operations Manager database for Lync Server 2013](lync-server-2013-using-microsoft-sql-server-2008-r2-as-your-system-center-operations-manager-database.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

