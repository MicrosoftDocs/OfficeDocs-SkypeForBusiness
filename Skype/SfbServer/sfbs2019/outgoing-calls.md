---
title: "Outgoing calls in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 885ffe6f-cd51-4f21-8d4f-a1ff8d818858
description: "The routing of outbound calls of users enabled for Location-Based Routing is affected by the network location of the user's endpoint. The following table illustrates how Location-Based Routing affects the routing of outbound calls depending on the location of the caller's endpoint."
---

# Outgoing calls in Lync Server 2013
[]
The routing of outbound calls of users enabled for Location-Based Routing is affected by the network location of the user's endpoint. The following table illustrates how Location-Based Routing affects the routing of outbound calls depending on the location of the caller's endpoint. 
  
**Caller placing an outbound call to the PSTN**

||**User endpoint located in a network site enabled for Location-Based Routing**|**User endpoint located in unknown network site or not enabled for Location-Based Routing**|
|:-----|:-----|:-----|
|Authorization of outbound calls  <br/> |Call is authorized based on user's voice policy  <br/> |Call is authorized based on user's voice policy  <br/> |
|Routing of outbound call  <br/> |Call is routed according to the network site's voice routing policy  <br/> |Call is routed according to user's voice policy and only through trunks not enabled for Location-Based Routing (if available)  <br/> |
   
## See also

#### 

[Scenarios for Location-Based Routing in Lync Server 2013](scenarios-for-location-based-routing.md)

