---
title: "Planning outbound voice routing in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 37c55fa4-175a-4190-b9e4-c2e5ac7b9261
description: "Outbound call routing applies to calls that are destined for a public switched telephone network (PSTN) gateway, trunk, or private branch exchange (PBX). When a user places a call, the server normalizes the phone number to E.164 format, if necessary, and attempts to match it to a SIP URI. If the server cannot make the match, it applies outbound call routing logic based on the supplied dial string. You define that logic by configuring the server settings that are described in the following table."
---

# Planning outbound voice routing in Lync Server 2013
[]
Outbound call routing applies to calls that are destined for a public switched telephone network (PSTN) gateway, trunk, or private branch exchange (PBX). When a user places a call, the server normalizes the phone number to E.164 format, if necessary, and attempts to match it to a SIP URI. If the server cannot make the match, it applies outbound call routing logic based on the supplied dial string. You define that logic by configuring the server settings that are described in the following table.
  
**Lync Server Outbound Call Routing Settings**

|**Object**|**Description**|
|:-----|:-----|
|Dial Plan  <br/> |A dial plan is a named set of normalization rules that translates phone numbers for a named location, individual user, or contact object into a single standard (E.164) format for purposes of phone authorization and call routing.  <br/> |
|Normalization rule  <br/> |Normalization rules define how phone numbers expressed in various formats are to be routed for each specified location, user, or contact object. The same dial string may be interpreted and translated differently, depending on the location from which it is dialed and the person or contact object that makes the call. A set of normalization rules associated with a particular location constitutes a dial plan.  <br/> |
|Voice policy  <br/> |A voice policy associates one or more PSTN usage records with one user or a group of users. A voice policy also provides a list of calling features that you can enable or disable.  <br/> |
|PSTN usage record  <br/> |A PSTN usage record specifies a class of call (such as internal, local, or long distance) that can be made by various users, or groups of users, in an organization.  <br/> |
|Call Route  <br/> |A call route associates destination phone numbers with particular trunks and PSTN usage records. A PSTN gateway is considered a trunk.  <br/> |
   
## In this section

This section provides guidelines for configuring the following outbound call routing server settings: 
  
> [Dial plans and normalization rules in Lync Server 2013](dial-plans-and-normalization-rules.md)
    
> [Voice policies in Lync Server 2013](voice-policies.md)
    
> [PSTN usage records in Lync Server 2013](pstn-usage-records.md)
    
> [Voice routes in Lync Server 2013](voice-routes.md)
    
## See also

#### 

[SIP trunking in Lync Server 2013](sip-trunking.md)
  
[Direct SIP connections in Lync Server 2013](direct-sip-connections.md)

