---
title: "Simultaneous ringing in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: df02f919-4d50-4832-9300-6c51f8b4fc56
description: "When the called party has simultaneous ringing enabled, Location-Based Routing analyzes the location of the calling party and the endpoints of the called parties to determine whether the call should be routed."
---

# Simultaneous ringing in Lync Server 2013
[]
When the called party has simultaneous ringing enabled, Location-Based Routing analyzes the location of the calling party and the endpoints of the called parties to determine whether the call should be routed.
  
The following table illustrates a user configured with simultaneous ringing, and the simultaneous ringing target is a user in the same network site, in a different network site, or in an unknown network site. 
  
****

|**Incoming PSTN call for**|**Located in the same network site as callee**|**Located in different network site than callee**|**Located in unknown network site or not enabled for Location-Based Routing**|
|:-----|:-----|:-----|:-----|
|Lync user  <br/> |Simultaneous ring allowed  <br/> |Simultaneous ring not allowed  <br/> |Simultaneous ring not allowed  <br/> |
   
The following table illustrates a call from a Lync user (i.e. Lync caller) in the same network site, in a different network site, or from an unknown network site. The callee has a PSTN endpoint (i.e. cellphone) configured as a simultaneous ring target. In this scenario, Location-Based Routing will determine whether the call should be routed to the simultaneous ring target (i.e. cellphone) of the callee or not.
  
****

|**Simultaneous ring target**|**Located in the same network site as callee**|**Located in different network site than callee**|**Located in unknown network site or not enabled for Location-Based Routing**|
|:-----|:-----|:-----|:-----|
|PSTN endpoint  <br/> |Simultaneous ring allowed through the caller's site voice routing policy  <br/> |Simultaneous ring allowed through the caller's site voice routing policy  <br/> |Simultaneous ring allowed through the caller's voice policy to trunks not enabled for Location-Based Routing  <br/> |
   
## See also

#### 

[Scenarios for Location-Based Routing in Lync Server 2013](scenarios-for-location-based-routing.md)

