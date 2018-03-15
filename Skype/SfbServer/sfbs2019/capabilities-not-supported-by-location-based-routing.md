---
title: "Capabilities not supported by Location-Based Routing in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c3d54953-a7d6-4465-a6c3-ae411b2d8ea9
description: "Location-Based Routing does not apply to the following types of interactions. Location-Based Routing is not enforced when Lync endpoints interact with PSTN endpoints using these capabilities."
---

# Capabilities not supported by Location-Based Routing in Lync Server 2013
[]
Location-Based Routing does not apply to the following types of interactions. Location-Based Routing is not enforced when Lync endpoints interact with PSTN endpoints using these capabilities.
  
- PSTN dial-in to conferences
    
- Incoming and outgoing PSTN calls through Response Group
    
- Call park or retrieval of PSTN calls through Call Park
    
- Incoming PSTN calls to Announcement Service
    
- Incoming PSTN calls retrieved via Group Call Pickup
    
To enforce Location-Based Routing rules to the types of interactions in the following list, you must enable Location-Based Routing for Conferencing:
  
- PSTN dial-out from conferences
    
- Escalations from peer-to-peer audio conversations to conferencing involving PSTN endpoints 
    
- Consultative transfers involving PSTN endpoints
    
To enable Location-Based Routing for Conferencing, see [Location-Based Routing for conferencing in Lync Server 2013](location-based-routing-for-conferencing.md).
  
## See also

#### 

[Planning for Location-Based Routing in Lync Server 2013](planning-for-location-based-routing.md)

