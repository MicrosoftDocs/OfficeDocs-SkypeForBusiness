---
title: "Call transfers and call forwarding in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 978610ec-63c7-4cf6-ad7a-9ef91559bf12
description: "When a PSTN endpoint is involved, Location-Based Routing analyzes the location of the calle's endpoint and the endpoint where the call will be transferred or forwarded to (i.e. transfer/forward target). Location-Based Routing determines whether the call should be transferred or forwarded depending on the location of both endpoints."
---

# Call transfers and call forwarding in Lync Server 2013
[]
When a PSTN endpoint is involved, Location-Based Routing analyzes the location of the calle's endpoint and the endpoint where the call will be transferred or forwarded to (i.e. transfer/forward target). Location-Based Routing determines whether the call should be transferred or forwarded depending on the location of both endpoints.
  
The following table illustrates the scenario of a Lync user in a call with a PSTN endpoint, and the Lync user transfers the call to another Lync user. Depending on the network site location of the transferee's endpoint, Location-Based Routing affects the routing of the call transfer or forward.
  
**Initiating call transfer or forward**

|**User initiating the call transfer/forward**|**Target endpoint is in same network site as user initiating call transfer or forward**|**Target endpoint is in different network site as user initiating call transfer or forward**|**Target endpoint is in unknown network site or network site not enabled for Location-Based Routing**|
|:-----|:-----|:-----|:-----|
|Lync user  <br/> |Call forward or transfer is allowed  <br/> |Call forward or transfer is not allowed  <br/> |Call forward or transfer is not allowed  <br/> |
   
For example: a Lync user in a call with a PSTN endpoint transfers the call to another Lync user that is in the same network site. In this case, the call transfer is allowed. 
  
The following table illustrates the scenario of a Lync user in a call with another Lync user, and one of the users transfers the call to a PSTN endpoint. Depending on the location of the user the call is being transferred to, the table details how Location-Based Routing affects the call.
  
**Call transfer or forward to PSTN endpoint**

|**Call transfer/forward endpoint target**|**Lync users in same network site**|**Lync users in different network sites**|**One or both Lync users in unknown network site or network site not enabled for Location-Based Routing**|
|:-----|:-----|:-----|:-----|
|PSTN endpoint  <br/> |Call forward or transfer allowed by the transferred user's site voice routing policy  <br/> |Call forward or transfer allowed by the transferred user's site voice routing policy  <br/> |Call forward or transfer allowed by the transferred user's voice policy only through trunks not enabled for Location-Based Routing  <br/> |
   
For example: a Lync user in a call with another Lync user that is in the same network site transfers the call to a PSTN endpoint and the call transfer is allowed. 
  
## See also

#### 

[Scenarios for Location-Based Routing in Lync Server 2013](scenarios-for-location-based-routing.md)

