---
title: "New disaster recovery and high availability features in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4fa7cd0f-784b-4d3f-b839-432c2ecaf7c1
description: "As in Lync Server 2010, the main high availability (HA) scheme for Lync Server 2013 is based on server redundancy via pooling. If a server running a certain server role fails, the other servers in the pool running the same role take the load of that server. This applies to Front End Servers, Edge Servers, Mediation Servers, and Directors."
---

# New disaster recovery and high availability features in Lync Server 2013
[]
As in Lync Server 2010, the main high availability (HA) scheme for Lync Server 2013 is based on server redundancy via pooling. If a server running a certain server role fails, the other servers in the pool running the same role take the load of that server. This applies to Front End Servers, Edge Servers, Mediation Servers, and Directors.
  
Lync Server 2013 adds new disaster recovery measures by enabling you to pair Front End pools located in two datacenters. If one of the paired pools goes down, an administrator can fail over the users from that pool to the other pool in the pair, to provide continuation of service. This functionality does not require expensive network or hardware solutions such as storage networks or shared disks.
  
Lync Server 2013 also adds Back End Server high availability. This is an optional topology in which you deploy two Back End Servers for a Front End pool, and set up synchronous SQL mirroring for all the Lync databases running on the Back End Servers. You may choose whether to deploy a witness for the mirror.
  
## See also

#### 

[Planning for high availability and disaster recovery in Lync Server 2013](planning-for-high-availability-and-disaster-recovery.md)

