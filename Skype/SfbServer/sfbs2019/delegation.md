---
title: "Delegation in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 89e76e5c-3cfb-4504-8d0d-7509c8ba9815
description: "The delegation capabilities in Lync are affected by Location-Based Routing in the following manner:"
---

# Delegation in Lync Server 2013
[]
The delegation capabilities in Lync are affected by Location-Based Routing in the following manner:
  
- When a delegate enabled for Location-Based Routing places a call on behalf of a manager, the delegate's voice policy is used to authorize the call and the delegate's site voice routing policy will be used to route the call
    
- For incoming PSTN calls to a manager, the same rules applicable for call forwarding or simultaneously ringing will apply as described in the Call transfers and forwarding and Simultaneous ringing topics.
    
- When a delegate sets a PSTN endpoint as a simultaneous ring target, for an incoming call to the manager, the voice routing policy of the site that is associated to the incoming trunk will be used to route the call to the delegate's PSTN endpoint.
    
- For delegation, it's recommended that the manager and his associated delegates to be usually located in the same network site.
    
## See also

#### 

[Scenarios for Location-Based Routing in Lync Server 2013](scenarios-for-location-based-routing.md)

