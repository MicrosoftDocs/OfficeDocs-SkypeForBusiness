---
title: Add or remove a Front End Server in Skype for Business Server 2015
ms.prod: SKYPEFORBUSINESS
ms.assetid: ab748733-6bad-4c93-8dda-db8d5271653d
---


# Add or remove a Front End Server in Skype for Business Server 2015
[] **Summary:** Learn how to add or remove Front End Servers in Skype for Business Server.
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


