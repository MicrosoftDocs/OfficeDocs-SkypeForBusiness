---
title: 'Lync Server 2013: Topologies and components for Front End Servers, instant messaging, and presence'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Topologies and components for Front End Servers, instant messaging, and presence
ms:assetid: f08ce7a1-d14e-4a54-9771-a82c870658bf
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412996(v=OCS.15)
ms:contentKeyID: 48185763
ms.date: 10/24/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Topologies and components for Front End Servers, instant messaging, and presence in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-10-24_

The only components required for instant messaging (IM) and presence are:

  - Your organization’s Front End Servers or Standard Edition servers. IM and presence capabilities are always enabled on these servers.

  - A load balancer, if you have an Enterprise Edition Front End pool. For more information, see [Load balancing requirements for Lync Server 2013](lync-server-2013-load-balancing-requirements.md).

<div>

## Planning for the Deployment of Front End Pools

In Lync Server 2013, Front End pool architecture has changed, and these changes affect how you should plan and maintain your Front End pools.

We recommend that all your Enterprise Edition Front End pools include at least three Front End Servers. In Lync Server, the architecture of Front End pools uses a distributed systems model, with each user’s data kept on three Front End servers in the pool. For more information about this new architecture, see [Topology changes in Lync Server 2013](lync-server-2013-topology-changes.md).

If you do not want to deploy three Enterprise Edition Front End Servers and want disaster recovery, we recommend you use Lync Server Standard Edition and create two pools with a paired backup relationship. This will provide a disaster recovery solution with only two servers. For more information, on high availability and disaster recovery topologies and features, see [Planning for high availability and disaster recovery in Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md).

</div>

<div>

## Planning for the Management of Front End Pools

For Front End pools, follow the guidelines in this section.

<div>

## Ensuring That Pools are Functional

With the new distributed model for Front End pools, certain numbers of a pool’s servers must be running for the pool to function. There are two loss modes for a pool

  - Routing Group Level quorum loss, caused by not enough replica servers for a particular routing group. A routing group is an aggregation of a set of users homed in the pool. Each routing group has three replicas in the pool: one primary and two secondaries.

  - Pool Level quorum loss, caused when not enough seed servers are running in the pool.

<div>

## Routing Group Level quorum loss

The first time you start a new Front End pool, it is essential that 85% of the servers are up and running, as shown in the following table. If fewer servers are running, the services might be stuck in the starting state and the pool might not start.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Total number of servers in the pool</th>
<th>Number of servers that must be running for the pool to be started the first time</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>2</p></td>
<td><p>1</p></td>
</tr>
<tr class="even">
<td><p>3</p></td>
<td><p>3</p></td>
</tr>
<tr class="odd">
<td><p>4</p></td>
<td><p>3</p></td>
</tr>
<tr class="even">
<td><p>5</p></td>
<td><p>4</p></td>
</tr>
<tr class="odd">
<td><p>6</p></td>
<td><p>5</p></td>
</tr>
<tr class="even">
<td><p>7</p></td>
<td><p>5</p></td>
</tr>
<tr class="odd">
<td><p>8</p></td>
<td><p>6</p></td>
</tr>
<tr class="even">
<td><p>9</p></td>
<td><p>7</p></td>
</tr>
<tr class="odd">
<td><p>10</p></td>
<td><p>8</p></td>
</tr>
<tr class="even">
<td><p>11</p></td>
<td><p>9</p></td>
</tr>
<tr class="odd">
<td><p>12</p></td>
<td><p>10</p></td>
</tr>
</tbody>
</table>


