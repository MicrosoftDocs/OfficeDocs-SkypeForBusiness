---
title: "Location-Based Routing and consultative call transfers in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b12460c2-36c8-481f-b867-fe10dc1c0bdf
description: "In addition to enforcing Location-Based Routing to Lync meetings, the Location-Based Routing Conferencing application enforces Location-Based Routing restrictions on consultative call transfers that egress to PSTN endpoints. A consultative call transfer is a call established between two parties where one of the parties transfers the call to a new user. For example, a PSTN endpoint calls user A (Lync callee). User A determines the PSTN user should be forwarded to user B (Lync user). User A places the call with the PSTN user on hold, and calls user B. User B agrees to talk to the PSTN user. User A transfers the call on-hold to user B."
---

# Location-Based Routing and consultative call transfers in Lync Server 2013
[]
In addition to enforcing Location-Based Routing to Lync meetings, the Location-Based Routing Conferencing application enforces Location-Based Routing restrictions on consultative call transfers that egress to PSTN endpoints. A consultative call transfer is a call established between two parties where one of the parties transfers the call to a new user. For example, a PSTN endpoint calls user A (Lync callee). User A determines the PSTN user should be forwarded to user B (Lync user). User A places the call with the PSTN user on hold, and calls user B. User B agrees to talk to the PSTN user. User A transfers the call on-hold to user B.
  
**Consultative call transfer call flow**

![Location-based routing for conferencing diagram](media/LocationBasedRoutingForConferencing.jpg)
  
When a user enabled for Location-Based Routing initiates a consultative call transfer of a PSTN endpoint (as shown in the preceding figure), this creates two active calls, one call between the PSTN user and Lync user A, and the other between Lync user A and Lync user B. the following behavior is enforced by the Location-Based Routing Conferencing application:
  
- If the SIP trunk routing the PSTN call is authorized to re-route the PSTN call to the network site where Lync user B (i.e. transfer target) is located,, then the call transfer will be allowed; otherwise, the consultative call transfer will be blocked. This authorization is performed based on the transferred party's location being in the same network site as the SIP trunk that is routing the active call to the PSTN endpoint. 
    
- If the SIP trunk routing the inbound PSTN call is not authorized to route calls to the network site where the transferred party (Lync user B) is located or the transferred party is located in an unknown network site, then the consultative call transfer to the PSTN endpoint (i.e. call transfer target) will be blocked.
    
The following table describes how Location-Based Routing restrictions are applied by the Location-Based Routing Conferencing application for consultative call transfers. Although PBX endpoints are not directly associated with a network site, the SIP trunk the PBX is connected to can be assigned a network site. Therefore, the PBX endpoint can be indirectly associated with a network site.
  
||||
|:-----|:-----|:-----|
|Network site of call transferred party  <br/> |Network site of call transfer target  <br/> |Behavior  <br/> |
|PSTN endpoint  <br/> |Lync user in the same network site (i.e. site 1)  <br/> |Consultative transfer will be allowed  <br/> |
|PSTN endpoint  <br/> |Lync user in different network sites (i.e. site 2)  <br/> |Consultative transfer will be disallowed  <br/> |
|PSTN endpoint  <br/> |Lync user in an unknown network site  <br/> |Consultative transfer will be disallowed  <br/> |
|PSTN endpoint  <br/> |Federated Lync user  <br/> |Consultative transfer will be disallowed  <br/> |
|PSTN endpoint  <br/> |PBX endpoint in the same site (i.e. site 1)  <br/> |Consultative transfer will be allowed  <br/> |
|PSTN endpoint  <br/> |PBX endpoint in a different sites (i.e. site 2)  <br/> |Consultative transfer will be disallowed  <br/> |
|PBX endpoint in the same site (i.e. site 1)  <br/> |PSTN endpoint  <br/> |Consultative transfer will be allowed  <br/> |
|PBX endpoint in a different site (i.e. site 2)  <br/> |PSTN endpoint  <br/> |Consultative transfer will be disallowed  <br/> |
|PBX endpoint in any site  <br/> |Lync user in the same network site (i.e. site 1)  <br/> |Consultative transfer will be allowed  <br/> |
|PBX endpoint in any site  <br/> |Lync user in different network sites (i.e. site 2)  <br/> |Consultative transfer will be allowed  <br/> |
|PBX endpoint in any site  <br/> |Lync user in an unknown network site  <br/> |Consultative transfer will be allowed  <br/> |
|PBX endpoint in any site  <br/> |Federated Lync user  <br/> |Consultative transfer will be allowed  <br/> |
   

