---
title: "Define Persistent Chat FQDN"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
f1_keywords:
- ms.lync.tb.AddPersistentChatFqdnPage
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e0123fa6-008b-430e-a68b-61f0cc3fb12e
description: "You create a new Persistent Chat Server or Persistent Chat Server pool using the Define New Persistent Chat Pool wizard. Select either a Multiple computer pool or a Single computer pool. If you select a single computer pool and later need a multiple computer poo, you will need to remove the single computer pool and then define a multiple computer pool."
---

# Define Persistent Chat FQDN
[]
You create a new Persistent Chat Server or Persistent Chat Server pool using the **Define New Persistent Chat Pool** wizard. Select either a **Multiple computer pool** or a **Single computer pool**. If you select a single computer pool and later need a multiple computer poo, you will need to remove the single computer pool and then define a multiple computer pool.
  
You must also define a **Pool FQDN** for the Persistent Chat Server or Persistent Chat Server pool. The pool fully qualified domain name (FQDN) for a single computer pool must be the same as the FQDN of the computer that makes up the single server pool. For a multiple computer pool, the FQDN must be the name you choose to represent this multiple computer pool and is defined in DNS by a host A (and AAAA if IPv6 is being used) record. 
  
![Add FQDN for chat pool dialog box](media/Define_New_Persistent_Chat_Pool.jpg)
  
## See also

#### 

[Add Persistent Chat Server to the topology in Lync Server 2013](add-persistent-chat-server-to-the-topology.md)

