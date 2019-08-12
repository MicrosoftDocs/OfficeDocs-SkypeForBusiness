---
title: 'Lync Server 2013: Planning for response group disaster recovery'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Planning for response group disaster recovery
ms:assetid: 14e0f5dc-77cd-42cd-a9c9-4d0da38fb1cf
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204699(v=OCS.15)
ms:contentKeyID: 48183482
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Planning for response group disaster recovery in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

This section describes some ways to prepare response groups for disaster recovery and provides an overview of the disaster recovery process.

<div>

## Preparing for Response Group Disaster Recovery

Keep the following in mind when you prepare for and carry out disaster recovery procedures.

<div>


> [!NOTE]  
> In a coexistence environment, only the Lync Server 2013 response groups are supported for the disaster recovery procedures described in this document.



</div>

  - Plan for disaster recovery when you do your capacity planning. For disaster recovery capacity, each pool in a paired pool should be able to handle the workloads of all the response groups in both pools. For details about Response Group capacity planning, see [Capacity planning for Response Group in Lync Server 2013](lync-server-2013-capacity-planning-for-response-group.md).

  - Take regular backup copies of all the response group configurations in all the Front End pools where you deployed the Response Group application by using the export procedure described in this document. For details, see [Response group disaster recovery procedures in Lync Server 2013](lync-server-2013-response-group-disaster-recovery-procedures.md). Keep the backup copies in a safe location.

  - Keep a separate backup copy of all the original audio files you used for the Response Group application, including any recordings and music-on-hold files. Keep the backup files in a safe location.

  - For Lync Server 2013 disaster recovery, all Response Group settings must have unique names across your deployment. This requirement applies to workflows, queues, agent groups, holiday sets, and hours of business. You should verify that this requirement is met when the primary and backup pools are still active, and before you need to initiate any failover procedure. If you encounter name conflicts while importing response group data to the backup pool, the import fails. To complete the import and failover procedure, you need to resolve the name conflicts by renaming the response group object in the backup pool or by using the **Import-CsRgsConfiguration** cmdlet with the –ResolveNameConflicts parameter to automatically resolve the conflict by appending a unique identifying number to the response group object.

  - In general, we recommend that you perform daily backups, but if you have a high volume of changes, you might want to schedule more frequent backups. The amount of information you can lose in the event of a disaster depends on the frequency of your backups, as well as the frequency and volume of changes.

  - It is possible to import response groups to a backup pool before a disaster or failover operation occurs. Importing response groups in advance reduces downtime, because the Lync Server Response Group service can be restored in the backup pool as soon as calls are routed to the backup pool.
    
    <div>
    

    > [!NOTE]  
    > The Response Group application cannot reach any agents homed in an inactive pool until failover is complete. During this time, the Response Group application processes calls as if those agents are unavailable.

    
    </div>

</div>

<div>

## Response Group Disaster Recovery Process

In the event of a disaster, you can recover response groups by using either of the following recovery approaches:

  - Fail over to a backup pool and then fail back to the original pool.

  - Fail over to a backup pool, create a new pool with a different fully qualified domain name (FQDN), and then import the response groups to the new pool.

During the failover phase of disaster recovery, the response groups reside in multiple pools: in the primary pool (which is unavailable) and in the backup pool. The response groups in both pools have the same name and the same owner (the primary pool), but they have different parents.

When you recover by creating a new pool with a different FQDN, you need to assign the new pool as the owner of the response groups when you import them. Ownership of response groups remains with the original pool unless or until you explicitly reassign ownership by using the –OverwriteOwner parameter with the **Import-CsRgsConfiguration** cmdlet.

<div>


> [!NOTE]  
> You also need to use the –OverwriteOwner parameter if you rebuilt the pool during the recovery (that is, the Response Group database is empty), whether or not you use the same FQDN. You do not need to use the –OverwriteOwner parameter if you did not rebuild the pool, but it is permissible to use this parameter whenever you import response groups back to the primary pool.



</div>

