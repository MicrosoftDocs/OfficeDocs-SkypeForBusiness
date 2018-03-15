---
title: "Configuring a failover route in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 76e48df4-3b78-4fb7-b1f7-c1e604b81bad
description: "The following example shows how an administrator can define a failover route for use if the Dallas-GW1 is down for maintenance or is otherwise unavailable. The following tables illustrate the required configuration change."
---

# Configuring a failover route in Lync Server 2013
[]
 The following example shows how an administrator can define a failover route for use if the Dallas-GW1 is down for maintenance or is otherwise unavailable. The following tables illustrate the required configuration change. 
  
**Table 1. User Policy**

|**User policy**|**Phone usage**|
|:-----|:-----|
|Default Calling Policy  <br/> |Local  <br/> GlobalPSTNHopoff  <br/> |
|Redmond Local Policy  <br/> |RedmondLocal  <br/> |
|Dallas Calling Policy  <br/> |DallasUsers  <br/> GlobalPSTNHopoff  <br/> |
   
**Table 2. Routes**

|**Route name**|**Number pattern**|**Phone usage**|**Trunk**|**Gateway**|
|:-----|:-----|:-----|:-----|:-----|
|Redmond Local Route  <br/> |^\+1(425|206|253)(\d{7})$  <br/> |Local  <br/> RedmondLocal  <br/> |Trunk1  <br/> Trunk2  <br/> |Red-GW1  <br/> Red-GW2  <br/> |
|Dallas Local Route  <br/> |^\+1(972|214|469)(\d{7})$  <br/> |Local  <br/> |Trunk3  <br/> |Dallas-GW1  <br/> |
|Universal Route  <br/> |^\+?(\d\*)$  <br/> |GlobalPSTNHopoff  <br/> |Trunk1  <br/> Trunk2  <br/> Trunk3  <br/> |Red-GW1  <br/> Red-GW2  <br/> Dallas-GW1  <br/> |
|Dallas Users Route  <br/> |^\+?(\d\*)$  <br/> |DallasUsers  <br/> |Trunk3  <br/> |Dallas-GW1  <br/> |
   
In Table 1, a phone usage of GlobalPSTNHopoff is added after the DallasUsers phone usage in the Dallas Calling Policy. This enables calls with the Dallas Calling policy to use routes that are configured for the GlobalPSTNHopoff phone usage if a route for the DallasUsers phone usage is unavailable.
  

