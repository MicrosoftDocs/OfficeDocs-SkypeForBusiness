---
title: Lync Server 2013 response group experience during pool failure
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Response group experience during pool failure
ms:assetid: 4e00fb38-64b1-4fd9-903d-7639177bc303
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204886(v=OCS.15)
ms:contentKeyID: 48184116
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Response group experience in Lync Server 2013 during pool failure

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-30_

This section describes in detail how response group activity is affected in the following stages:

  - An outage occurs in the primary pool, but failover is not yet initiated.

  - Service is failed over to the backup pool.

  - Service is failed back to the primary pool.

<div>

## User Experience When Outage Occurs

When a pool or site outage occurs, but the administrator has not yet initiated failover, response group activity is handled as described in the following table.

<div>


> [!NOTE]  
> During disaster recovery, calls behave differently depending on whether the primary pool response groups were imported to the backup pool during recovery. In the following table, references to imported response groups mean that primary pool response groups were imported to the backup pool during disaster recovery mode.



</div>

### Outage Occurs

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Type of call or user action</th>
<th>During outage</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Calls connected to an agent</p></td>
<td><ul>
<li><p>Regular calls remain connected.</p></li>
<li><p>Anonymous calls are disconnected.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>In progress calls not yet connected to an agent</p></td>
<td><p>Calls are disconnected.</p></td>
</tr>
<tr class="odd">
<td><p>New calls</p></td>
<td><ul>
<li><p>Calls are disconnected.</p></li>
<li><p>If response groups were imported, calls connect to backup pool, but agents homed in primary pool are unreachable.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Agent calls on behalf of response group</p></td>
<td><p>Feature is disabled during this stage.</p></td>
</tr>
<tr class="odd">
<td><p>Agent sign-in and agent information</p></td>
<td><ul>
<li><p>Agent groups owned by the primary pool can be viewed on agent console but agents cannot sign in.</p></li>
<li><p>Agent groups owned by the backup pool can be viewed on agent console and agents can sign in.</p></li>
<li><p>Imported agent groups are not displayed on agent console.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Response group configuration</p></td>
<td><ul>
<li><p>Response groups owned by the primary pool can be viewed, depending on the availability of the primary pool’s back-end database, but cannot be modified.</p></li>
<li><p>Response groups owned by the backup pool can be viewed and modified.</p></li>
<li><p>Imported response groups cannot be viewed with Lync Server Control Panel or the Response Group Configuration Tool, but can be configured by using Lync Server Management Shell cmdlets.</p></li>
</ul></td>
</tr>
</tbody>
</table>


</div>

<div>

## User Experience During Failover

When an administrator invokes failover to a backup pool, response group activity is handled during and after the failover as described in the following table. The first column describes the type of activity that might be taking place. The middle column describes how each activity is handled during the brief time that it takes to fail over to the backup pool. The last column describes how the activity is handled for the duration, after the failover process is complete and the backup pool is standing in for the primary pool.

<div>


> [!NOTE]  
> During disaster recovery, calls behave differently depending on whether the primary pool response groups were imported to the backup pool during recovery. In the following table, references to imported response groups mean that primary pool response groups were imported to the backup pool during disaster recovery mode.



</div>

### Failover Is Initiated

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Type of call or user action</th>
<th>During Failover</th>
<th>After Failover Completes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Calls connected to an agent</p></td>
<td><ul>
<li><p>Regular calls remain connected.</p></li>
<li><p>Anonymous calls are disconnected.</p></li>
</ul></td>
<td><ul>
<li><p>Regular calls remain connected.</p></li>
<li><p>For imported response groups, anonymous calls that have reached the backup pool remain connected.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>In progress calls not yet connected to an agent</p></td>
<td><p>Calls are disconnected.</p></td>
<td><ul>
<li><p>If response groups were not imported, no calls are in this status.</p></li>
<li><p>For imported response groups, calls that have reached the backup pool remain connected.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>New calls</p></td>
<td><ul>
<li><p>Calls are disconnected.</p></li>
<li><p>For imported response groups, calls connect to the backup pool, but agents homed in the primary pool are unreachable.</p></li>
</ul></td>
<td><ul>
<li><p>If response groups were not imported, calls are disconnected.</p></li>
<li><p>For imported response groups, calls connect to the backup pool.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Agent calls on behalf of response group</p></td>
<td><p>Feature is disabled during this stage</p></td>
<td><ul>
<li><p>If response groups were not imported, calls fail.</p></li>
<li><p>For imported response groups, calls succeed.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Agent sign-in and agent information</p></td>
<td><ul>
<li><p>Agent groups owned by the primary pool can be viewed on agent console but agents cannot sign in.</p></li>
<li><p>Agent groups owned by the backup pool can be viewed on agent console and agents can sign in.</p></li>
<li><p>Imported agent groups are displayed on agent console and agents can sign in.</p></li>
</ul></td>
<td><ul>
<li><p>Agent groups owned by the primary pool can be viewed on agent console but agents cannot sign in.</p></li>
<li><p>Agent groups owned by the backup pool can be viewed on agent console and agents can sign in.</p></li>
<li><p>Imported agent groups are displayed on agent console and agents can sign in.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Response group configuration</p></td>
<td><ul>
<li><p>Response groups owned by the primary pool can be viewed, depending on the availability of the primary pool’s back-end database, but cannot be modified.</p></li>
<li><p>Response groups owned by the backup pool can be viewed and modified.</p></li>
<li><p>Imported response groups cannot be viewed with Lync Server Control Panel or the Response Group Configuration Tool, but can be configured by using Lync Server Management Shell cmdlets.</p></li>
</ul></td>
<td><ul>
<li><p>Response groups owned by the primary pool can be viewed, depending on the availability of the back end database, but cannot be modified.</p></li>
<li><p>Response groups owned by the backup pool can be viewed and modified.</p></li>
<li><p>Imported response groups cannot be viewed with Lync Server Control Panel or the Response Group Configuration Tool, but can be configured by using Lync Server Management Shell cmdlets.</p></li>
</ul></td>
</tr>
</tbody>
</table>


