---
title: 'Lync Server 2013: Front End pool ABC failover procedure'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Front End pool ABC failover procedure
ms:assetid: 67763ad3-6796-45eb-a486-901f21ac1a95
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945635(v=OCS.15)
ms:contentKeyID: 51541486
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Front End pool ABC failover procedure in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-05-22_

Use the following steps to perform the ABC failover procedure. This procedure contains a high-level description of each step, followed by commands and cmdlets to be run for each step.

To run the cmdlets, open a Lync Server Management Shell using Run as Administrator.

<div>

## To Perform an ABC Failover

1.  Check whether the pool A is the host for the Central Management Server (CMS).
    
      - Run the following cmdlet:
        
            Get-CsService -CentralManagement
        
        If the Identity field of the active CMS points to the fully qualified domain name (FQDN) of Pool A, then you use steps 2 and 3 of this procedure to fail over the Central Management Server first. Otherwise, skip to step 4.

2.  Fail over the CMS to Pool B in disaster recovery mode by running the following cmdlet:
    
        Invoke-CsManagementServerFailover -BackupSqlServerFqdn <Pool B BE FQDN> -BackupSqlInstanceName <Pool B BE instance name> [-BackupMirrorSqlServerFqdn <Pool B Mirror BE FQDN> -BackupMirrorSqlInstanceName <Pool B Mirror BE Instance name>] -Force -Verbose
    
    After you do this, we recommend that you move the CMS from pool B to another existing paired pool for extra resiliency. For details, see [Move-CsManagementServer](https://docs.microsoft.com/powershell/module/skype/Move-CsManagementServer)..

3.  If Pool A contains CMS, import the LIS configuration from pool A into pool B’s LIS database (Lis.mdf). This will work only if you have been backing up LIS data on a regular basis. To import the LIS configuration, run the following cmdlets:
    
        Import-CsLisConfiguration -FileName <String> 
        Publish-CsLisConfiguration

4.  Import backed-up Lync Server Response Group service workflows from pool A into pool B.
    
    <div>
    

    > [!NOTE]  
    > Currently, the <STRONG>Import-CsRgsConfiguration</STRONG> cmdlet requires that the queue and workflow names on pool A are distinct from the queue and workflow names on pool B. If the names are not distinct, you will get an error when running the <STRONG>Import-CsRgsConfiguration</STRONG> cmdlet, and the queues and workflows will need to be renamed in pool B before proceeding with <STRONG>Import-CsRgsConfiguration</STRONG> cmdlet.

    
    </div>
    
    You have two options for importing the Response Group configuration from pool A to pool B. Which option you use depends on whether you want to overwrite the application-level settings of pool B with the application-level settings in pool A.
    
      - If you want to overwrite the Pool B settings, run the **Import-CsRgsConfiguration** cmdlet with the **ReplaceExistingSettings** option:
        
            Import-CsRgsConfiguration -Destination "service:ApplicationServer:<Pool B FQDN>" -FileName "C:\RgsExportPrimary.zip"  -ReplaceExistingRgsSettings
    
      - If you do not want to overwrite the Pool B settings, use the **Import-CsRgsConfiguration** cmdlet without the **ReplaceExistingSettings** option.
        
            Import-CsRgsConfiguration -Destination "service:ApplicationServer:<Pool B FQDN>" -FileName "C:\RgsExportPrimary.zip"
    
    <div>
    

    > [!WARNING]  
    > Keep in mind that if you do not want to overwrite the application-level settings of the backup pool (pool B) with the settings of the primary pool (pool A), pool A’s application-level settings will be lost if pool A is lost, because the Response Group application can store only one set of application-level settings per pool. When pool C is deployed to replace pool A, the application-level settings must be reconfigured, including the default music-on-hold audio file.

    
    </div>

5.  Verify that the Response Group configuration import was successful by running the following cmdlets to display the imported response groups. Note that the imported response groups are still owned by pool A.
    
        Get-CsRgsWorkflow -Identity "service:ApplicationServer:<Pool B FQDN>" -Owner "service:ApplicationServer:<Pool A FQDN>"
        
        Get-CsRgsQueue -Identity "service:ApplicationServer:<Pool B FQDN>" -Owner "service:ApplicationServer:<Pool A FQDN>"
        
        Get-CsRgsAgentGroup -Identity "service:ApplicationServer:<Pool B FQDN>" -Owner "service:ApplicationServer:<Pool A FQDN>"

6.  For Unassigned Numbers, move the Unassigned Number ranges that are using "Announcement" as the selected announcement service from pool A to pool B. To do so:
    
      - Re-create all announcements that were deployed in pool A on pool B. If any audio files were used when deploying the announcements in pool A, these files will be needed to re-create the announcements in pool B. To re-create the announcements in pool B, use the **New-CsAnnouncement** cmdlets, with pool B as the Parent service.
    
      - Retarget all the Unassigned Number ranges that are targeting an announcement in pool A to the newly deployed announcements in pool B. Run the following cmdlet for every Unassigned Number range targeting an announcement of pool A:
        
            Set-CsUnassignedNumber -Identity "<Range Name>" -AnnouncementService "<Pool B FQDN>" -AnnouncementName "<New Announcement in pool B>"
    
    <div>
    

    > [!NOTE]  
    > This step is not required for unassigned number ranges that use "Exchange UM" as the selected announcement service.

    
    </div>

7.  Fail over Pool A to Pool B in Disaster Recovery (DR) mode, by running the following cmdlet:
    
        Invoke-CsPoolFailover -PoolFqdn <Pool A FQDN> -DisasterMode

8.  Build pool C, but do not start any services on pool C.
    
    Note that this step can be carried out concurrently with steps 5 and 6.

9.  Force users homed on pool A to move to pool C by running the following cmdlet:
    
        Get-csuser -Filter {RegistrarPool -eq "<Pool A FQDN>"} | Move-CsUser -Target <Pool C FQDN> -Force
    
    At this point, users homed on pool A will begin to experience a service outage. This outage will continue until step 16, at which point services are started on pool C.

10. Force the conference directory of pool A to move to pool C by running the following cmdlet:
    
        Move-CsConferenceDirectory -Identity <Conference Directory ID of Pool A> -TargetPool <Pool C FQDN> -Force

11. Force the Conference Auto Attendant (CAA) Contact Object to move from pool A to pool C by running the following cmdlet:
    
        Move-csApplicationEndpoint -Identity "<Pool A CAA Uri>" -targetApplicationPool <Pool C FQDN> -force

12. Copy conference content from pool B to pool C.

13. Export user data from pool B and import the user data into pool C by running the following cmdlets:
    
        Export-CsUserData -PoolFqdn <Pool B Fqdn> -FileName <String>
        Import-CsUserData -PoolFqdn <Pool C Fqdn> -FileName <String>

14. Restore backed-up Call Park application data from pool A into pool C and assign the Call Park orbit ranges of pool A to pool C.
    
      - You can reassign a Call Park orbit range of pool A to pool C either through the Lync Server Control Panel or the Lync Server Management Shell. For the Lync Server Management Shell, run the following cmdlet for every Call Park orbit range assigned to pool A (note that the Identity parameter refers to the Call Park Orbit Ranges that belong to pool A):
        
            Set-CsCallParkOrbit -Identity "<Call Park Orbit Identity>" -CallParkService "service:ApplicationServer:<Pool C FQDN>"
    
      - If a customized music-on-hold has been configured for Call Park in pool A, restore the Call Park customized music-on-hold file in pool C.
        
            Xcopy <Source> <Destination: Pool C CPS File Store Path>
        
        For example:
        
            Xcopy "Source Path" "<Pool C File Store Path>\OcsFileStore\coX-ApplicationServer-X\AppServerFiles\CPS\"
    
      - Finally, reconfigure the Call Park settings on pool C by using the **Set-CsCpsConfiguration** cmdlet. The Call Park application can store only one set of settings and one customized music-on-hold audio file per pool, and these settings are not backed up or preserved in the event of a disaster.

15. If the next hop pool for Persistent Chat is pointing to pool A, make and publish topology changes so that the next hop server points to pool C.
    
      - In Topology Builder, change the Persistent Chat pool to point to Pool C as its next hop. To do so, right-click on the Persistent Chat pool, then click the **General** tab, and then type the name of Pool C in **Next Hop Pool**.
    
      - Start services on pool C by running the following cmdlet:
        
            Start-csWindowsService
    
    At this point, the service outage ends for users originally homed on pool A.

16. Export Lync Server Response Group service workflows from pool B owned by pool A for import into pool C by running the following cmdlet:
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:<Pool B FQDN>" -Owner "service:ApplicationServer:<Pool A FQDN>" -FileName "C:\RgsExportPrimaryUpdated.zip" 

17. Import Lync Server Response Group service workflows into pool C from pool B.
    
    You have two options are for importing the Response Group configuration from pool B to pool C. Which option you use depends on whether you want to overwrite the application-level settings of pool C with the application-level settings in pool B.
    
      - If you want to overwrite the Pool C settings, run the **Import-CsRgsConfiguration** cmdlet with the **ReplaceExistingSettings** option:
        
            Import-CsRgsConfiguration -Destination "service:ApplicationServer:<Pool C FQDN>" -FileName "C:\RgsExportPrimary.zip"  -ReplaceExistingRgsSettings
    
      - If you do not want to overwrite the Pool C settings, use the **Import-CsRgsConfiguration** cmdlet without the **ReplaceExistingSettings** option.
        
            Import-CsRgsConfiguration -Destination "service:ApplicationServer:<Pool B FQDN>" -FileName "C:\RgsExportPrimary.zip"
    
    <div>
    

    > [!WARNING]  
    > Keep in mind that if you do not want to overwrite the application-level settings of Pool C with the settings of the backup pool (pool B), pool B’s application-level settings will be lost because the Response Group application can store only one set of application-level settings per pool.

    
    </div>

18. Verify that the Response Group configuration import was successful by running the following cmdlets to display the response groups that have been imported to Pool C.
    
        Get-CsRgsWorkflow -Identity "service:ApplicationServer:<Pool C FQDN>" -ShowAll
         Get-CsRgsQueue -Identity "service:ApplicationServer:<Pool C FQDN>" -ShowAll
        Get-CsRgsAgentGroup -Identity "service:ApplicationServer:<Pool C FQDN>" -ShowAll

19. When the imported configuration has been verified in pool C, remove the response groups owned by the primary pool from pool B. This will minimize the downtime of the response groups.
    
    This step creates a new file with the exported configuration, and then removes the file from pool B.
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:<Pool B FQDN>" -Owner "service:ApplicationServer:<Pool A FQDN>" -FileName "C:\RgsExportPrimaryUpdated.zip" -RemoveExportedConfiguration

20. Move to pool C the Unassigned Number ranges that were moved from pool A to pool B.
    
      - Re-create in pool C all announcements that were re-created from pool A in pool B. If any audio files were used when deploying the announcements to be moved, you will need to use these files to re-create the announcements in pool C. To re-create the announcements in pool C, use the **New-CsAnnouncement** cmdlets, with pool C as the Parent service.
    
      - Retarget to pool C all the unassigned number ranges that were retargeted from pool A to pool B. Run the following cmdlet for every Unassigned Number range that needs to be retargeted:
        
            Set-CsUnassignedNumber -Identity "<Range Name>" -AnnouncementService "<Pool C FQDN>" -AnnouncementName "<New Announcement in pool C>"
    
      - (Optional) Remove from pool B the announcements that were re-created in pool C if they are no longer in use in pool B. To remove announcements, use the **Remove-CsAnnouncement** cmdlet.
        
        <div>
        

        > [!NOTE]  
        > This step is not required for unassigned number ranges that use "Exchange UM" as the announcement service.

        
        </div>

21. Clean up user data of pool A in pool B by running the following cmdlet:
    
        Remove-CsUserStoreBackupData -PoolFqdn <Pool B FQDN> -Verbose

22. Do the following in Topology Builder:
    
      - Unpair pool A and pool B. Pair pool B and pool C. Then remove Pool A from the topology and publish it. To do so:
        
          - In Topology Builder, right-click on Pool B, and then click **Edit Properties**.
        
          - Click **Resiliency** in the left pane.
        
          - In the box below **Associated Backup Pool**, select Pool C. Note that the Associated Backup Pool selection box will initially display pool A, because pool B was previously associated with this pool.
        
          - Select **Automatic failover and failback for Voice**, and then click **OK**.
            
            When you view the details about this pool, the associated pool now appears in the right pane under **Resiliency**.
        
          - In the console tree, right-click pool A, and then click Delete.
        
          - Publish the topology.

23. Run the bootstrapping application on pool C to install the backup service application, and then start the backup service application by running the following from the deployment folder on a local machine in pool C:
    
        Run "%SYSTEMROOT%\Program Files\Microsoft Lync Server 2013\Deployment\Bootstrapper.exe"
        Start-CsWindowsService -name LyncBackup

24. Restart the backup service application on pool B by running the following cmdlets:
    
        Stop-CsWindowsService -name LyncBackup
        Start-CsWindowsService -name LyncBackup

25. If pool C is a Standard Edition (SE) Pool and pool B has CMS, install the CMS database manually on pool C by running the following cmdlet:
    
        Install-CsDatabase -CentralManagementDatabase -SqlServerFqdn <Pool C FQDN> -SqlInstanceName rtc

26. Invoke the backup service to sync old conferencing content from pool B to pool C that was generated before pairing B and C together, and to sync new conferencing content from pool C to pool B that was generated after starting pool C and before B and C were paired together. To do so, run the following cmdlets:
    
        Invoke-CsBackupServiceSync -PoolFqdn <Pool C FQDN>
        Invoke-CsBackupServiceSync -PoolFqdn <Pool B FQDN>

27. For each Survivable Branch Appliance X associated with pool A:
    
      - Shut down SBA X by running the following cmdlet:
        
            Stop-CsWindowsService
    
      - Create a file that contains a list of users homed on SBA X. The list will be needed when the users are moved back to SBA X in step 30. To do so, run the following cmdlet:
        
            Get-CsUser -Filter {RegistrarPool -eq "<SBA X FQDN>"} | Export-Csv d:\sbaxusers.txt
    
      - Force users homed on SBA X to move to pool C by running the following cmdlet:
        
            Get-CsUser -Filter {RegistrarPool -eq "<SBA X FQDN>"} | Move-CsUser -Target <Pool C FQDN> -Force -Verbose
    
      - Update the data of these users by first running the following cmdlets:
        
            Convert-csUserData -InputFile <Data file exported from PoolB> -OutputFile c:\Logs\ExportedUserData.xml -TargetVersionLync2010 
            $a=get-csuser -Filter {RegistrarPool -eq "FQDN of SBA X"} | select SipAddress
            foreach($x in $a) {$x.SipAddress.Substring(4) >> users.txt}
        
        And then run this script:
        
            $users=gc c:\logs\users.txt
            foreach ($user in $users)
            {
            Update-CsUserData -FileName c:\logs\exportedUserDAta.xml -UserFilter $user - 
            }
        
        <div>
        

        > [!NOTE]  
        > A service outage will occur for users who are homed on SBAs that are associated with pool A until these users are moved to pool C.

        
        </div>

28. In Topology Builder, for each SBA X previously associated with Pool A, do the following:
    
      - Change the association to Pool C. To do so, click the branch site, expand the Survivable Branch Appliances or Servers node, and click **Survivable Branch Appliance**. Then select the **Front End pool, User Services Pool** that this Survivable Branch Appliance will connect to as Pool C, and then click **Next**.
    
      - Publish the topology. To do so, in the console tree, right-click the new **Survivable Branch Appliance**, click **Topology**, and then click **Publish**.

29. For each SBA X now associated with pool C:
    
      - Start SBA X by running the following cmdlet on the survivable branch appliance:
        
            Start-CsWindowsService
    
      - Move users who were originally homed on SBA X from pool C to SBA X by running the following cmdlet.
        
            Import-Csv d:\sbaxusers.txt | Move-CsUser -Target <SBA X FQDN> -Force

</div>

</div>

<span> </span>

</div>

</div>

</div>

