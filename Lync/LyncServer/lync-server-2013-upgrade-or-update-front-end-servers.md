---
title: 'Lync Server 2013: Upgrade or update Front End Servers'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Upgrade or update Front End Servers
ms:assetid: 20fa39ae-ecfb-4c72-9cc4-8e183d3c752f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204736(v=OCS.15)
ms:contentKeyID: 48183597
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Upgrade or update Front End Servers in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-06-28_

The Front End Servers in an Enterprise Edition pool are organized into *upgrade domains*. These are subsets of Front End Servers in the pool. Upgrade Domains are created automatically by Topology Builder.

When you upgrade servers, you must do so one Upgrade Domain at a time. Bring each Server in one Upgrade Domain down, upgrade it, and then restart it before you move on to another Upgrade Domain. Be sure to keep track of which Upgrade Domains and Servers that you have upgraded so far. Use the following flowchart diagram when upgrading each server.

![42ed59a4-1c26-49f7-ade4-a5a788457ab9](images/JJ204736.42ed59a4-1c26-49f7-ade4-a5a788457ab9(OCS.15).jpg "42ed59a4-1c26-49f7-ade4-a5a788457ab9")

<div>

## To apply an upgrade to the Front End servers in a pool

1.  On a Front End Server in the pool, run the following cmdlet:
    
    **Get-CsPoolUpgradeReadinessState**
    
    If the value of *PoolUpgradeState* is **Busy**, wait for 10 minutes, and then try **Get-CsPoolUpgradeReadinessState** again. If you see **Busy** for at least three consecutive times, after waiting 10 minutes in between each attempt, or if you see any result of **InsufficientActiveFrontEnds** for **PoolUpgradeState,** then there is an issue with the pool. If this pool is paired with another Front End pool in a disaster recovery topology, you should fail the pool over to the backup pool, and then update the servers in this pool. For details, see [Failing over a pool in Lync Server 2013](lync-server-2013-failing-over-a-pool.md).
    
    If the value of *PoolUpgradeState* is **Ready**, go to step 2.

2.  The **Get-CsPoolUpgradeReadinessState** cmdlet also returns information about each upgrade domain in the pool, and about which Front End Servers are in each upgrade domain. If the **ReadyforUpgrade** value is **True** for the upgrade domain that contains the server or servers you want to upgrade, you can safely upgrade those servers now. To do so, do the following:
    
    1.  Stop new connections to the Front End Servers you are going to upgrade by using the `Stop-CsWindowsService -Graceful -Verbose` cmdlet.
        
        <div>
        

        > [!NOTE]  
        > If you are performing these server upgrades during a scheduled server downtime, you can run this cmdlet without the ‘-<STRONG>Graceful</STRONG>‘ parameter, as follows: <STRONG>Stop-CsWindowsService</STRONG>. This will immediately shut down services, without waiting for all existing service requests to be filled.

        
        </div>
    
    2.  Upgrade the servers associated with this the Upgrade Domain.
    
    3.  Restart the servers, and make sure they are accepting new connections.

3.  Repeat Steps 1 and 2 for each other Upgrade Domain in the pool, until all Front End Servers have been upgraded.

</div>

</div>

<span> </span>

</div>

</div>

</div>

