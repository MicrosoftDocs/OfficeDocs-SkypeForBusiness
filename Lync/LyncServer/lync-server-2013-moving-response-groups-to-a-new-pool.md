---
title: 'Lync Server 2013: Moving response groups to a new pool'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Moving response groups to a new pool
ms:assetid: da0db765-41e5-430b-b5a7-5418ec5ff2a7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205298(v=OCS.15)
ms:contentKeyID: 48185538
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Moving response groups to a new pool in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

Lync Server 2013 introduces new cmdlet support for moving response groups from one pool to another pool, even when the fully qualified domain name (FQDN) is different.

Use the steps in the following procedure to move response groups from one Front End pool to another Front End pool with a different FQDN.

<div>


> [!NOTE]  
> In a coexistence environment, you can move response groups only between Lync Server 2013&nbsp;Front End pools.



</div>

<div>

## To move response groups to a pool with a different FQDN

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Export the response groups in the source pool. At the command line, type:
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:<source FQDN>" -FileName "<export file name>"
    
    For example:
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:source.contoso.com" -FileName "C:\RgsExportSource.zip"
    
    To remove the response groups from the source pool during the export, include the –RemoveExportedConfiguration parameter. For example:
    
        Export-CsRgsConfiguration -Source ApplicationServer:source.contoso.com -FileName "C:\RgsExportSource.zip" -RemoveExportedConfiguration

3.  Import the response groups to the destination pool and assign the destination pool as the new owner. At the command line, type:
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:<destination pool>" -FileName "<export file name>" -OverwriteOwner
    
    If you also want to copy the Response Group application-level settings from the source pool to the destination pool, include the –ReplaceExistingRgsSettings parameter. You can define only one set of application-level settings per pool. If you copy the application-level settings from the source pool to the destination pool, the settings from the source pool replace the settings for the destination pool. If you do not copy the application-level settings from the source pool, the existing settings from the destination pool apply to the imported response groups.
    
    For example:
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:destination.contoso.com" -FileName "C:\RgsExportSource.zip" -OverwriteOwner -ReplaceExistingRgsSettings
    
    <div>
    

    > [!NOTE]  
    > Application-level settings include the default music-on-hold configuration, the default music-on-hold audio file, the agent ringback grace period, and the call context configuration. To view these configuration settings, run the <STRONG>Get-CsRgsConfiguration</STRONG> cmdlet. For details about this cmdlet, see <A href="https://docs.microsoft.com/powershell/module/skype/Get-CsRgsConfiguration">Get-CsRgsConfiguration</A>.

    
    </div>

4.  Verify that the import was successful by displaying the imported response group configuration by doing the following:
    
      - Verify that all the workflows were imported. At the command line, type the following:
        
            Get-CsRgsWorkflow -Identity "service:ApplicationServer:<destination pool FQDN>"
    
      - Verify that all the queues were imported. At the command line, type the following:
        
            Get-CsRgsQueue -Identity "service:ApplicationServer:<destination pool FQDN>"
    
      - Verify that all the agent groups were imported. At the command line, type the following:
        
            Get-CsRgsAgentGroup -Identity "service:ApplicationServer:<destination pool FQDN>"
    
      - Verify that all the hours of business were imported. At the command line, type the following:
        
            Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:<destination pool FQDN>" 
    
      - Verify that all the holiday sets were imported. At the command line, type the following:
        
            Get-CsRgsHolidaySet -Identity "service:ApplicationServer:<destination pool FQDN>" 

5.  Verify that the import was successful by placing a call to one of the response groups and verifying that the call is handled correctly.

6.  Request agents who are members of formal agent groups to sign in to their agent groups in the destination pool.

7.  If you did not previously remove response groups from the source pool, remove the response groups from the source pool. At the command line, type:
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:<source pool FQDN> -RemoveExportedConfiguration -FileName "<temporary export file name>"
    
    For example:
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:source.contoso.com" -RemoveExportedConfiguration -FileName "C:\TempRGsConfiguration.zip"

</div>

</div>

<span> </span>

</div>

</div>

</div>

