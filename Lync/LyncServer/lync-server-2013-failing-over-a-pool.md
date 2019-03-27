---
title: 'Lync Server 2013: Failing over a pool'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Failing over a pool
ms:assetid: 10b13732-bc80-4cb2-a71c-56b1d6cb5bbb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204678(v=OCS.15)
ms:contentKeyID: 48183432
ms.date: 10/10/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Failing over a pool in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-10-10_

If a single Front End pool has failed and needs to be failed over, use the following procedure. In this procedure, Datacenter1 contains Pool1, and Pool1 has failed. You are failing over to Pool2 located in Datacenter2.

Most of the work for the pool failover involves failing over the Central Management store, if it is required. This is important because the Central Management store must be functional when the pool’s users are failed over.

Additionally, if a Front End pool fails but the Edge pool at that site is still running, you must know whether the Edge pool uses the failed pool as a next hop pool. If it does, you must change the Edge pool to use a different Front End pool before failing over the failed Front End pool. How you change the next hop setting depends on whether the Edge will use a pool at the same site as the Edge pool, or a different site.

**To Set an Edge Pool to Use a Next Hop Pool at the Same Site**

1.  Open Topology Builder, right-click the Edge pool that needs to be changed, and click **Edit Properties**.

2.  Click **Next Hop**. From the **Next hop pool:** list, select the pool which will now serve as the next hop pool.

3.  Click **OK**, and then publish the changes.

**To Set an Edge Pool to Use a Next Hop Pool at a Different Site**

1.  Open a Lync Server Management Shell window and type the following cmdlet:
    
        Set-CsEdgeServer -Identity EdgeServer:<Edge Server pool FQDN> -Registrar Registrar:<NextHopPoolFQDN>

**To Fail Over a Pool in a Disaster**

1.  Find which pool is the host for the Central Management Server by typing the following cmdlet on a Front End server in Pool2:
    
        Invoke-CsManagementServerFailover -Whatif
    
    The results of this cmdlet show which pool currently hosts the Central Management Server. In the rest of this procedure, this pool is known as CMS\_Pool.

2.  Use Topology Builder to find the version of Lync Server running on the CMS\_Pool. If it is running Lync Server 2013, use the following cmdlet to find the backup pool of Pool 1.
    
        Get-CsPoolBackupRelationship -PoolFQDN <CMS_Pool FQDN>
    
    Let Backup\_Pool be the backup pool.

3.  Check the status of the Central Management store with the following cmdlet:
    
        Get-CsManagementStoreReplicationStatus -CentralManagementStoreStatus 
    
    This cmdlet should show that both ActiveMasterFQDN and ActiveFileTransferAgents are pointing to the FQDN of CMS\_Pool. If they are empty, the Central Management Server is not available and you must fail it over.

4.  If the Central Management store is not available or if the Central Management store was running on Pool1 (that is, the pool that has failed), you must fail over the Central Management Server before failing over the pool. If you need to fail over the Central Management Server that was hosted on a pool running Lync Server 2013, use the cmdlet in step 5 of this procedure. If you need to fail over the Central Management Server that was hosted on a pool running Lync Server 2010, use the cmdlet in step 6 of this procedure. If you do not need to fail over the Central Management Server, skip to step 7 of this procedure.

5.  To fail over the Central Management store on a pool running Lync Server 2013, do the following:
    
      - First, check which Back End Server in Backup\_Pool runs the principal instance of the Central Management store by typing the following:
        
            Get-CsDatabaseMirrorState -DatabaseType Centralmgmt -PoolFqdn <Backup_Pool Fqdn>
    
      - If the primary Back End Server in Backup\_Pool is the principal, type:
        
            Invoke-CSManagementServerFailover -BackupSQLServerFqdn <Backup_Pool Primary BackEnd Server FQDN> -BackupSQLInstanceName <Backup_Pool Primary SQL Instance Name>
        
        If the mirror Back End Server in Backup\_Pool is the principal, type:
        
            Invoke-CSManagementServerFailover -MirrorSQLServerFqdn <Backup_Pool Mirror BackEnd Server FQDN> -MirrorSQLInstanceName <Backup_Pool Mirror SQL Instance Name>
    
      - Validate that the Central Management Server failover is complete. Type the following:
        
            Get-CsManagementStoreReplicationStatus -CentralManagementStoreStatus 
        
        Check that both ActiveMasterFQDN and ActiveFileTransferAgents are pointing to the FQDN of Backup\_Pool.
    
      - Finally, check the replica status for all Front End Servers by typing the following:
        
            Get-CsManagementStoreReplicationStatus 
        
        Check that all replicas have a value of True.
        
        Skip to step 7 in this procedure.

6.  Install the Central Management store on the Back End Server of Backup\_Pool.
    
      - First, run the following command:
        
        ``` 
        Install-CsDatabase -CentralManagementDatabase -Clean -SqlServerFqdn <Backup_Pool Back End Server FQDN> -SqlInstanceName rtc  
        ```
    
      - Run the next command on one of the Front End Servers of Backup\_Pool to force the move of the Central Management store:
        
            Move-CsManagementServer -ConfigurationFileName c:\CsConfigurationFile.zip -LisConfigurationFileName c:\CsLisConfigurationFile.zip -Force 
    
      - Validate the move is complete:
        
            Get-CsManagementStoreReplicationStatus -CentralManagementStoreStatus 
        
        Check that both ActiveMasterFQDN and ActiveFileTransferAgents are pointing to the FQDN of Backup\_Pool.
    
      - Check the replica status for all Front End Servers by typing the following:
        
            Get-CsManagementStoreReplicationStatus 
        
        Check that all replicas have a value of True.
    
      - Install the Central Management Server service on the rest of the Front End Servers in Backup\_Pool. To do so, run the following command on all the Front End Servers, except the one you used when forcing the Central Management store move earlier in this procedure:
        
            Bootstrapper /Setup 

7.  Fail over the users from Pool1 to Pool2 by running the following cmdlet in a Lync Server Management Shell window:
    
        Invoke-CsPoolFailover -PoolFQDN <Pool1 FQDN> -DisasterMode -Verbose
    
    Because the steps taken in the previous parts of this procedure to check the Central Management store status are not universal, there is still a chance this cmdlet will fail because the Central Management store is not yet fully failed over. In this case, you must fix the Central Management store based on the error messages that you see, and then run this cmdlet again.
    
    If you see the following error message, then you need to change the Edge pool at this site to use a different pool as its next hop before failing over the pool. For details, see the procedures at the beginning of this topic.
    
        Invoke-CsPoolFailOver : This Front-end pool "pool1.contoso.com" is specified in
        topology as the next hop for the Edge server. Failing over this pool may cause External
        access/Federation/Split-domain/XMPP features to stop working. Please use Topology Builder to
        change the Edge internal next hop setting to point to a different Front-end pool,  before you
        proceed.

</div>

<span> </span>

</div>

</div>

</div>

