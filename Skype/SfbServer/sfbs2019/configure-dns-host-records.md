---
title: "Configure DNS Host records for Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 78a1afcf-41c8-4da5-8740-c6570c19078c
description: "To successfully complete this procedure, you should be logged on to the server or domain at minimum as a member of the Domain Admins group or a member of the DnsAdmins group."
---

# Configure DNS Host records for Lync Server 2013
[]
To successfully complete this procedure, you should be logged on to the server or domain at minimum as a member of the Domain Admins group or a member of the DnsAdmins group.
  
### To configure DNS Host A records

1. On the Domain Name System (DNS) server, click **Start**, click **Administrative Tools**, and then click **DNS**.
    
2. In the console tree for your domain, expand **Forward Lookup Zones**, and then right-click the domain in which Lync Server 2013 will be installed.
    
3. Click **New Host (A or AAAA)**.
    
4. Click **Name**, type the host name for the pool (the domain name is assumed from the zone that the record is defined in and does not need to be entered as part of the A record).
    
5. Click **IP Address**, type the virtual IP (VIP) of the load balancer for the Front End pool.
    
    > [!IMPORTANT]
    > In deployments that use a Director pool, the host (A) records for the simple URLs should point to the VIP of the Director load balancer. 
  
    > [!NOTE]
    >  If you deploy only one Enterprise Edition server or Director that is connected to the topology without a load balancer, or if you deploy a Standard Edition server, type the IP address of the Enterprise Edition server, Standard Edition server, or Director. A load balancer is required if you deploy more than one Enterprise Edition server or Director in a pool. Load balancers are not used with Standard Edition servers. 
  
6. Click **Add Host**, and then click **OK**. 
    
7. To create an additional A record, repeat steps 4 and 5.
    
8. When you are finished creating all the A records that you need, click **Done**.
    

