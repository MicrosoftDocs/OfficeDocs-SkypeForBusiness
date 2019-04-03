---
title: 'Lync Server 2013: Backup and restoration worksheets'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Backup and restoration worksheets
ms:assetid: 26c78155-0306-41ac-845b-7ad58000a1d6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh202169(v=OCS.15)
ms:contentKeyID: 51541460
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Backup and restoration worksheets for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-18_

The backup and restoration plan for your organization should contain details about how and when you back up data and settings. You can use the worksheets presented here to help you document this information for your specific deployment and for your organization's backup and restoration requirements.

Use the following worksheets to record the information that you need to back up and restore database, File Store, and settings information for a Lync Server pool or Standard Edition server. Keep one or more copies of these worksheets in a secure location so that they are readily accessible if you need to restore Lync Server.

<div>


> [!NOTE]  
> The worksheets in this section cover only the information that is required to restore the data and settings of Lync Server databases and servers. If you need to document other restoration information, such as the information for reinstalling operating systems and other software, use your organization's deployment plans and backup and restoration plans to address those requirements.



</div>

<div>

## Database Backup and Restoration Worksheet

Use the following table to record the information that you need to back up and restore Lync Server databases.

### Database Information for Backup and Restoration

<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Database</th>
<th>Server name (FQDN)</th>
<th>Backup schedule</th>
<th>Database backup tool</th>
<th>Backup set</th>
<th>Backup destination</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Rtc database on Back End Server for user data</p></td>
<td><p>                    </p></td>
<td><p>                    </p></td>
<td><p><strong>Export-CsUserData</strong> cmdlet</p></td>
<td><p>Name:</p>
<p>Expiration:</p>
<p>                   </p></td>
<td><p>                    </p></td>
<td><p>                    </p></td>
</tr>
<tr class="even">
<td><p>LcsLog (default name) database on Archiving database server</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>SQL Server management tool</p></td>
<td><p>Name:</p>
<p>Expiration:</p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>LcsCdr database on Monitoring database server for call detail records (CDRs)</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>SQL Server management tool</p></td>
<td><p>Name:</p>
<p>Expiration:</p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>QoEMetrics database on Monitoring database server for Quality of Experience (QoE) data</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>SQL Server management tool</p></td>
<td><p>Name:</p>
<p>Expiration:</p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Persistent Chat Database</p></td>
<td></td>
<td></td>
<td><p>SQL Server management tool or <strong>Export-CsPersistentChatData</strong> cmdlet</p></td>
<td><p>Name:</p>
<p>Expiration:</p></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>


No backup or restoration is required of the following databases:

  - Rtcdyn. The transient user data in this database is not necessary for restoration of service.

  - Rtcab. The Address Book database is automatically recreated from the Global Address List (GAL) in Active Directory Domain Services.

  - Rgsdyn. The transient Response Group service data in this database is not necessary for restoration of service.

  - Cpsdyn. The dynamic information for the Call Park application is not necessary for restoration of service.

  - MgcComp. The compliance database for Persistent Chat is not necessary for restoration of service.

</div>

<div>

## File Store Backup and Restoration Worksheet

Use the following table to record the information that you need to back up and restore the File Stores. File Stores contain data such as meeting content metadata, meeting compliance logs, update logs for device updates, and audio files for the Response Group, Call Park, and Announcement applications.

### File Store Information for Backup and Restoration

<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Content</th>
<th>Server name (FQDN)</th>
<th>Backup schedule</th>
<th>File system backup tool</th>
<th>File share to be backed up *</th>
<th>Backup destination</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync Server File Store</p></td>
<td></td>
<td></td>
<td><p>Standard backup tool, such as Robocopy</p></td>
<td><p>On file server for Enterprise Edition. On Standard Edition by default, for Standard Edition deployment. Typically, one per site.</p></td>
<td></td>
<td><p>Files named <strong>Meeting.Active</strong> should not be backed up. These files are in use and are locked while a meeting takes place.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Settings Backup and Restoration Worksheet

Use the following table to record the information that you need to back up and restore settings.

### Settings Information for Backup and Restoration

<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Database</th>
<th>Server name (FQDN)</th>
<th>Backup schedule</th>
<th>Backup tool</th>
<th>Configuration file (.xml) name</th>
<th>Backup location</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Xds database in Central Management store for topology configuration (global)</p></td>
<td><p>                    </p></td>
<td><p>                    </p></td>
<td><p><strong>Export-CsConfiguration</strong> cmdlet</p></td>
<td><p>                   </p></td>
<td><p>                    </p></td>
<td><p>                   </p></td>
</tr>
<tr class="even">
<td><p>Lis database in Central Management store for E9-1-1 location information (global)</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p><strong>Export-CsLisConfiguration</strong> cmdlet</p></td>
<td></td>
<td><p> </p></td>
<td><p>                    </p></td>
</tr>
<tr class="odd">
<td><p>RgsConfig database on Back End Server for Response Group configuration (pool)</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p><strong>Export-CsRgsConfiguration</strong> cmdlet</p></td>
<td></td>
<td><p> </p></td>
<td><p>                    </p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

