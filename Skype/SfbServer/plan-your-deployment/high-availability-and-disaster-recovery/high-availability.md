---
title: "Front End Pool high availability and management"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 965041b7-3136-49f2-89c1-8b30417cb8ea
description: "Learn about Front End pool management in Skype for Business Server, including managing pools, quorum loss, and special steps for pools with only two Front End Servers."
---

# Front End Pool high availability and management
 
Learn about Front End pool management in Skype for Business Server, including managing pools, quorum loss, and special steps for pools with only two Front End Servers.
  
In Skype for Business Server, the architecture of Front End pools uses a distributed systems model, with each user's data kept on as many as three Front End servers in the pool. We recommend that all your Enterprise Edition Front End pools include at least three Front End Servers. 
  
## Planning for the management of Front End pools

 Skype for Business Server uses a distributed systems model based on Windows Fabric. In this model, important data for each user and conference is stored on three Front End Servers in a Front End pool. These three servers storing a certain set of data are calledreplicas.
  
With the distributed model for Front End pools, a certain numbers of a pool's servers must be running for the pool to function. There are two loss modes for a pool.
  
- Routing Group Level quorum loss, caused by not enough replica servers for a particular routing group. A routing group is a set of users homed in the pool. Each routing group has three replicas in the pool: one primary replica and two secondary replicas.
    
- Pool Level quorum loss, caused when not enough seed servers are running in the pool. 
    
### Routing Group Level quorum loss

The first time you start a new Front End pool, it is essential that 85% of the servers are up and running, as shown in the following table. If fewer servers are running, the services might be stuck in the starting state and the pool might not start.
  
|Total number of servers in the pool  <br/> |Number of servers that must be running for the pool to be started the first time  <br/> |
|:-----|:-----|
|2  <br/> |1  <br/> |
|3  <br/> |3  <br/> |
|4  <br/> |3  <br/> |
|5  <br/> |4  <br/> |
|6  <br/> |5  <br/> |
|7  <br/> |5  <br/> |
|8  <br/> |6  <br/> |
|9  <br/> |7  <br/> |
|10  <br/> |8  <br/> |
|11  <br/> |9  <br/> |
|12  <br/> |10  <br/> |
   
Every subsequent time the pool is started, 85% of the servers should be started (as shown in the preceding table). If this number of servers cannot be started (but enough servers can be started so that you are not at pool-level quorum loss), you can use the  `Reset-CsPoolRegistrarState -ResetType QuorumLossRecovery` cmdlet to enable the pool to recover from this routing group level quorum loss and make progress. For more information about how to use this cmdlet, see <link Reset-CsPoolRegistrarState>.
  
> [!NOTE]
> In pools with an even number of servers, Skype for Business Server uses the Primary SQL database as Witness. In a pool like this, if you shut down the primary database and switch to the Mirror copy, and shut down enough Front End servers so that not enough are running according to the preceding table, the entire pool will go down. For more information, see [Database Mirroring Witness](https://go.microsoft.com/fwlink/?LinkId=393672). 
  
#### Pool-level quorum loss

For a Front End pool to function at all, it cannot be in pool-level quorum loss. If the number of servers running falls below the functional level as shown in the following table, the remaining servers in the pool will stop all Skype for Business Server services. Note that the numbers in the following table assume that the Back End Servers in the pool are running.
  
|Total number of Front End Servers in the pool  <br/> |Number of servers that must be running for pool to be functional  <br/> |
|:-----|:-----|
|2  <br/> |1  <br/> |
|3-4  <br/> |Any 2  <br/> |
|5-6  <br/> |Any 3  <br/> |
|7  <br/> |Any 4  <br/> |
|8-9  <br/> |Any 4 of the first 7 servers  <br/> |
|10-12  <br/> |Any 5 of the first 9 servers  <br/> |
   
In the preceding table, the "first servers" are the servers which were brought up first, chronologically, when the pool was started for the first time. To determine these servers, you can use the  `Get-CsComputer` cmdlet with the ` -PoolFqdn` option. This cmdlet will show the servers in the order that they appear in the topology, and the ones at the top of the list are the first servers.
  
#### Additional steps to ensure pools are functional

You should watch for a couple of other factors to ensure that your Front End pools remain functional.
  
- When you move users to the pool for the first time, be sure at least three of the Front End Servers are running.
    
- If you establish a pairing relationship between this pool and another pool for disaster recovery purposes, then after establishing that relationship you must be sure this pool has three Front End servers running simultaneously at some time to properly synchronize data with the backup pool. For more information on pool pairing and disaster recovery features, see [Plan for high availability and disaster recovery in Skype for Business Server](high-availability-and-disaster-recovery.md). 
    
## Front End pool with two Front End servers

We do not recommend deploying a Front End pool that contains only two Front End Servers. This small pool will not provide a robust high-availability solution like a larger pool would, and needs extra care in managing. Additionally, if the Back End Server of a two-server pool went down, the whole pool itself would likely soon go down as well. If you want to deploy just one or two servers running Skype for Business Server, we recommend you deploy them as Standard Edition servers.
  
If you do ever need to deploy a pool with two Front End Servers, follow these guidelines:
  
- If one of the two Front End Servers goes down, you should try to bring the failed server back up as soon as you can. Similarly, if you need to upgrade one of the two servers, bring it back online as soon as the upgrade is finished.
    
- If for some reason you need to bring both servers down at the same time, do the following when the downtime for the pool is finished:
    
  - The best practice is to restart both Front End Servers at the same time. 
    
  - If the two servers cannot be restarted at the same time, you should bring them back up in the reverse order of the order they went down.
    
  - If you cannot bring them back up in that order, then use the following cmdlet before bringing the pool back up:  `Reset-CsPoolRegistrarState -ResetType QuorumLossRecovery -PoolFQDN <FQDN>`
    
## Front End pool configuration failures and changes

If a Front End server fails and is unlikely to be replaced for a few days or more, remove the server from the topology. Add the new Front End server to the topology when it is available again.
  
Whenever you make a configuration change to a Front End pool, such as adding or removing servers, you must follow these guidelines:
  
- After the new topology has been published, you must restart each Front End server in the pool. Restart them one at a time.
    
- If the entire pool has been down during the configuration change, then run the following cmdlet after the new topology is published:  `Reset-CsPoolRegistrarState -PoolFQDN <PoolFQDN> -ResetType ServiceReset`
    

