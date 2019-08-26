---
title: "Remove Front End pool or Standard Edition server"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "This topic guides you through the process of removing a Front End pool or a Standard Edition Front End Server. When you remove a Front End pool, you remove each Front End Server that belongs to the pool as a part of the pool removal process. When you remove a Standard Edition Front End Server, you must remove the SQL Store definition from Topology Builder."
---

# Remove Front End pool or Standard Edition server

This article guides you through the process of removing a Front End pool or a Standard Edition Front End Server. When you remove a Front End pool, you remove each Front End Server that belongs to the pool as a part of the pool removal process. When you remove a Standard Edition Front End Server, you must remove the SQL Store definition from Topology Builder.
  
## To remove a Front End Server pool

1. Open Topology Builder.
    
2. Navigate to the legacy node.
    
3. Expand **Enterprise Edition Front End pools**, expand the Front End pool, right-click the Front End pool that you want to remove, and then click **Delete**.
    
4. Publish the topology, check replication status, and then run the legacy Deployment Wizard as needed. 
    
## To remove a Standard Edition Front End server

1. Open Topology Builder.
    
2. Navigate to the legacy installs node.
    
3. Expand **Standard Edition Front End servers**, right-click the Front End Server that you want to remove, and then click **Delete**.
    
4. Expand **SQL stores**, right-click the SQL Server database that is associated with the Standard Edition Front End Server, and then click **Delete**.
    
    > [!IMPORTANT]
    > You must remove the definition of the collocated SQL Server databases from the Standard Edition Front End Server. 
  
5. Publish the topology, check replication status, and then run the Deployment Wizard as needed. 
    

