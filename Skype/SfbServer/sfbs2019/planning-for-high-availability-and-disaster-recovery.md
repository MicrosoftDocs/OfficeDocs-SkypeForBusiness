---
title: "Planning for high availability and disaster recovery in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 15a72073-0336-45dd-b2a0-35e7522c6000
description: "As in Lync Server 2010, the main high availability scheme for most server roles in Lync Server 2013 is based on server redundancy via pooling. If a server running a certain server role fails, the other servers in the pool running the same role take the load of that server. This applies to Front End Servers, Edge Servers, Mediation Servers, and Directors."
---

# Planning for high availability and disaster recovery in Lync Server 2013
[]
As in Lync Server 2010, the main high availability scheme for most server roles in Lync Server 2013 is based on server redundancy via pooling. If a server running a certain server role fails, the other servers in the pool running the same role take the load of that server. This applies to Front End Servers, Edge Servers, Mediation Servers, and Directors.
  
Lync Server 2013 adds new disaster recovery measures for Front End pools by introducing geographical dispersement of your servers into two data centers to provide continuation of service should one entire pool or site go down. 
  
Lync Server 2013 also enhances Back End Server high availability, by supporting synchronous SQL mirroring for your Back End databases. 
  
This section explains these major high availability and disaster recovery features, and also covers what steps you can take for high availability and disaster recovery for your other server roles as well. 
  
## In This Section

- [Front End pool disaster recovery in Lync Server 2013](front-end-pool-disaster-recovery.md)
    
- [Edge Server disaster recovery in Lync Server 2013](edge-server-disaster-recovery.md)
    
- [Planning for Enterprise Voice resiliency in Lync Server 2013](planning-for-enterprise-voice-resiliency.md)
    
- [Call management features for disaster recovery in Lync Server 2013](call-management-features-for-disaster-recovery.md)
    
- [Configuring Persistent Chat Server for high availability and disaster recovery in Lync Server 2013](configuring-persistent-chat-server-for-high-availability-and-disaster-recovery.md)
    
- [Lync Server 2010 metropolitan site resiliency](lync-server-2010-metropolitan-site-resiliency.md)
    

