---
title: "Define Persistent Chat FQDN"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 3/27/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.AddPersistentChatFqdnPage
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e0123fa6-008b-430e-a68b-61f0cc3fb12e
description: "You create a new Persistent Chat Server or Persistent Chat Server pool using the Define New Persistent Chat Pool wizard. Select either a Multiple computer pool or a Single computer pool. If you select a single computer pool and later need a multiple computer pool, you will need to remove the single computer pool and then define a multiple computer pool."
---

# Define Persistent Chat FQDN
 
You create a new Persistent Chat Server or Persistent Chat Server pool using the **Define New Persistent Chat Pool** wizard. Select either a **Multiple computer pool** or a **Single computer pool**. If you select a single computer pool and later need a multiple computer pool, you will need to remove the single computer pool and then define a multiple computer pool.
  
You must also define a **Pool FQDN** for the Persistent Chat Server or Persistent Chat Server pool. The pool fully qualified domain name (FQDN) for a single computer pool must be the same as the FQDN of the computer that makes up the single server pool. For a multiple computer pool, the FQDN must be the name you choose to represent this multiple computer pool and is defined in DNS by a host A (and AAAA if IPv6 is being used) record.
  
## See also

[Plan for Persistent Chat Server in Skype for Business Server 2015](../../plan-your-deployment/persistent-chat-server/persistent-chat-server.md)
  
[Add Persistent Chat Server to your Skype for Business Server 2015 topology](../../deploy/deploy-persistent-chat-server/add-persistent-chat-server.md)
