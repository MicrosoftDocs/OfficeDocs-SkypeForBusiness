---
title: "Incoming calls in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 65b9c1b4-6af7-4527-8c33-22c4442bd209
description: "The routing of incoming calls to users enabled for Location-Based Routing depends on the location of the user's endpoint. The routing of incoming calls is affected in the following way. If a user has an incoming call to an endpoint located in a Location-Based Routing enabled network site, and the endpoint is located in the same network site as the PSTN gateway, the call will be routed. If a user has an incoming call to an endpoint located in a Location-Based Routing enabled network site, and the endpoint is located in a different network site than the PSTN gateway, the call will not be routed. When a user has no endpoints located in the same network site as the PSTN gateway where the incoming call is originating from, the incoming call will be routed directly to the user's voicemail and a missed call notification will be sent to the called party."
---

# Incoming calls in Lync Server 2013
[]
The routing of incoming calls to users enabled for Location-Based Routing depends on the location of the user's endpoint. The routing of incoming calls is affected in the following way. If a user has an incoming call to an endpoint located in a Location-Based Routing enabled network site, and the endpoint is located in the same network site as the PSTN gateway, the call will be routed. If a user has an incoming call to an endpoint located in a Location-Based Routing enabled network site, and the endpoint is located in a different network site than the PSTN gateway, the call will not be routed. When a user has no endpoints located in the same network site as the PSTN gateway where the incoming call is originating from, the incoming call will be routed directly to the user's voicemail and a missed call notification will be sent to the called party.
  
The call forwarding settings of a user that is enabled for Location-Based Routing will continue to be enforced, however, calls forwarded will be subject to Location-Based Routing restrictions of the user.
  
The following table illustrates how Location-Based Routing affects the routing of inbound calls depending on the location of the callee's endpoint. The network site of the PSTN gateway is enabled for Location-Based Routing, and Location-Based Routing only permits routing of PSTN calls to endpoints within the same network site.
  
**Callee receiving an inbound call from the PSTN**

||**Callee's endpoint located in the same network site as PSTN gateway**|**Callee's endpoint not located in the same network site as PSTN gateway**|**Callee's endpoint located in unknown network site or not enabled for Location-Based Routing**|
|:-----|:-----|:-----|:-----|
|Routing of inbound PSTN call  <br/> |Incoming call is routed to callee's endpoints  <br/> |Incoming call is not routed to callee's endpoints  <br/> |Incoming call is not routed to callee's endpoints  <br/> |
   
## See also

#### 

[Scenarios for Location-Based Routing in Lync Server 2013](scenarios-for-location-based-routing.md)

