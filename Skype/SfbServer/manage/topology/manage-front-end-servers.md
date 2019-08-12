---
title: "Manage Front End Servers in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: ab748733-6bad-4c93-8dda-db8d5271653d
description: "Summary: Learn how to add, remove, patch, or update Front End Servers in Skype for Business Server."
---

# Manage Front End Servers in Skype for Business Server
 
This article explains how to add or remove Front End Servers and how to apply upgrades or patches to Front End Servers.

## Add or remove Front End Servers
  
When you add a Front End Server to a pool, or remove a Front End Server from a pool, you then need to restart the pool. 
  
> [!IMPORTANT]
> When you add or remove a server to the pool in your topology and then publish the updated topology, it will cause all of the servers in the pool to restart at the same time. While the servers are restarting the pool is offline, which will interrupt service for your users connected to that pool. To prevent any interruption of service to users, plan to publish the topology with the new server in the pool during non-business hours. 
  
You can use the following procedure when adding or removing a Front End Server.
  
> [!NOTE]
> If you're adding new servers to the pool, update your new pool servers to be at the same Cumulative Update level as the existing servers in the Pool. 
  
### To add or remove Front End Servers

1. If you are removing any Front End Servers, first stop new connections to those servers. To do so, you can use the following cmdlet:
    
   ```
   Stop-CsWindowsService -Graceful
   ```

2. Open Topology Builder, and add or remove the necessary servers. 
    
3. Publish the topology.
    
    > [!IMPORTANT]
    > When you add or remove a server to the pool in your topology and then publish the updated topology, it will cause all of the servers in the pool to restart at the same time. While the servers are restarting the pool is offline, which will interrupt service for your users connected to that pool. To prevent any interruption of service to users, plan to publish the topology with the new server in the pool during non-business hours. 
  
  > [!NOTE]
> Also, when you add or remove a server to the pool, you must run the Skype for Business Server Deployment Wizard on each computer added or removed, for more information, see [Install Skype for Business Server on servers in the topology](https://docs.microsoft.com/skypeforbusiness/deploy/install/install-skype-for-business-server)
  
4. If you have changed the number of servers in your Front End pool in any of the following ways, then reset the pool with by typing the following cmdlet: Reset-CsPoolRegistrarState -ResetType FullReset -PoolFqdn 
    
   ```
    Reset-CsPoolRegistrarState -ResetType FullReset -PoolFqdn  <PoolFQDN>
   ```

     - 2 to any
    
     - Any to 2
    
     - 3 to any
    
     - Any to 3
    
5. Restart the pool by typing the following cmdlet
    
   ```
   Start-CsPool
   ```

## Patch or update Front End Servers

When you patch the servers in a Front End pool, you do so one server at a time. 
  
### To apply an upgrade to the Front End servers in a pool

1. Type the following cmdlet:
    
   ```
   Get-CsPoolFabricState -PoolFqdn <PoolFQDN>
   ```

     If this cmdlet shows any missing replicas, then run the following cmdlet to recover the pool before you apply any patches.
    
   ```
   Reset-CsPoolRegistrarState -ResetType QuorumLossRecovery
   ```

2. On the first server you want to patch, run the following cmdlet:
    
   ```
   Invoke-CsComputerFailOver -ComputerName <Front End Server to be patched>
   ```

    This cmdlet moves all services to other Front End Servers in the pool, and takes this server offline.
    
3. Apply the upgrade or patch to this server.
    
4. On the upgraded server, run the following cmdlet:
    
   ```
   Invoke-CsComputerFailBack -ComputerName <Front End Server to be patched>
   ```

    The server is returned to service.
    
5. Repeat Steps 2-4 for each server that needs to be upgraded.
    
