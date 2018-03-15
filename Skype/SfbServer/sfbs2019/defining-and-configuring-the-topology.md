---
title: "Defining and configuring the topology in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 51d1601e-4f83-48d4-ad08-3b4d5e2003aa
description: "You define and configure your topology by using Topology Builder. Topology Builder does not require you to be a member of the local Administrators group or a privileged domain group (such as Domain Admins). You can define your topology as a standard user. When you start Topology Builder on first use and subsequent edit sessions, you are prompted for the location where you want Topology Builder to load the current configuration document. The choices are the following:"
---

# Defining and configuring the topology in Lync Server 2013
[]
You define and configure your topology by using Topology Builder. Topology Builder does not require you to be a member of the local Administrators group or a privileged domain group (such as Domain Admins). You can define your topology as a standard user. When you start Topology Builder on first use and subsequent edit sessions, you are prompted for the location where you want Topology Builder to load the current configuration document. The choices are the following:
  
- Download topology from existing deployment
    
- Open topology from a local file
    
- New topology
    
If you have already defined a topology and have established the Central Management store, you should choose to download a topology from an existing deployment. Topology Builder will read the database and retrieve the current definition. If you have an existing Central Management store, you should always choose this option.
  
If you have not established a Central Management store and want to edit a previously saved configuration, you should choose to open the topology from a local file. The file that you will open would be the configuration file that was saved in a previous session. You can use this option to edit the previously saved topology.
  
> [!CAUTION]
> If you already have a published topology, you should not load a local configuration file. You should choose to download the topology from an existing deployment. 
  
Choose to create a new topology, if you want to create a new Topology Builder configuration. A previously saved design is not overwritten unless you choose to save it as the same file that you created in an earlier design session.
  
In each of these options, you will be prompted for a location to store the Topology Builder configuration file. The location for the file could be a local location, a shared location on an established file share, or removable media.
  
## In this section

- [Define and configure a topology in Topology Builder for Lync Server 2013](define-and-configure-a-topology-in-topology-builder.md)
    
- [Define and configure a Front End pool or Standard Edition server in Lync Server 2013](define-and-configure-a-front-end-pool-or-standard-edition-server.md)
    
- [Deploying paired Front End pools for disaster recovery in Lync Server 2013](deploying-paired-front-end-pools-for-disaster-recovery.md)
    
- [Deploying SQL mirroring for Back End Server high availability in Lync Server 2013](deploying-sql-mirroring-for-back-end-server-high-availability.md)
    
- [Edit or configure simple URLs in Lync Server 2013](edit-or-configure-simple-urls.md)
    
- [Select the Central Management Server in Lync Server 2013](select-the-central-management-server.md)
    

