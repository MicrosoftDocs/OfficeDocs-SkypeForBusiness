---
title: "Coexistence considerations"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9d1a3c0f-492a-4e37-bc2f-63509e328785
description: "After migration, only a Lync Server 2013, Persistent Chat Server pool will exist, and you can decommission your legacy deployment."
---

# Coexistence considerations
[]
After migration, only a Lync Server 2013, Persistent Chat Server pool will exist, and you can decommission your legacy deployment.
  
Before migration completes and before you have decommissioned your current Group Chat Server deployment completely, you may have any of the following deployments:
  
- Lync Server 2013, Persistent Chat Server pool, which must be homed on a Lync Server 2013 pool.
    
- Lync Server 2010, Group Chat pool, which must be homed on a Lync Server 2010 pool.
    
- Office Communications Server 2007 R2 Group Chat pool, which must be homed on an Office Communications Server 2007 R2 pool.
    
These deployments can exist side by side. However the categories, rooms, and add-ins in one deployment do not interact with those in the accompanying deployment.
  
Using manual configuration, a legacy client (Group Chat client) can connect to one pool at a time for Office Communications Server 2007 R2, Lync Server 2010, Group Chat, or Lync Server 2013.
  
The Lync 2013 (client) can interact only with the Lync Server 2013, Persistent Chat Server pool, not with legacy Group Chat Server pools. To use Persistent Chat in a Lync 2013 (client), the user must be homed on Lync 2013 and enabled by policy.
  

