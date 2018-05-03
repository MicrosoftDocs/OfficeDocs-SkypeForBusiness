---
title: "Remove Front End pool or Standard Edition server"
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 11/17/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 83c39a36-49a1-4ac6-9cc5-b0e441b1fdec
description: "This topic guides you through the process of removing a Front End pool or a Standard Edition Front End Server. When you remove a Front End pool, you remove each Front End Server that belongs to the pool as a part of the pool removal process. When you remove a Standard Edition Front End Server, you must remove the SQL Store definition from Topology Builder."
---

# Remove Front End pool or Standard Edition server
[]
This topic guides you through the process of removing a Front End pool or a Standard Edition Front End Server. When you remove a Front End pool, you remove each Front End Server that belongs to the pool as a part of the pool removal process. When you remove a Standard Edition Front End Server, you must remove the SQL Store definition from Topology Builder.
  
### To remove a Front End Server pool

1. Open Topology Builder.
    
2. Navigate to the Lync Server 2010 node.
    
3. Expand **Enterprise Edition Front End pools**, expand the Front End pool, right-click the Front End pool that you want to remove, and then click **Delete**.
    
4. Publish the topology, check replication status, and then run the Lync Server Deployment Wizard as needed. 
    
### To remove a Standard Edition Front End server

1. Open Topology Builder.
    
2. Navigate to the Lync Server 2010 node.
    
3. Expand **Standard Edition Front End servers**, right-click the Front End Server that you want to remove, and then click **Delete**.
    
4. Expand **SQL stores**, right-click the SQL Server database that is associated with the Standard Edition Front End Server, and then click **Delete**.
    
    > [!IMPORTANT]
    > You must remove the definition of the collocated SQL Server databases from the Standard Edition Front End Server. 
  
5. Publish the topology, check replication status, and then run the Lync Server Deployment Wizard as needed. 
    

