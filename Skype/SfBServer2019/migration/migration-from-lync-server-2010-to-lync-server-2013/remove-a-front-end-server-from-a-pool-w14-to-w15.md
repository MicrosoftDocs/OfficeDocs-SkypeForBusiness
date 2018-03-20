---
title: "Remove a Front End Server from a pool [w14 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 767225c9-7c0b-4d54-a407-d77134ba2abe
description: "The Microsoft Lync Server 2010 Enterprise Edition Front End Server cannot exist as a stand-alone computer. It must be defined as a Front End pool, even if there is only a single computer in the pool."
---

# Remove a Front End Server from a pool [w14 to W15]
[]
The Microsoft Lync Server 2010 Enterprise Edition Front End Server cannot exist as a stand-alone computer. It must be defined as a Front End pool, even if there is only a single computer in the pool.
  
This topic guides you through the process of removing an individual Front End Server from an existing Front End pool. If the Front End Server is the last server in the pool or if you are removing the pool completely, see [Remove Front End pool or Standard Edition server [W14 to W15]](remove-front-end-pool-or-standard-edition-server-w14-to-w15.md). There is no need to remove the individual Front End Servers before you remove the Front End pool. When you remove the pool, you remove each Front End Server.
  
### To remove a Front End Server from a pool

1. Open the Lync Server 2013 Front End Server, open Topology Builder.
    
2. Navigate to the Lync Server 2010 node.
    
3. Expand **Enterprise Edition Front End pools**, expand the Front End pool with the Front End Server that you want to remove, right-click the Front End Server that you want to remove, and then click **Delete**.
    

