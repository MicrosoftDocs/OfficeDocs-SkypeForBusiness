---
title: 'Lync Server 2013: Backup and restoration requirements: tools and permissions'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: 'Backup and restoration requirements: tools and permissions'
ms:assetid: 35ec2e33-f33e-4f84-9e64-6550fd78aa52
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh202171(v=OCS.15)
ms:contentKeyID: 51541465
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Backup and restoration requirements in Lync Server 2013: tools and permissions

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-17_

This topic identifies the tools that you can use to back up and restore Lync Server 2013, the permissions that you need, and whether you can run commands remotely or locally. Specifically, this topic focuses on tools that are provided with Lync Server for backup and restoration.

<div>

## Backups

To back up Lync Server, use the tools identified in the following table. All the commands that you need to back up Lync Server can be scripted and can be run remotely.

### Tools for Backing Up Lync Server

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>To back up this:</th>
<th>Use this tool or cmdlet:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Topology configuration data (Xds.mdf)</p></td>
<td><p>Export-CsConfiguration</p></td>
</tr>
<tr class="even">
<td><p>Location information service (E9-1-1) data (Lis.mdf)</p></td>
<td><p>Export-CsLisConfiguration</p></td>
</tr>
<tr class="odd">
<td><p>Response Group configuration data (RgsConfig.mdf)</p></td>
<td><p>Export-CsRgsConfiguration</p></td>
</tr>
<tr class="even">
<td><p>Persistent user data (Rtcxds.mdf database)</p>
<p>Conference IDs</p></td>
<td><p>Export-CsUserData</p></td>
</tr>
<tr class="odd">
<td><ul>
<li><p>Archiving database (LcsLog.mdf)</p></li>
<li><p>Monitoring call detail record database (LcsCDR.mdf)</p></li>
<li><p>Monitoring QoE database (QoEMetrics.mdf)</p></li>
</ul></td>
<td><p>SQL Server database tool, such as SQL Server Management Studio</p></td>
</tr>
<tr class="even">
<td><p>Persistent Chat database (Mgc.mdf)</p></td>
<td><p>SQL Server backup procedures or Export-CsPersistentChatData. Export-CsPersistentChatData exports Persistent Chat data as a file.</p></td>
</tr>
<tr class="odd">
<td><p>All file stores: Lync Server file store, Archiving file store</p>
<div>

> [!NOTE]  
> Files named <STRONG>Meeting.Active</STRONG> should not be backed up. These files are in use and locked while a meeting takes place.


</div></td>
<td><p>Standard file system management tool, such as Robocopy.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Restoration

To restore Lync Server, use the tools in the following table. All the commands that you need to restore Lync Server can be scripted. Some can be run remotely, but others need to be run locally, as specified in the following table.

### Tools for Restoring Lync Server

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>To do this:</th>
<th>Use this tool or cmdlet:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Build a new or clean computer</p></td>
<td><ul>
<li><p>Windows operating system installation software</p></li>
<li><p>SQL Server installation software</p></li>
<li><p>Certificates Microsoft Management Console (MMC) snap-in, if restoring certificates with an exportable private key</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Restore file store data</p></td>
<td><p>Standard file system management tool, such as Robocopy</p></td>
</tr>
<tr class="odd">
<td><p>Recreate empty databases and set permissions for the following:</p>
<ul>
<li><p>Central Management store</p></li>
<li><p>Back End Server</p></li>
<li><p>Monitoring database</p></li>
<li><p>Archiving database</p></li>
</ul></td>
<td><p>Install-CsDatabase</p></td>
</tr>
<tr class="even">
<td><p>Restore the Active Directory Domain Services pointer to the Central Management store</p>
<div>

> [!NOTE]  
> If you lose the service connection point at any time, you can rerun this cmdlet.


</div></td>
<td><p>Set-CsConfigurationStoreLocation</p></td>
</tr>
<tr class="odd">
<td><p>Import the topology, policies, and configuration settings to the Central Management store (Xds.mdf)</p></td>
<td><p>Import-CsConfiguration</p></td>
</tr>
<tr class="even">
<td><p>Publish and enable the topology</p></td>
<td><p>Topology Builder</p>
<p>-or-</p>
<p>Publish-CsTopology and Enable-CsTopology</p></td>
</tr>
<tr class="odd">
<td><p>Enable the last published topology</p></td>
<td><p>Enable-CsTopology</p></td>
</tr>
<tr class="even">
<td><p>Reinstall Lync Server components</p></td>
<td><p>Lync Server Setup</p>
<div>

> [!NOTE]  
> Located in the Lync Server installation folder or media at \setup\amd64\Setup.exe.


</div></td>
</tr>
<tr class="odd">
<td><p>Restore location information (E9-1-1) data (Lis.mdf)</p></td>
<td><p>Import-CsLisConfiguration</p></td>
</tr>
<tr class="even">
<td><p>Restore persistent user data (Rtcxds.mdf)</p></td>
<td><p>Import-CsUserData</p></td>
</tr>
<tr class="odd">
<td><p>Restore Response Group configuration data (RgsConfig.mdf)</p></td>
<td><p>Import-CsRgsConfiguration</p>
<div>

> [!NOTE]  
> If the configuration is being restored in a newly deployed pool that has no Response Group data in the database, then you should use the –OverwriteOwner option. Use this option even if the data being restored is in a pool with the same fully qualified domain name (FQDN). Otherwise, the import will not succeed, due to the contact objects to the Response Groups already existing in Active Directory.


</div></td>
</tr>
<tr class="even">
<td><p>Restore the following databases:</p>
<ul>
<li><p>Archiving database (LcsLog.mdf)</p></li>
<li><p>Monitoring databases: call detail record database (LcsCDR.mdf) and QoE database (QoEMetrics.mdf)</p></li>
</ul></td>
<td><p>SQL Server database management tools</p></td>
</tr>
<tr class="odd">
<td><p>Persistent Chat database (Mgs.mdf)</p></td>
<td><p>SQL Server restore procedures or Import-CsPersistentChatData. You can use Import-CsPersistentChatData with a file created by Export-CsPersistentChatData, and the data will be imported into the Persistent Chat database.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Required Permissions

Users must be a member of the **RTCUniversalServerAdmins** group to perform all the commands described in this topic. Most backup and restore commands do not support role-based access control (RBAC). Two exceptions are the Persistent Chat cmdlets Export-CsPersistentChatData and Import-CsPersistentChatData, which must be run by a user who is a member of the CsPersistentChatAdministrator group. To run Lync Server Deployment Wizard, a user must also be a member of the Local Adminstrators group.

</div>

</div>

<span> </span>

</div>

</div>

</div>

