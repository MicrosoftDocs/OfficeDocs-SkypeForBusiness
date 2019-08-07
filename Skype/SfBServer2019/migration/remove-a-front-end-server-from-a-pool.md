---
title: "Remove a Front End Server from a pool"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "The Front End Server cannot exist as a stand-alone computer. It must be defined as a Front End pool, even if there is only a single computer in the pool."
---

# Remove a Front End Server from a pool

The Front End Server cannot exist as a stand-alone computer. It must be defined as a Front End pool, even if there is only a single computer in the pool.
  
This topic guides you through the process of removing an individual Front End Server from an existing Front End pool. If the Front End Server is the last server in the pool or if you are removing the pool completely, see [Remove Front End pool or Standard Edition server](remove-front-end-pool-or-standard-edition-server.md). There is no need to remove the individual Front End Servers before you remove the Front End pool. When you remove the pool, you remove each Front End Server.
  
### To remove a Front End Server from a pool

1. On the Skype for Business Server 2019 Front End Server, open Topology Builder.
    
2. Navigate to the legacy install node.
    
3. Expand **Enterprise Edition Front End pools**, expand the Front End pool with the Front End Server that you want to remove, right-click the Front End Server that you want to remove, and then click **Delete**.
    

