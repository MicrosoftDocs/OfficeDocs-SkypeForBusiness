---
title: "Estimating voice usage and traffic for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 621b08fb-f894-4d91-ac38-e443401b098b
description: "The Microsoft Lync Server 2013, Planning Tool uses the following metric to estimate user traffic at each site and the number of ports that are required to support that traffic."
---

# Estimating voice usage and traffic for Lync Server 2013
[]
The Microsoft Lync Server 2013, Planning Tool uses the following metric to estimate user traffic at each site and the number of ports that are required to support that traffic.
  
> For **Light traffic** (one PSTN call per user per hour), figure 15 users per port. 
    
> For **Medium traffic** (2 PSTN calls per user per hour), figure 10 users per port. 
    
> For **Heavy traffic** (3 or more PSTN per user calls per hour), figure 5 users per port. 
    
The number of ports in turn determines the number of Mediation Servers and gateways that will be required. The public switched telephone network (PSTN) gateways that most organizations consider deploying range in size from 2 ports to as many as 960 ports. (There are even larger gateways, but these are used mainly by telephony service providers.)
  
For example, an organization with 10,000 users and medium traffic would require 1000 ports. The number of gateways required would equal the total number of ports required as determined by the total capacity of the gateways.
  

