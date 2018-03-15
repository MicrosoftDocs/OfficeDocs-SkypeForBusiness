---
title: "Publish your topology in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: bfed3829-7a54-4b5c-a7cb-28871acd35e7
description: "Each time you use Topology Builder to build your topology, you must publish the topology to a database in the Central Management store so that the data can be used to deploy Lync Server 2013. Use the following procedure to publish your topology."
---

# Publish your topology in Lync Server 2013
[]
Each time you use Topology Builder to build your topology, you must publish the topology to a database in the Central Management store so that the data can be used to deploy Lync Server 2013. Use the following procedure to publish your topology.
  
### To publish the topology

1. Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.
    
2. In Topology Builder, in the console tree, right-click **Lync 2013**, and then click **Publish Topology**.
    
3. On the **Welcome** page of the wizard, click **Next**.
    
4. On the **Topology Builder found a CMS store** page, click **Next**.
    
5. On the **Create other databases** page, click **Next**.
    
6. When the status indicates that database creation succeeded, do the following:
    
  - To view the log, click **View log**.
    
  - To close the wizard, click **Finish**.
    
    > [!IMPORTANT]
    > If this is a new installation of an Edge Server or Edge pool, you must export the Edge Server configuration from an existing Front End Server, Front End pool, or Standard Edition server. To export the configuration, see [Export your Lync Server 2013 topology and copy it to external media for edge installation](export-your-topology-and-copy-it-to-external-media-for-edge-installation.md). You will import the configuration file from the external media or network share during the setup and deployment phase of the Edge Servers through the Lync Server Deployment Wizard. > Once the Edge Servers are operational and the local configuration management store database is replicating with the internal deployment, subsequent updates to the Lync Server 2013 configuration will be published and replicated to the Edge Servers. 
  

