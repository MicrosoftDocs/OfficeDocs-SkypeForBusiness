---
title: "Add Edge Server IP Options"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 11/17/2018
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.tb.AddEdgeServerIPOptionsPage
ms.service: skype-for-business-server
ms.localizationpriority: medium
ms.assetid: f458287f-e7a5-45f2-8393-3e1377be81d9
description: "Microsoft Lync Server 2013 allows you to configure IPv4 and IPv6 addresses for each interface for the Microsoft Edge Server and Edge pool. To do this, you do the following:"
---

# Add Edge Server IP Options
 
Microsoft Lync Server 2013 allows you to configure IPv4 and IPv6 addresses for each interface for the Microsoft Edge Server and Microsoft Edge pool. To do this, you do the following:
  
- **Enable IPv4 on internal interface**: Select the check box if you want to apply an IPv4 address to the Microsoft Edge Server or Microsoft Edge pool internal interface
    
- **Enable IPv6 on internal interface**: Select the check box if you want to apply an IPv6 address to the Microsoft Edge Server or Microsoft Edge pool internal interface
    
- **Enable IPv4 on external interface**: Select the check box if you want to apply an IPv4 address to the Microsoft Edge Server or Microsoft Edge pool external interface
    
- **Enable IPv6 on external interface**: Select the check box if you want to apply an IPv6 address to the Microsoft Edge Server or Microsoft Edge pool external interface
    
You can also configure the Microsoft Edge Server or Microsoft Edge pool to use a network address translation address for the external IP addresses. You do this by selecting the check box **The external IP address of this Edge pool is translated by NAT**.
  
NAT support. Network address translation (NAT) isn't supported when you use hardware load balancing, so don't select the NAT option if you deploy a Microsoft Edge Server pool with hardware load balancing.
  

