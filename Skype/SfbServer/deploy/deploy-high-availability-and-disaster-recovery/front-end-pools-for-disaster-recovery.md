---
title: "Deploy paired Front End pools for disaster recovery in Skype for Business Server"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 2f12467c-8b90-43e6-831b-a0b096427f17
description: "You may decide to use paired Front End pools to provide disaster recovery protection, but doing so is not a requirement."
---

# Deploy paired Front End pools for disaster recovery in Skype for Business Server
 
You may decide to use paired Front End pools to provide disaster recovery protection, but doing so is not a requirement.
  
You can easily deploy the disaster recovery topology of paired Front End pools using Topology Builder. 
  
## To deploy a pair of Front End pools

1. If the pools are new and not yet defined, use Topology Builder to create the pools.
    
2. In Topology Builder, right-click one of the two pools, and then click **Edit Properties**.
    
3. Click **Resiliency** in the left pane, and then select **Associated Backup Pool** in the right pane.
    
4. In the box below **Associated Backup Pool**, select the pool that you want to pair with this pool. Only existing pools that are not already paired with another pool will be available to select from.
    
5. Select **Automatic failover and failback for Voice**, and then click **OK**.
    
    When you view the details about this pool, the associated pool now appears in the right pane under **Resiliency**. 
    
6. Use Topology Builder to publish the topology.
    
7. If the two pools were not yet deployed, deploy them now and the configuration will be complete. You can skip the final steps in this procedure.
    
    However, if the pools were already deployed before you defined the paired relationship, you must complete the following final steps.
    
8. On every Front End Server in both pools, run the following:
    
   ```powershell
   <system drive>\Program Files\Skype for Business Server 2019\Deployment\Bootstrapper.exe 
   ```

    This configures other services required for backup pairing to work correctly.
    
9. Once Bootstrapper finishes installing the required components for backup pairing on every Front end Server in both pools, please be sure to re-apply any existing Cumulative Update that was previously applied on these Front End Servers in both pools and then continue with the next step.

10. From a Skype for Business Server Management Shell command prompt, run the following: 
    
   ```powershell
   Start-CsWindowsService -Name LYNCBACKUP
   ```

11. Force the user and conference data of both pools to be synchronized with each other with the following cmdlets:
    
    ```powershell
    Invoke-CsBackupServiceSync -PoolFqdn <Pool1 FQDN>
    ```

    ```powershell
    Invoke-CsBackupServiceSync -PoolFqdn <Pool2 FQDN>
    ```

    Synchronizing the data may take some time. You can use the following cmdlets to check the status. Make sure that the status in both directions is in steady state.
    
    ```powershell
    Get-CsBackupServiceStatus -PoolFqdn <Pool1 FQDN>
    ```

    ```powershell
    Get-CsBackupServiceStatus -PoolFqdn <Pool2 FQDN>
    ```

> [!NOTE]
> The **Automatic failover and failback for Voice** option and the associated time intervals in Topology Builder apply only to the voice resiliency features that were introduced in Lync Server. Selecting this option does not imply that the pool failover discussed in this document is automatic. Pool failover and failback always require an administrator to manually invoke the failover and failback cmdlets, respectively.
  
## See also

[Front End pool disaster recovery in Skype for Business Server](../../plan-your-deployment/high-availability-and-disaster-recovery/disaster-recovery.md)