Every subsequent time the pool is started, 85% of the servers should be started (as shown in the preceding table). If this number of servers cannot be started (but enough servers can be started so that you are not at pool-level quorum loss), you can use the **Reset-CsPoolRegistrarState –ResetType QuorumLossRecovery** cmdlet to enable the pool to recover from this routing group level quorum loss and make progress. For more information about how to use this cmdlet, see [Reset-CsPoolRegistrarState](https://docs.microsoft.com/powershell/module/skype/Reset-CsPoolRegistrarState).

<div>


> [!NOTE]  
> Because Lync Server uses the Primary SQL database as Witness, if you shut down the primary database and switch to the Mirror copy, and shut down enough Front End Servers so that not enough are running according to the preceding table, the entire pool will go down. For more information, see <A href="http://go.microsoft.com/fwlink/?linkid=393672">Database Mirroring Witness</A>.



</div>

</div>

<div>

## Pool-level quorum loss

For a Front End pool to function at all, it cannot be in pool-level quorum loss. If the number of servers running falls below the functional level as shown in the following table, the remaining servers in the pool will stop all Lync Server services. Note that the numbers in the following table assume that the Back End Servers in the pool are running.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Total number of Front End Servers in the pool</th>
<th>Number of servers that must be running for pool to be functional</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>2</p></td>
<td><p>1</p></td>
</tr>
<tr class="even">
<td><p>3-4</p></td>
<td><p>Any 2</p></td>
</tr>
<tr class="odd">
<td><p>5-6</p></td>
<td><p>Any 3</p></td>
</tr>
<tr class="even">
<td><p>7</p></td>
<td><p>Any 4</p></td>
</tr>
<tr class="odd">
<td><p>8-9</p></td>
<td><p>Any 4 of the first 7 servers</p></td>
</tr>
<tr class="even">
<td><p>10-12</p></td>
<td><p>Any 5 of the first 9 servers</p></td>
</tr>
</tbody>
</table>


In the preceding table, the “first servers” are the servers which were brought up first, chronologically, when the pool was started for the first time. To determine these servers, you can use the **Get-CsComputer** cmdlet with the **–PoolFqdn** option. This cmdlet will show the servers in the order that they appear in the topology, and the ones at the top of the list are the first servers.

</div>

<div>

## Front End Pools with Two Front End Servers

We do not recommend deploying a Front End pool that contains only two Front End Servers. If you do ever need to deploy such a pool, follow these guidelines:

  - If one of the two Front End Servers goes down, you should try to bring the failed server back up as soon as you can. Similarly, if you need to upgrade one of the two servers, bring it back online as soon as the upgrade is finished.

  - If for some reason you need to bring both servers down at the same time, do the following when the downtime for the pool is finished:
    
      - The best practice is to restart both Front End Servers at the same time.
    
      - If the two servers cannot be restarted at the same time, you should bring them back up in the reverse order of the order they went down.
    
      - If you cannot bring them back up in that order, then use the following cmdlet before bringing the pool back up:.
        
            Reset-CsPoolRegistrarState -ResetType QuorumLossRecovery -PoolFQDN <FQDN>

</div>

<div>

## Additional Steps to Ensure Pools are Functional

You should watch for a couple of other factors to ensure that your Front End pools remain functional.

  - When you move users to the pool for the first time, be sure at least three of the Front End Servers are running.

  - If you establish a pairing relationship between this pool and another pool for disaster recovery purposes, then after establishing that relationship you must be sure this pool has three Front End Servers running simultaneously at some time to properly synchronize data with the backup pool. For more information on pool pairing and disaster recovery features, see [Planning for high availability and disaster recovery in Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md).

</div>

</div>

<div>

## Improving the Reliability of Pool Upgrades

When you need to upgrade or patch the servers in a Front End pool, follow the workflow shown in [Upgrade or update Front End Servers in Lync Server 2013](lync-server-2013-upgrade-or-update-front-end-servers.md), and the following guidelines:

  - When you move from one upgrade domain to another for upgrades (following the workflow at [Upgrade or update Front End Servers in Lync Server 2013](lync-server-2013-upgrade-or-update-front-end-servers.md)), you will use the **Get-CsPoolUpgradeReadinessState** cmdlet and check for Ready state. Adding a 20-minute wait between each upgrade domain after it reaches “Ready” will make the upgrades more reliable. If it becomes **Not Ready** during this 20 minutes, restart the 20-minute timer. Also, you can run the **Get-CsPoolFabricState** cmdlet before and after starting the 20-minute interval and make sure there are no changes to the primaries and secondaries of routing groups.

  - Do not move on to the next upgrade domain if any of the servers in the last patched upgrade domain are stuck or not restarted. This also applies if any of the servers within an upgrade cannot start. Run **Get-CsPoolFabricState** to make sure all of the routing groups have a primary and at least one secondary; this will confirm whether all users have service.

  - If some users have service and others do not, run **Get-CsPoolFabricState** with the –Verbose option to check for routing groups that have missing replicas. Do not restart the entire pool as the first troubleshooting step. For more information on this cmdlet, see [Get-CsPoolFabricState](https://docs.microsoft.com/powershell/module/skype/Get-CsPoolFabricState).

  - Make sure that all instances of the Event Viewer or Performance Monitor windows are closed for windows fabric installs/uninstalls.

</div>

<div>

## Changing a Front End Pool’s Configuration

Whenever you add Front End Servers to a pool, or remove them from the pool, and then publish the new topology, follow these guidelines:

  - After the new topology has been published, you must restart each Front End Server in the pool. Restart them one at a time.

  - If the entire pool has been down during the configuration change, then run the following cmdlet after the new topology is published:
    
        Reset-CsPoolRegistrarState -PoolFQDN <PoolFQDN> -ResetType ServiceReset

If a Front End Server fails and is unlikely to be replaced for a few days or more, remove the server from the topology. Add the new Front End Server to the topology when it is available again.

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

