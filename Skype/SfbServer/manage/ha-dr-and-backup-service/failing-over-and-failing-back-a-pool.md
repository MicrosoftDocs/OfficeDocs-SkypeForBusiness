---
title: 'Failing over and failing back a pool'
ms.reviewer: 
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "."
---

# Failing over and failing back a pool in Skype for Business Server 

Use the following procedures if a single Front End pool has failed and needs to be failed over, or the pool that experienced the disaster is back online and you need to restore your deployment to regular working status. Also  learn how to fail over and fail back the Edge pool used for Skype for Business federation or XMPP federation, or change the Edge pool associated with a Front End pool.

- [Fail over a Front End pool](#fail-over-a-front-end-pool)
- [Fail back a pool](#fail-back-a-pool)
- [Fail over the Edge pool used for Skype for Business Server federation](#fail-over-the-edge-pool-used-for-skype-for-business-server-federation)
- [Fail over the Edge pool used for XMPP federation in Skype for Business Server](#fail-over-the-edge-pool-used-for-xmpp-federation-in-skype-for-business-server)
- [Fail back the Edge pool used for Skype for Business Server federation or XMPP federation](#fail-back-the-edge-pool-used-for-skype-for-business-server-federation-or-xmpp-federation)
- [Change the Edge pool associated with a Front End pool](#change-the-edge-pool-associated-with-a-front-end-pool)

## Fail over a Front End pool

In this procedure, Datacenter1 contains Pool1, and Pool1 has failed. You are failing over to Pool2 located in Datacenter2.

Most of the work for the pool failover involves failing over the Central Management store, if it is required. This is important because the Central Management store must be functional when the pool’s users are failed over.

Additionally, if a Front End pool fails but the Edge pool at that site is still running, you must know whether the Edge pool uses the failed pool as a next hop pool. If it does, you must change the Edge pool to use a different Front End pool before failing over the failed Front End pool. How you change the next hop setting depends on whether the Edge will use a pool at the same site as the Edge pool, or a different site.

**To set an Edge pool to use a next hop pool at the same site**

1.  Open Topology Builder, right-click the Edge pool that needs to be changed, and click **Edit Properties**.

2.  Click **Next Hop**. From the **Next hop pool:** list, select the pool which will now serve as the next hop pool.

3.  Click **OK**, and then publish the changes.

**To set an Edge pool to use a next hop pool at a different site**

1.  Open a Skype for Business Server Management Shell window and type the following cmdlet:
    
        Set-CsEdgeServer -Identity EdgeServer:<Edge Server pool FQDN> -Registrar Registrar:<NextHopPoolFQDN>

**To fail over a pool in a disaster**

1.  Find which pool is the host for the Central Management Server by typing the following cmdlet on a Front End server in Pool2:
    
        Invoke-CsManagementServerFailover -Whatif
    
    The results of this cmdlet show which pool currently hosts the Central Management Server. In the rest of this procedure, this pool is known as CMS\_Pool.

2.  Use Topology Builder to find the version of Skype for Business Server running on the CMS\_Pool. If it is running Skype for Business Server, use the following cmdlet to find the backup pool of Pool 1.
    
        Get-CsPoolBackupRelationship -PoolFQDN <CMS_Pool FQDN>
    
    Let Backup\_Pool be the backup pool.

3.  Check the status of the Central Management store with the following cmdlet:
    
        Get-CsManagementStoreReplicationStatus -CentralManagementStoreStatus 
    
    This cmdlet should show that both ActiveMasterFQDN and ActiveFileTransferAgents are pointing to the FQDN of CMS\_Pool. If they are empty, the Central Management Server is not available and you must fail it over.

4.  If the Central Management store is not available or if the Central Management store was running on Pool1 (that is, the pool that has failed), you must fail over the Central Management Server before failing over the pool. If you need to fail over the Central Management Server that was hosted on a pool running Skype for Business Server, use the cmdlet in step 5 of this procedure. If you do not need to fail over the Central Management Server, skip to step 7 of this procedure.

5.  To fail over the Central Management store on a pool running Skype for Business Server, do the following:
    
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

7.  Fail over the users from Pool1 to Pool2 by running the following cmdlet in a Skype for Business Server Management Shell window:
    
        Invoke-CsPoolFailover -PoolFQDN <Pool1 FQDN> -DisasterMode -Verbose
    
    Because the steps taken in the previous parts of this procedure to check the Central Management store status are not universal, there is still a chance this cmdlet will fail because the Central Management store is not yet fully failed over. In this case, you must fix the Central Management store based on the error messages that you see, and then run this cmdlet again.
    
    If you see the following error message, then you need to change the Edge pool at this site to use a different pool as its next hop before failing over the pool. For details, see the procedures at the beginning of this topic.
    
        Invoke-CsPoolFailOver : This Front-end pool "pool1.contoso.com" is specified in
        topology as the next hop for the Edge server. Failing over this pool may cause External
        access/Federation/Split-domain/XMPP features to stop working. Please use Topology Builder to
        change the Edge internal next hop setting to point to a different Front-end pool,  before you
        proceed.


## Fail back a pool

After the pool that experienced the disaster is back online (that is, Pool1 in this example), take the following steps to restore your deployment to regular working status.

Note that the failback process takes several minute to complete.  For reference, it is expected to take up to 60 minutes for a pool of 20,000 users.

Fail back the users who were originally homed in Pool1 and have been failed over to Pool2 by typing the following cmdlet:
    
    Invoke-CsPoolFailback -PoolFQDN <Pool1 FQDN> -Verbose

No other steps are necessary. If you failed over the Central Management Server, you can leave it in Pool2.

## Fail over the Edge pool used for Skype for Business Server federation 

If the Edge pool where you have Skype for Business Server federation configured goes down, you must change federation to use a different Edge pool for federation to work.

1.  On a Front End server, open Topology Builder. Expand **Edge pools**, and then right-click the Edge server or Edge server pool that is currently configured for Federation. Select **Edit properties**.

2.  In **Edit Properties** under **General**, clear **Enable federation for this Edge pool (Port 5061)**. Click **OK**.

3.  Expand **Edge pools**, and then right-click the Edge server or Edge server pool that you now want to use for Federation. Select **Edit properties**.

4.  In **Edit Properties** under **General**, select **Enable federation for this Edge pool (Port 5061)**. Click **OK**.

5.  Click **Action**, select **Topology**, select **Publish**. When prompted on **Publish the topology**, click **Next**. When the Publish is finished, click **Finish**.

6.  On the Edge server, open the Skype for Business Server Deployment wizard. Click **Install or Update Skype for Business Server System**, and then click **Setup or Remove Skype for Business Server Components**. Click **Run Again**.

7.  Click **Next**. The summary screen will show actions as they are executed. Once the deployment is done, click **View Log** to view available log files. Click **Finish** to complete the deployment.
    
    If the site containing the failed Edge pool contains Front End Servers that are still running, you must update the Web Conferencing Service and A/V Conferencing Service on these Front End pools to use an Edge pool in a remote site that is still running. 

 ## Fail over the Edge pool used for XMPP federation in Skype for Business Server 

In your organization, there is one Edge pool designated as the pool to use for XMPP federation. If this pool goes down, you must fail over XMPP federation to use a different Edge pool before XMPP federation can work again.

When you first install Edge pools and enable XMPP Federation, you can simplify the disaster recovery process by setting up external DNS SRV records for all of your Edge pools for XMPP federation, instead of just one. Each of these SRV records must have a different priority set. All XMPP federation traffic goes through the pool with the SRV record with the highest priority. 

In the following procedure, EdgePool1 is the pool which originally hosted XMPP federation, and EdgePool2 is the pool which will now host XMPP federation.


### To fail over the Edge pool used for XMPP federation

1.  If you don’t already have another Edge pool deployed (besides the one which is currently down), deploy that pool. 

2.  On each Edge Server in the new Edge pool which will now host XMPP federation (EdgePool2), run the following cmdlet:
    
        Stop-CsWindowsService

3.  Run the following cmdlet to repoint the XMPP federation route to EdgePool2:
    
        Set-CsSite Site2 -XmppExternalFederationRoute EdgeServer2.contoso.com
    
    In this example, Site2 is the site containing the Edge pool which will now host the XMPP federation route, and EdgeServer2.contoso.com is the FQDN of an Edge Server in that pool.

4.  On the external DNS server, change the DNS A record for XMPP federation to point to EdgeServer2.contoso.com.

5.  If you do not already have a DNS SRV record for XMPP federation which resolves to the Edge pool which will now host XMPP federation, you must add it, as in the following example. This SRV record must have a port value of 5269.
    
        _xmpp-server._tcp.contoso.com

6.  Verify that the Edge pool which will now host XMPP federation has port 5269 open externally.

7.  Start the services on all Edge Servers in the Edge pool which will now host XMPP federation:
    
        Start-CsWindowsService


## Fail back the Edge pool used for Skype for Business Server federation or XMPP federation 

After a failed Edge pool that used to host federation has been brought back online, use this procedure to fail back the Skype for Business Server federation route and/or the XMPP federation route to again use this restored Edge pool.

1.  On the Edge pool that is now available again, start the Edge Services.

2.  If you want to fail back the Skype for Business Server federation route to use the restored Edge Server, do the following:
    
      - On a Front End server, open Topology Builder. Expand **Edge pools**, then right click the Edge server or Edge server pool that is currently configured for Federation. Select **Edit properties**.
    
      - In **Edit Properties** under **General**, clear **Enable federation for this Edge pool (Port 5061)**. Click **OK**.
    
      - Expand **Edge pools**, then right click the original Edge server or Edge server pool that you again want to use for Federation. Select **Edit properties**.
    
      - In **Edit Properties** under **General**, select **Enable federation for this Edge pool (Port 5061)**. Click **OK**.
    
      - Click **Action**, select **Topology**, select **Publish**. When prompted on **Publish the topology**, click **Next**. When the Publish is finished, click **Finish**.
    
      - On the Edge server, open the Skype for Business Server Deployment wizard. Click **Install or Update Skype for Business Server System**, then click **Setup or Remove Skype for Business Server Components**. Click **Run Again**.
    
      - Click **Next**. The summary screen will show actions as they are executed. Once the deployment is done, click **View Log** to view available log files. Click **Finish** to complete the deployment.

3.  If you want to fail back the XMPP federation route to use the restored Edge Server, do the following:
    
      - Run the following cmdlet to repoint the XMPP federation route to the Edge pool which will now host XMPP federation (in this example, EdgeServer1):
        
            Set-CsSite Site1 -XmppExternalFederationRoute EdgeServer1.contoso.com
        
        In this example, Site1 is the site containing the Edge pool which will now host the XMPP federation route, and EdgeServer1.contoso.com is the FQDN of an Edge Server in that pool.
    
      - If you do not already have a DNS SRV record for XMPP federation which resolves to the Edge pool which will now host XMPP federation, you must add it, as in the following example. This SRV record must have a port value of 5269.
        
            _xmpp-server._tcp.contoso.com
    
      - On the external DNS server, change the DNS A record for XMPP federation to point to EdgeServer2.contoso.com.
    
      - Verify that the Edge pool which will now host XMPP federation has port 5269 open externally.

4.  If the Front End pools remained running in the site containing the Edge pool that failed and has been restored, you should update the Web Conferencing Service and A/V Conferencing Service on these Front End pools to again use the Edge pools at their local site.

5.  If the Front End pool at the same site as the failed Edge pool also failed, you can now use Invoke–CsPoolFailback to fail back the Front End pool.


## Change the Edge pool associated with a Front End pool

If an Edge pool goes down but the Front End pool at the same site is still running, you will need to set the Front End pool to use an Edge pool at a different site until the failed Edge pool is restored.

1.  In Topology Builder, navigate to the name of the Front End pool you need to change.

2.  Right-click the pool, and then click **Edit Properties**.

3.  In the **Associations** section, under **Associate Edge Pool (for media components)**, use the drop down box to select the Edge pool you want to associate this Front End pool with.

4.  Click **OK**.
