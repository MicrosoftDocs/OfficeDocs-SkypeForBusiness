---
title: "Media bypass modes in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 38c06c81-7e45-4423-9e00-7fbfa4befe46
description: "You must configure media bypass both globally and for each individual PSTN trunk. When enabling media bypass globally, you have two choices: Always Bypass and Use Site and Region Information."
---

# Media bypass modes in Lync Server 2013
[]
You must configure media bypass both globally and for each individual PSTN trunk. When enabling media bypass globally, you have two choices: **Always Bypass** and **Use Site and Region Information**. 
  
As the name suggests, **Always Bypass** means that bypass will be attempted for all PSTN calls. **Always Bypass** is used for deployments where there is no need to enable call admission control, nor is there a need to specify detailed configuration information regarding when to attempt media bypass. Furthermore, **Always Bypass** is used when there is full connectivity between clients and PSTN gateways. In this configuration, all subnets are mapped to one and only one bypass ID, which is computed by the system. 
  
With **Use Site and Region Information**, the bypass ID associated with site and region configuration is used to make the bypass decision. This configuration provides the flexibility to configure bypass for most common topologies, as it gives you fine-grained control over when bypass happens, in addition to supporting interactions with call admission control (CAC). The system tries to ease your task by automatically assigning bypass IDs as follows.
  
- The system automatically assigns a single unique bypass ID to each region.
    
- Any site connected to a region over a WAN link without bandwidth constraints inherits the same bypass ID as the region.
    
- A site associated with the region over a WAN link with constrained bandwidth is assigned a different bypass ID from that of the region.
    
- Subnets associated with each site inherit the bypass ID for that site.
    
## See also

#### 

[Overview of media bypass in Lync Server 2013](overview-of-media-bypass.md)
  
[Media bypass and call admission control in Lync Server 2013](media-bypass-and-call-admission-control.md)
  
[Technical requirements for media bypass in Lync Server 2013](technical-requirements-for-media-bypass.md)

