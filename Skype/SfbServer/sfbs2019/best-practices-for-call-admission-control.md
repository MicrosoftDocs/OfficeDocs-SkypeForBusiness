---
title: "Best practices for call admission control in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 97173cca-8175-4ae2-a247-eb7ef809da93
description: "To enhance performance and facilitate deployment, apply the following best practices when you deploy call admission control:"
---

# Best practices for call admission control in Lync Server 2013
[]
To enhance performance and facilitate deployment, apply the following best practices when you deploy call admission control:
  
- Ensure that WANs are adequately provisioned for current and anticipated media traffic.
    
    > [!NOTE]
    > We recommend that you factor in a buffer to your bandwidth limits. There are scenarios such as race conditions that affect the total bandwidth used and can result in situations where the bandwidth limit is exceeded. For example, if two calls try to start while media traffic is approaching a bandwidth limit, one of them may be denied because the other managed to start first. 
  
- Monitor network usage and call detail records so that you can choose optimal CAC settings and update CAC settings as network usage changes.
    
- Use CAC bandwidth policies to complement QoS settings.
    
- If you want to re-route blocked calls onto the PSTN, verify PSTN functionality and capacity. For details, see [Planning outbound voice routing in Lync Server 2013](planning-outbound-voice-routing.md).
    
    > [!NOTE]
    > Capacity refers to the number of ports you need to open to support potential PSTN re-routing. 
  