</div>

<div>

## User Experience During Failback

When an administrator invokes failback to the primary pool, response group activity is handled during and after the failback as described in the following table.

<div>


> [!NOTE]  
> During disaster recovery, calls behave differently depending on whether the primary pool response groups were imported to the backup pool during recovery. In the following table, references to imported response groups mean that primary pool response groups were imported to the backup pool during disaster recovery mode.



</div>

### Call Handling in Failback

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Type of call or user action</th>
<th>During Failback</th>
<th>After Failback Completes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Calls connected to an agent</p></td>
<td><ul>
<li><p>Regular calls remain connected.</p></li>
<li><p>If response groups were not imported, no anonymous calls are in this status.</p></li>
<li><p>For imported response groups, anonymous calls remain connected.</p></li>
</ul></td>
<td><ul>
<li><p>Regular calls remain connected.</p></li>
<li><p>If response groups were not imported, no anonymous calls are in this status.</p></li>
<li><p>For imported response groups, anonymous calls remain connected.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>In progress calls not yet connected to an agent</p></td>
<td><ul>
<li><p>If response groups were not imported, no calls are in this status.</p></li>
<li><p>For imported response groups, calls will be disconnected.</p></li>
</ul></td>
<td><ul>
<li><p>If response groups were not imported, no calls are in this status.</p></li>
<li><p>For imported response groups, calls will be disconnected.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>New calls</p></td>
<td><p>Calls connect to the primary pool, but agents homed in the primary pool are unreachable.</p></td>
<td><p>Calls connect to the primary pool.</p></td>
</tr>
<tr class="even">
<td><p>Agent calls on behalf of response group</p></td>
<td><p>Feature is disabled during this stage.</p></td>
<td><p>Calls succeed.</p></td>
</tr>
<tr class="odd">
<td><p>Agent sign-in and agent information</p></td>
<td><ul>
<li><p>Agent groups owned by the primary pool can be viewed on agent console but agents cannot sign in.</p></li>
<li><p>Agent groups owned by the backup pool can be viewed on agent console and agents can sign in.</p></li>
<li><p>Imported agent groups are displayed on agent console and agents can sign in.</p></li>
</ul></td>
<td><ul>
<li><p>Agent groups owned by the primary pool can be viewed on agent console and agents can sign in.</p></li>
<li><p>Agent groups owned by the backup pool can be viewed on agent console and agents can sign in.</p></li>
<li><p>Imported agent groups are not displayed on agent console.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Response group configuration</p></td>
<td><ul>
<li><p>Response groups owned by the primary pool can be viewed, depending on the availability of the primary pool’s back-end database, but cannot be modified.</p></li>
<li><p>Response groups owned by the backup pool can be viewed and modified.</p></li>
<li><p>Imported response groups cannot be viewed with Lync Server Control Panel or the Response Group Configuration Tool, but can be configured by using Lync Server Management Shell cmdlets.</p></li>
</ul></td>
<td><ul>
<li><p>Response groups owned by the primary pool can be viewed and modified.</p></li>
<li><p>Response groups owned by the backup pool can be viewed and modified.</p></li>
<li><p>Imported response groups cannot be viewed with Lync Server Control Panel or the Response Group Configuration Tool, but can be configured by using Lync Server Management Shell cmdlets.</p></li>
</ul></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

