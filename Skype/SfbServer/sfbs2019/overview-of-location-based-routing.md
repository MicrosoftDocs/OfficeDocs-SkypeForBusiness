---
title: "Overview of Location-Based Routing in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4aa494bd-0d66-4335-b9e8-f758d44a7202
description: "Location-Based Routing introduces a new set of rules that modifies the routing of national and international PSTN calls to prevent toll bypass. Location-Based Routing provides the flexibility to scope these rules to specific regions, specific gateways or to specific set of users only."
---

# Overview of Location-Based Routing in Lync Server 2013
[]
Location-Based Routing introduces a new set of rules that modifies the routing of national and international PSTN calls to prevent toll bypass. Location-Based Routing provides the flexibility to scope these rules to specific regions, specific gateways or to specific set of users only.
  
The following scenarios illustrate the main types of restrictions Location-Based Routing can enforce:
  
- Egress calls - Location-Based Routing can enforce outgoing calls to egress from a PSTN gateway that is located in the same region as where the caller is to prevent PSTN toll bypass, which prevents calls to egress from a PSTN gateway located in a different region as the caller.
    
- Ingress calls - Location-Based Routing can prevent incoming PSTN calls to ring Lync endpoints if the PSTN gateway routing the incoming call is not located in the same region as the called Lync user.
    
- Unknown regions - Location-Based Routing restricts incoming and outgoing PSTN calls to and from users that are located in undetermined locations (i.e. remote users connecting from the Internet or located in unknown regions).
    
- International regions - Location-Based Routing enforces routing of outgoing calls through international PSTN gateways if a gateway local to the user's location cannot be found.
    
## See also

#### 

[Planning for Location-Based Routing in Lync Server 2013](planning-for-location-based-routing.md)

