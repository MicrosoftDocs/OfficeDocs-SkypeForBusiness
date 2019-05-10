---
title: "Estimating voice usage and traffic for Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 621b08fb-f894-4d91-ac38-e443401b098b
description: "You can use the following metric to estimate user traffic at each site and the number of ports that are required to support that traffic."
---

# Estimating voice usage and traffic for Skype for Business Server
 
You can use the following metric to estimate user traffic at each site and the number of ports that are required to support that traffic.
  
> For **Light traffic** (one PSTN call per user per hour), figure 15 users per port.
> 
> For **Medium traffic** (2 PSTN calls per user per hour), figure 10 users per port.
> 
> For **Heavy traffic** (3 or more PSTN per user calls per hour), figure 5 users per port.
    
The number of ports in turn determines the number of Mediation Servers and gateways that will be required. The public switched telephone network (PSTN) gateways that most organizations consider deploying range in size from 2 ports to as many as 960 ports. (There are even larger gateways, but these are used mainly by telephony service providers.)
  
For example, an organization with 10,000 users and medium traffic would require 1000 ports. The number of gateways required would equal the total number of ports required as determined by the total capacity of the gateways.
  

