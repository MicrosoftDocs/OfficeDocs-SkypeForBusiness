---
title: 'Lync Server 2013: Backing up core data and settings'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Backing up core data and settings
ms:assetid: 278bc95a-7b8d-4e01-a872-a844830459de
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh202170(v=OCS.15)
ms:contentKeyID: 51541452
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Backing up core data and settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-04-23_

The following procedures use Lync Server Management Shell cmdlets to create backup files for settings and data for core services. For details about the tools used in this section, including where they are located, see [Backup and restoration requirements in Lync Server 2013: tools and permissions](lync-server-2013-backup-and-restoration-requirements-tools-and-permissions.md). For details about backing up Archiving and Monitoring data, see [Backing up Archiving and Monitoring databases in Lync Server 2013](lync-server-2013-backing-up-archiving-and-monitoring-databases.md).

<div>


> [!NOTE]  
> The step in this section to back up the Central Management store includes the settings and configuration for Archiving and Monitoring.



</div>

You can run the cmdlets described in this section locally or remotely.

<div>

## To back up core data and settings

1.  From a user account that is a member of the RTCUniversalServerAdmins group, log on to any computer in your internal deployment.

2.  To store the backups you create in the following steps, create a new shared folder and update the path referenced by **$Backup** to the new shared folder.

3.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

4.  Back up the Central Management store configuration file. At the command line, type the following:
    
        Export-CsConfiguration -FileName <path and file name for backup>
    
    For example:
    
        Export-CsConfiguration -FileName "C:\Config.zip"
    
    <div>
    

    > [!NOTE]  
    > This step exports your Lync Server topology, policies, and configuration settings to a file. No other step is required to backup topology data.

    
    </div>

5.  Copy the backed-up Central Management store configuration file to $Backup\\.

6.  Back up Location Information service data. At the command line, type the following:
    
        Export-CsLisConfiguration -FileName <path and file name for backup>
    
    For example:
    
        Export-CsLisConfiguration -FileName "C:\E911Config.zip"

7.  Copy the backed-up Location Information service configuration file to $Backup\\.

8.  Back up user data on every back-end database of a Front End pool and every Standard Edition server. At the command line, type the following:
    
        Export-CsUserData -PoolFQDN <Fqdn> -FileName <String>
    
    For example:
    
        Export-CsUserData -PoolFQDN "atl-cs-001.litwareinc.com" -FileName "C:\Logs\ExportedUserData.zip"

9.  Copy the backed up user file to $Backup\\.

10. On every pool that runs the Response Group application, back up the Response Group configuration. Do the following:
    
    1.  At the command line, type:
        
            Export-CsRgsConfiguration -Source "service:ApplicationServer:<pool FQDN>" -FileName <path and file name for backup>
        
        For example:
        
            Export-CsRgsConfiguration -Source ApplicationServer:pool01.contoso.com -FileName C:\RgsConfiguration.zip

11. Copy the backed up Response Group configuration file to $Backup\\.

</div>

</div>

<span> </span>

</div>

</div>

</div>

