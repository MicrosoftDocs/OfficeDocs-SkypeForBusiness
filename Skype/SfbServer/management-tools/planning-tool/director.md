---
title: Director planning tool
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 4/8/2016
audience: ITPro
ms.topic: article
f1.keywords:
- ms.lync.plan.Director
- ms.lync.plan.Director
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.assetid: 02795b46-21ec-4a85-9890-959c91d97df3
description: "A Director is a server running Skype for Business Server 2015 communications software that can authenticate user requests but doesn't home any user accounts."
---

# Director planning tool
 
A Director is a server running Skype for Business Server 2015 communications software that can authenticate user requests, but doesn't home any user accounts. 
  
This role is optional, you would choose to deploy a Director in the following two scenarios:
  
- If you enable access by guest users by deploying Edge Servers, you should also deploy a Director. In this scenario, the Director authenticates the guests, and then passes their traffic on to internal servers. When a Director is used to authenticate guests, it relieves Front End pool servers from the overhead of authenticating these users. It also helps insulate internal Front End pools from malicious traffic such as denial-of-service attacks. If the network is flooded with invalid external traffic in such an attack, this traffic ends at the Director.
    
- If you deploy multiple Front End pools at a central site, by adding a Director to that site you can streamline authentication requests and improve performance. In this scenario, all requests go first to the Director, which then routes them to the correct Front End pool.
    

