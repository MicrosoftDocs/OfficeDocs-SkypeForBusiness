---
title: High Availability panning tool
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 4/8/2016
audience: ITPro
ms.topic: article
f1.keywords:
- ms.lync.plan.HighAvailability
- ms.lync.plan.HighAvailability
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.assetid: 14a897b3-2406-46c7-b08f-490085b3d048
description: "The main high availability scheme for most server roles in Skype for Business Server 2015 is based on server redundancy via pooling. If a server running a certain server role fails, the other servers in the pool that run the same role take the load from that server."
---

# High availability planning tool
 
The main high availability scheme for most server roles in Skype for Business Server 2015 is based on server redundancy via pooling. If a server running a certain server role fails, the other servers in the pool running the same role take the load of that server.
  
Skype for Business Server 2015 requires at least two Front End Servers to enable high availability. The Planning Tool uses the following criteria to determine if it will add extra servers to support high availability:
  
- If the deployment contains two or more Front End Servers, the Planning Tool doesn't add an extra server.
    
- If the deployment contains Edge Server, another server is added. 
    
- If the deployment contains Persistent Chat, the planning tool will add an extra server, but not increase the pool number. For example, if the deployment already contains four servers, the Planning Tool will suggest adding another server (for a total of five servers) but will maintain a single pool. 
    
The Planning Tool also adds a mirror SQL database for all databases. For example, if there's a Front End SQL Server database, the Planning Tool will add the other database as the mirror database for this one and name it as the "Front End mirror SQL database.
  
For more information about preparing your environment for high availability, see [Plan for high availability and disaster recovery in Skype for Business Server 2015](../../plan-your-deployment/high-availability-and-disaster-recovery/high-availability-and-disaster-recovery.md).
  

