---
title: "High Availability (Planning Tool)"
ms.author: heidip
author: microsoftheidi
manager: serdars
ms.date: 4/8/2016
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.plan.HighAvailability
- ms.lync.plan.HighAvailability
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 14a897b3-2406-46c7-b08f-490085b3d048
description: "The main high availability scheme for most server roles in Skype for Business Server 2015 is based on server redundancy via pooling. If a server running a certain server role fails, the other servers in the pool running the same role take the load of that server."
---

# High Availability (Planning Tool)
 
The main high availability scheme for most server roles in Skype for Business Server 2015 is based on server redundancy via pooling. If a server running a certain server role fails, the other servers in the pool running the same role take the load of that server.
  
Skype for Business Server 2015 requires at least two Front End Servers in order to enable high availability. The Planning Tool uses the following criteria to determine if it will add extra servers in order to support high availability:
  
- If the deployment contains two or more Front End Servers, the Planning Tool does not add an extra server.
    
- If the deployment contains Edge Server, an additional server is added. 
    
- If the deployment contains Persistent Chat, the planning tool will add an extra server, but not increase the pool number. For example, if the deployment already contains four servers, the Planning Tool will suggest adding an additional server (for a total of five servers) but will maintain a single pool. 
    
The Planning Tool also adds a mirror SQL database for all databases. For example, if there is a Front End SQL Server database, the Planning Tool will add the other database as the mirror database for this one and name it as the "Front End mirror SQL database.
  
For more details about preparing your environment for high availability, see [Plan for high availability and disaster recovery in Skype for Business Server 2015](../../plan-your-deployment/high-availability-and-disaster-recovery/high-availability-and-disaster-recovery.md).
  

