---
title: Add Persistent Chat File Store
ms.prod: SKYPEFORBUSINESS
ms.assetid: e1068706-ff61-4a98-8e51-4202111d936a
---


# Add Persistent Chat File Store
[]
You must specify a file share to be used as the file store for the Standard Edition server or Enterprise Edition Front End pool. You can use an existing file share for the file store or you can specify a new file share by specifying the fully qualified domain name (FQDN) of the file server on which the file share is to be located and a folder name for the new file share.
  
    
    


> [!IMPORTANT]
> The file share for Skype for Business Server cannot be located on the Enterprise Edition Front End Server, but can be located on a Standard Edition server. > You can define the file share in Topology Builder before you create the file share, but you must create the file share in the defined location you define before you publish the topology. > When you add a Persistent Chat Server or Persistent Chat Server pool to your topology, Topology Builder must be able to set up the file store and configure discretionary access control lists (DACLs) on the file share to be used for the file store. This requires that, when you run Topology Builder to publish the new topology, you are logged on with an account that has full control permissions (read/write/modify) for the file share. 
  
    
    



  
    
    


## See also


#### 


  
    
    
 [Plan for Persistent Chat Server in Skype for Business Server 2015](plan-for-persistent-chat-server-in-skype-for-business-server-2015.md)
  
    
    
 [Add Persistent Chat Server to your Skype for Business Server 2015 topology](add-persistent-chat-server-to-your-skype-for-business-server-2015-topology.md)
  
    
    
 [Hardware and software requirements for Persistent Chat Server in Skype for Business Server 2015](hardware-and-software-requirements-for-persistent-chat-server-in-skype-for-busin.md)
  
    
    
 [Server requirements for Skype for Business Server 2015](server-requirements-for-skype-for-business-server-2015.md)
  
    
    
 [Topology Basics for Skype for Business Server 2015](topology-basics-for-skype-for-business-server-2015.md)
