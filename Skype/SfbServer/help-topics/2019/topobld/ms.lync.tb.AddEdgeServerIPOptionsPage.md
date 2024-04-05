---
ms.date: 03/17/2018
title: "Add Edge Server IP Options"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.tb.AddEdgeServerIPOptionsPage
ms.service: skype-for-business-server
ms.localizationpriority: medium
ms.assetid: f458287f-e7a5-45f2-8393-3e1377be81d9
ROBOTS: NOINDEX, NOFOLLOW
description: "Skype for Business Server allows you to configure IPv4 and IPv6 addresses for each interface for the Microsoft Edge Server and Microsoft Edge pool."
---

# Add Edge Server IP Options
 
Skype for Business Server allows you to configure IPv4 and IPv6 addresses for each interface for the Microsoft Edge Server and Microsoft Edge pool. To do this, you do the following:
  
- **Enable IPv4 on internal interface**: Select the check box if you want to apply an IPv4 address to the Microsoft Edge Server or Microsoft Edge pool internal interface
    
- **Enable IPv6 on internal interface**: Select the check box if you want to apply an IPv6 address to the Microsoft Edge Server or Microsoft Edge pool internal interface
    
- **Enable IPv4 on external interface**: Select the check box if you want to apply an IPv4 address to the Microsoft Edge Server or Microsoft Edge pool external interface
    
- **Enable IPv6 on external interface**: Select the check box if you want to apply an IPv6 address to the Microsoft Edge Server or Microsoft Edge pool external interface
    
You can also configure the Microsoft Edge Server or Microsoft Edge pool to use a network address translation address for the external IP addresses. You can do configure the Microsoft Edge Server or Microsoft Edge Pool by selecting the check box **The external IP address of this Edge pool is translated by NAT**.
  
NAT support. Network address translation (NAT) isn't supported when you're using hardware load balancing. Microsoft recommends not to select the NAT option if you deploy a Microsoft Edge Server pool with hardware load balancing.
  


