---
title: Plan for high availability and disaster recovery in Skype for Business Server 2015
ms.prod: SKYPEFORBUSINESS
ms.assetid: 3543eb40-54f4-49ef-a058-03aceed4773a
---


# Plan for high availability and disaster recovery in Skype for Business Server 2015
[]Skype for Business Server offers high availability with server pooling, disaster recovery with pool pairing, and several modes of Back End Server high availibility, including AlwaysOn Availability groups, database mirroring, and SQL failover clustering. 
High availability refers to making sure that Skype for Business Server services are available even if one or more servers goes down.Disaster recovery refers to keeping services going in the event of a natural or human-caused disaster, and preserving as much data from before the disaster as possible.
  
    
    

As in previous versions of Lync Server, the main high availability feature for most server roles in Skype for Business Server is server redundancy via pooling. If a server running a certain server role fails, the other servers in the pool running the same role take the load of that server. This applies to Front End Servers, Edge Servers, Mediation Servers, and Directors.
Skype for Business Server also provides disaster recovery options for Front End pools. You can set up two pools in different geographical areas to serve as backups for each other. Then if you have an entire pool or site go down, the backup pool can continue to provide service to users at both sites.
  
    
    

Skype for Business Server also supports four modes of high availability for your Back End Servers: database mirroring, AlwaysOn Availability Groups, AlwaysOn Failover Cluster Instances (FCI), and SQL failover clustering.
> [!NOTE]
> AlwaysOn Availability Groups are not supported with Persistent Chat Servers. 
  
    
    

This section explains these features, and also covers what steps you can take for high availability and disaster recovery for some of your other server roles. 
## See also


#### 


  
    
    
 [Front End Pool high availability and management](front-end-pool-high-availability-and-management.md)
  
    
    
 [Front End pool disaster recovery in Skype for Business Server 2015](front-end-pool-disaster-recovery-in-skype-for-business-server-2015.md)
  
    
    
 [User experience during pool failure in Skype for Business Server 2015](user-experience-during-pool-failure-in-skype-for-business-server-2015.md)
  
    
    
 [Back End Server high availability in Skype for Business Server 2015](back-end-server-high-availability-in-skype-for-business-server-2015.md)
  
    
    
 [File sharing high availability in Skype for Business Server 2015](file-sharing-high-availability-in-skype-for-business-server-2015.md)