You can define only one set of application-level Response Group configuration settings per pool. These settings include the default music-on-hold configuration, the default music-on-hold audio file, the agent ringback grace period, and the call context configuration. To view these configuration settings, run the **Get-CsRgsConfiguration** cmdlet. For details about the **Get-CsRgsConfiguration** cmdlet, see [Get-CsRgsConfiguration](https://docs.microsoft.com/powershell/module/skype/Get-CsRgsConfiguration).

You can transfer these application-level settings from one pool to another by using the **Import-CsRgsConfiguration** cmdlet with the –ReplaceExistingSettings parameter, but doing so overrides the settings in the destination pool.

<div>


> [!IMPORTANT]  
> This constraint about transferring settings to another pool is true only for the application-level settings and the default music-on-hold audio file. It does not apply to agent groups, queues, workflows, business hours, and holiday sets.



</div>

If you don't want to replace the application-level settings in the backup pool during a disaster and the primary pool can't be recovered, the application-level settings from the primary pool will be lost. If you need to create a new pool to replace the primary pool during recovery, either with the same FQDN or with a different FQDN, you can't recover the original application-level settings. In this case, you need to configure the new pool with these settings and include the music-on-hold audio file.

If you decide to use the **Import-CsRgsConfiguration** cmdlet to transfer application-level settings from the primary pool to the backup pool during a disaster, you can then transfer the settings from the backup pool to the new pool during recovery in the same way that you transferred them from the primary pool to the backup pool.

The following table is an overview of the steps involved in recovering response groups.

For details about performing these steps, see [Response group disaster recovery procedures in Lync Server 2013](lync-server-2013-response-group-disaster-recovery-procedures.md).

### Response Group Disaster Recovery Steps

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Phase</th>
<th>Steps</th>
<th>Required groups and roles</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Before outage</p></td>
<td><p>On a routine basis, run the <strong>Export-CsRgsConfiguration</strong> cmdlet to create backups of all Response Group configurations in all Front End pools where Response Group application is deployed.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsResponseGroupAdministrator</p></td>
</tr>
<tr class="even">
<td><p>During outage</p></td>
<td><p>Run the <strong>Import-CsRgsConfiguration</strong> cmdlet to import the backed up Lync Server Response Group service configuration from the primary pool to the backup pool.</p>
<div>

> [!NOTE]  
> Use the –ReplaceExistingSettings parameter if you want to replace application-level Response Group settings in the backup pool with the settings from the primary pool. If you do not transfer the application-level settings from the primary pool to the backup pool, and the primary pool can't be recovered, you will lose the settings from the primary pool.


</div></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsResponseGroupAdministrator</p></td>
</tr>
<tr class="odd">
<td><p>After importing</p></td>
<td><p>Run Response Group cmdlets with either the –ShowAll parameter (to display all response groups) or the –Owner parameter (to display only imported response groups) to verify that all response group configurations were imported to the backup pool.</p>
<div>

> [!IMPORTANT]  
> If you do not use either the –ShowAll parameter or the –Owner parameter, the response groups that you imported to the backup pool will not be listed in the results returned by the cmdlets.


</div>
<p>Run the following cmdlets:</p>
<ul>
<li><p><strong>Get-CsRgsWorkflow</strong></p></li>
<li><p><strong>Get-CsRgsQueue</strong></p></li>
<li><p><strong>Get-CsRgsAgentGroup</strong></p></li>
<li><p><strong>Get-CsRgsHoursOfBusiness</strong></p></li>
<li><p><strong>Get-CsRgsHolidaySet</strong></p></li>
</ul></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsResponseGroupAdministrator</p></td>
</tr>
<tr class="even">
<td><p>After failover</p></td>
<td><ul>
<li><p>Place a test call to a response group that was imported to the backup pool and verify that the call is handled correctly.</p></li>
<li><p>All formal agents must sign in again to their formal groups on backup pool.</p></li>
<li><p>Manage configuration changes:</p>
<p>Response groups in the backup pool, whether imported to the backup pool or owned by the backup pool, can be modified as usual during the outage.</p>
<div>

> [!IMPORTANT]  
> You must use Lync Server Management Shell to manage the response groups that you imported to the backup pool. You cannot use Lync Server Control Panel to manage these response groups while they are in the backup pool.


</div></li>
</ul></td>
<td><p>N/A</p></td>
</tr>
<tr class="odd">
<td><p>After recovery, before failback</p></td>
<td><p>Run the <strong>Export-CsRgsConfiguration</strong> cmdlet specifying the -Source parameter as the backup pool and the –Owner parameter as the primary pool to export the response groups owned by the primary pool from the backup pool.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsResponseGroupAdministrator</p></td>
</tr>
<tr class="even">
<td><p>After failback</p></td>
<td><ul>
<li><p>Run the <strong>Import-CsRgsConfiguration</strong> cmdlet to import the response groups back to the primary pool.</p>
<div>

> [!NOTE]  
> If the primary pool can't be recovered and you deploy a new pool to replace it, use the –ReplaceExistingSettings parameter to transfer the application-level settings from the backup pool to the new pool. If you do not transfer the settings from the backup pool, the new pool will use the default settings.


</div></li>
<li><p>Run the following cmdlets with either the –ShowAll parameter (to display all response groups) or the –Owner parameter (to display only imported response groups) to verify that all response group configurations were successfully imported back to the primary pool:</p>
<ul>
<li><p><strong>Get-CsRgsWorkflow</strong></p></li>
<li><p><strong>Get-CsRgsQueue</strong></p></li>
<li><p><strong>Get-CsRgsAgentGroup</strong></p></li>
<li><p><strong>Get-CsRgsHoursOfBusiness</strong></p></li>
<li><p><strong>Get-CsRgsHolidaySet</strong></p></li>
</ul></li>
<li><p>Place a test call to a response group that was imported back to the primary pool and verify that the call is handled correctly.</p></li>
<li><p>Optionally, run the <strong>Export-CsRgsConfiguration</strong> cmdlet on the backup pool with the –RemoveExportedConfiguration parameter to remove the response groups owned by the primary pool from the backup pool.</p></li>
</ul></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsResponseGroupAdministrator</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

