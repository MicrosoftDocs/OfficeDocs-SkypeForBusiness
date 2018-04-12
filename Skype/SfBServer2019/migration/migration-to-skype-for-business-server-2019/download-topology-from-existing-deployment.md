---
title: "Download topology from existing deployment"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e39065a2-d4b0-4f27-8c49-f56be78fa55b
description: "When creating a Lync Server 2013 pool, you will use the Central Management Store that is associated with Lync Server 2010. When you start Topology Builder on first use and subsequent edit sessions, you are prompted for the location where you want Topology Builder to load the current configuration document. Because you already have a Lync Server 2010 topology defined and have established the Central Management store, you should choose to download a topology from an existing deployment. Topology Builder will read the database and retrieve the current definition."
---

# Download topology from existing deployment
[]
When creating a Lync Server 2013 pool, you will use the Central Management Store that is associated with Lync Server 2010. When you start Topology Builder on first use and subsequent edit sessions, you are prompted for the location where you want Topology Builder to load the current configuration document. Because you already have a Lync Server 2010 topology defined and have established the Central Management store, you should choose to download a topology from an existing deployment. Topology Builder will read the database and retrieve the current definition. 
  
### To download a topology from an existing deployment

1. Open the **Lync Server Deployment Wizard**.
    
2. From the **Lync Server 2013 - Deployment Wizard** page, click **Install Administrative Tools**.
    
3. Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.
    
4. Select **Download Topology from existing deployment**.
    
     ![Deployment Wizard Topology Builder settings](../../media/migration_lyncserver_2013_downloadtopology.JPG)
  
5. Choose a file name and save the topology with the default .tbxml file type.
    
6. Expand the Lync Server node, as shown, to reveal the various server roles in the deployment.
    
     ![Topology Builder server role general properties](../../media/migration_lyncserver_2013_tb_prepool_deployment.JPG)
  

