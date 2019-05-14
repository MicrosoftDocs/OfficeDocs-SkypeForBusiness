---
title: Lync Server 2013 response group disaster recovery procedures
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Response group disaster recovery procedures
ms:assetid: b49577b7-0ca3-4f20-b614-f3a2a0046b58
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205186(v=OCS.15)
ms:contentKeyID: 48185171
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Response group disaster recovery procedures in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

During the failover phase of disaster recovery, the response groups reside in multiple pools: in the primary pool (which is unavailable) and in the backup pool. The response groups in both pools have the same name and the same owner (the primary pool), but they have different parents. During this time, Response Group cmdlets work a little differently. Be sure to use parameters as specified in the following procedure. For details about how cmdlets work during the failover phase, see NextHop blog article "Lync Server 2013: Recovering Response Groups During Disaster Recovery" at [http://go.microsoft.com/fwlink/p/?LinkId=263957](http://go.microsoft.com/fwlink/p/?linkid=263957). This blog article also applies to the released version of Lync Server 2013.

Use the steps in the following procedure to prepare for and perform disaster recovery for Lync Server Response Group service.

<div>

## To fail over and fail back Response Group

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Routinely perform backups. At the command line, type:
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:<primary pool FQDN>" -FileName "<backup path and file name>"
    
    For example:
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:primary.contoso.com" -FileName "C:\RgsExportPrimary.zip"

3.  During an outage, after failover to the backup pool, import the response groups to the backup pool. At the command line, type:
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:<backup pool FQDN>" -FileName "<backup path and file name>"
    
    If you want to replace the application-level settings in the backup pool with the settings from the primary pool, include the –ReplaceExistingSettings parameter. For example:
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:backup.contoso.com" -FileName "C:\RgsExportPrimary.zip" -ReplaceExistingSettings
    
    <div>
    

    > [!WARNING]  
    > If you do not replace the settings in the backup pool and the primary pool can't be recovered, the primary pool settings will be lost. For details, see <A href="lync-server-2013-planning-for-response-group-disaster-recovery.md">Planning for response group disaster recovery in Lync Server 2013</A>.

    
    </div>

4.  Verify that the import was successful by displaying the imported response groups. The imported response groups are still owned by the primary pool. Do the following:
    
      - Display all the workflows in the backup pool that are owned by the primary pool, and verify that all the primary pool workflows are included. At the command line, type:
        
            Get-CsRgsWorkflow -Identity "service:ApplicationServer:<backup pool FQDN>" -Owner "service:ApplicationServer"<primary pool FQDN>
        
        For example:
        
            Get-CsRgsWorkflow -Identity "service:ApplicationServer:backup.contoso.com" -Owner "service:ApplicationServer:primary.contoso.com"
    
      - Display all the queues in the backup pool that are owned by the primary pool, and verify that all the primary pool queues are included. At the command line, type:
        
            Get-CsRgsQueue -Identity "service:ApplicationServer:<backup pool FQDN>" -Owner "service:ApplicationServer"<primary pool FQDN>
        
        For example:
        
            Get-CsRgsQueue -Identity "service:ApplicationServer:backup.contoso.com" -Owner "service:ApplicationServer"primary.contoso.com"
    
      - Display all the agent groups in the backup pool that are owned by the primary pool, and verify that all the primary pool agent groups are included. At the command line, type:
        
            Get-CsRgsAgentGroup -Identity "service:ApplicationServer:<backup pool FQDN>" -Owner "service:ApplicationServer"<primary pool FQDN>
        
        For example:
        
            Get-CsRgsAgentGroup -Identity "service:ApplicationServer:backup.contoso.com" -Owner "service:ApplicationServer"primary.contoso.com"
    
      - Display all the hours of business in the backup pool that are owned by the primary pool, and verify that all the primary pool hours of business are included. At the command line, type:
        
            Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:<backup pool FQDN>" -Owner "service:ApplicationServer"<primary pool FQDN>
        
        For example:
        
            Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:backup.contoso.com" -Owner "service:ApplicationServer"primary.contoso.com"
    
      - Display all the holiday sets in the backup pool that are owned by the primary pool, and verify that all the primary pool holiday sets are included. At the command line, type:
        
            Get-CsRgsHolidaySet -Identity "service:ApplicationServer:<backup pool FQDN>" -Owner "service:ApplicationServer"<primary pool FQDN>
        
        For example:
        
            Get-CsRgsHolidaySet -Identity "service:ApplicationServer:backup.contoso.com" -Owner "service:ApplicationServer"primary.contoso.com"
    
    Alternatively, you can display all the response groups in the backup pool, including the ones owned by the primary pool and the ones owned by the backup pool by using the –ShowAll parameter instead of the –Owner parameter. For example:
    
        Get-CsRgsWorkflow -Identity "service:ApplicationServer:<backup pool FQDN>" -ShowAll
    
    <div>
    

    > [!IMPORTANT]  
    > You must use either the –ShowAll parameter or the –Owner parameter. If you do not use either of these parameters, the response groups that you imported to the backup pool will not be listed in the results returned by the cmdlets.

    
    </div>

5.  Verify that the import was successful by placing a call to an imported response group and verifying that the call is handled correctly.

6.  Request agents who are members of formal agent groups to sign in to their agent groups in the backup pool.

7.  Manage and modify the imported response groups as usual.
    
    <div>
    

    > [!IMPORTANT]  
    > While the response groups are in the backup pool, you need to use Lync Server Management Shell to manage them. You cannot use Lync Server Control Panel to manage the response groups that you imported to the backup pool.

    
    </div>

8.  After the primary pool is restored and failback is complete, export the primary pool response groups that were imported to the backup pool. At the command line, type:
    
        Export-CsRgsConfiguration -Source ApplicationServer:<backup pool FQDN> -Owner ApplicationServer:<primary pool FQDN> -FileName "<backup path and file name>"

9.  Import the response groups back to the primary pool. At the command line, type:
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:<primary pool FQDN>" -OverwriteOwner -FileName "<exported path and file name>"
    
    For example:
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:primary.contoso.com" -OverwriteOwner -FileName "C:\RgsExportPrimaryUpdated.zip"
    
    <div>
    

    > [!NOTE]  
    > If you rebuild a pool during recovery, whether with the same or a different fully qualified domain name (FQDN), you need to use the –OverwriteOwner parameter. As a rule of thumb, you can always use the –OverwriteOwner parameter when you import response groups back to the primary pool.

    
    </div>
    
    If you deployed a new pool (with the same or a different FQDN) to replace the primary pool, and you want to use the application-level settings from the backup pool for the new pool, include the –ReplaceExistingSettings parameter. At the command line, type:
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:<new primary pool FQDN>" -OverwriteOwner -FileName "<exported path and file name>" -ReplaceExistingSettings
    
    For example:
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:newprimary.contoso.com" -OverwriteOwner -FileName "C:\RgsExportPrimaryUpdated.zip" -ReplaceExistingSettings
    
    <div>
    

    > [!IMPORTANT]  
    > If you don't want to replace the application-level settings and default music-on-hold audio file for the new pool with the settings from the backup pool, the new pool will use the default application-level settings.

    
    </div>

10. Verify that the import back to the primary pool was successful by displaying the imported response group configuration. Do the following:
    
      - Display all the workflows in the primary pool, and verify that all the imported workflows are included. At the command line, type:
        
            Get-CsRgsWorkflow -Identity "service:ApplicationServer:<primary pool FQDN>" -ShowAll
        
        For example:
        
            Get-CsRgsWorkflow -Identity "service:ApplicationServer: primary.contoso.com" -ShowAll
    
      - Display all the queues in the primary pool, and verify that all the imported queues are included. At the command line, type:
        
            Get-CsRgsQueue -Identity "service:ApplicationServer:<primary pool FQDN>" -ShowAll
        
        For example:
        
            Get-CsRgsQueue -Identity "service:ApplicationServer:primary.contoso.com" -ShowAll
    
      - Display all the agent groups in the primary pool, and verify that all the imported agent groups are included. At the command line, type:
        
            Get-CsRgsAgentGroup -Identity "service:ApplicationServer: <primary pool FQDN>" -ShowAll
        
        For example:
        
            Get-CsRgsAgentGroup -Identity "service:ApplicationServer:primary.contoso.com" -ShowAll
    
      - Display all the hours of business in the primary pool, and verify that all the imported hours of business are included. At the command line, type:
        
            Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:<primary pool FQDN>" -ShowAll
        
        For example:
        
            Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:primary.contoso.com" -ShowAll
    
      - Display all the holiday sets in the primary pool, and verify that all the imported holiday sets are included. At the command line, type:
        
            Get-CsRgsHolidaySet -Identity "service:ApplicationServer:<primary pool FQDN>" -ShowAll
        
        For example:
        
            Get-CsRgsHolidaySet -Identity "service:ApplicationServer:primary.contoso.com" -ShowAll

11. Verify that the import was successful by placing a call to an imported response group and verifying that the call is handled correctly.

12. Optionally, remove the response groups owned by the primary pool from the backup pool. At the command line, type:
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:<backup pool FQDN>" -Owner "service:ApplicationServer:<primary pool FQDN>" -FileName "<backup path and file name>" -RemoveExportedConfiguration
    
    For example:
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:backup.contoso.com" -Owner "service:ApplicationServer:primary.contoso.com" -FileName "C:\RgsExportPrimaryUpdated.zip" -RemoveExportedConfiguration
    
    <div>
    

    > [!NOTE]  
    > This step creates a new file with the exported configuration, and then removes it from the backup pool.

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

