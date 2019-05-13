---
title: 'Lync Server 2013: Deploying paired Front End pools for disaster recovery'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Deploying paired Front End pools for disaster recovery
ms:assetid: 2f12467c-8b90-43e6-831b-a0b096427f17
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204773(v=OCS.15)
ms:contentKeyID: 48183727
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deploying paired Front End pools for disaster recovery in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

You can easily deploy the disaster recovery topology of paired Front End pools using Topology Builder.

<div>

## To deploy a pair of Front End pools

1.  If the pools are new and not yet defined, use Topology Builder to create the pools.

2.  In Topology Builder, right-click one of the two pools, and then click **Edit Properties**.

3.  Click **Resiliency** in the left pane, and then select **Associated Backup Pool** in the right pane.

4.  In the box below **Associated Backup Pool**, select the pool that you want to pair with this pool. Only existing pools that are not already paired with another pool will be available to select from.
    
    ![36080581-db76-497d-bf9e-f02b39574d0e](images/JJ204773.36080581-db76-497d-bf9e-f02b39574d0e(OCS.15).png "36080581-db76-497d-bf9e-f02b39574d0e")  

5.  Select **Automatic failover and failback for Voice**, and then click **OK**.
    
    When you view the details about this pool, the associated pool now appears in the right pane under **Resiliency**.

6.  Use Topology Builder to publish the topology.

7.  If the two pools were not yet deployed, deploy them now and the configuration will be complete. You can skip the final two steps in this procedure.
    
    However, if the pools were already deployed before you defined the paired relationship, you must complete the following two final steps.

8.  On every Front End Server in both pools, run the following:
    
        <system drive>\Program Files\Microsoft Lync Server 2013\Deployment\Bootstrapper.exe 
    
    This configures other services required for backup pairing to work correctly.

9.  From a Lync Server Management Shell command prompt, run the following:
    
        Start-CsWindowsService -Name LYNCBACKUP

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

<div class="">


> [!NOTE]  
> The <STRONG>Automatic failover and failback for Voice</STRONG> option and the associated time intervals in Topology Builder apply only to the voice resiliency features that were introduced in Lync Server 2010. Selecting this option does not imply that the pool failover discussed in this document is automatic. Pool failover and failback always require an administrator to manually invoke the failover and failback cmdlets, respectively.



</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

