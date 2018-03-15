---
title: "Deploying paired Front End pools for disaster recovery in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2f12467c-8b90-43e6-831b-a0b096427f17
description: "You can easily deploy the disaster recovery topology of paired Front End pools using Topology Builder."
---

# Deploying paired Front End pools for disaster recovery in Lync Server 2013
[]
You can easily deploy the disaster recovery topology of paired Front End pools using Topology Builder.
  
## To deploy a pair of Front End pools

1. If the pools are new and not yet defined, use Topology Builder to create the pools.
    
2. In Topology Builder, right-click one of the two pools, and then click **Edit Properties**.
    
3. Click **Resiliency** in the left pane, and then select **Associated Backup Pool** in the right pane. 
    
4. In the box below **Associated Backup Pool**, select the pool that you want to pair with this pool. Only existing pools that are not already paired with another pool will be available to select from.
    
     ![Resiliency Dialog](media/Deploy_LyncServer_HADR_ResiliencyDialog.png)
  
5. Select **Automatic failover and failback for Voice**, and then click **OK**.
    
    When you view the details about this pool, the associated pool now appears in the right pane under **Resiliency**. 
    
6. Use Topology Builder to publish the topology.
    
7. If the two pools were not yet deployed, deploy them now and the configuration will be complete. You can skip the final two steps in this procedure.
    
    However, if the pools were already deployed before you defined the paired relationship, you must complete the following two final steps.
    
8. On every Front End Server in both pools, run the following:
    
  ```
  <system drive>\Program Files\Microsoft Lync Server 2013\Deployment\Bootstrapper.exe 
  ```

    This configures other services required for backup pairing to work correctly.
    
9. From a Lync Server Management Shell command prompt, run the following: 
    
  ```
  Start-CsWindowsService -Name LYNCBACKUP
  ```

10. Force the user and conference data of both pools to be synchronized with each other, with the following cmdlets:
    
  ```
  Invoke-CsBackupServiceSync -PoolFqdn <Pool1 FQDN>
  ```

  ```
  Invoke-CsBackupServiceSync -PoolFqdn <Pool2 FQDN>
  ```

    Synchronizing the data may take some time. You can use the following cmdlets to check the status. Make sure that the status in both directions is in steady state.
    
  ```
  Get-CsBackupServiceStatus -PoolFqdn <Pool1 FQDN>
  ```

  ```
  Get-CsBackupServiceStatus -PoolFqdn <Pool2 FQDN>
  ```

> [!NOTE]
> The **Automatic failover and failback for Voice** option and the associated time intervals in Topology Builder apply only to the voice resiliency features that were introduced in Lync Server 2010. Selecting this option does not imply that the pool failover discussed in this document is automatic. Pool failover and failback always require an administrator to manually invoke the failover and failback cmdlets, respectively. 
  

