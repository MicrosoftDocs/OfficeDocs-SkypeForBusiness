---
title: "Configure DNS records for pilot pool deployment [OCS 2007 R2 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5c7a6e10-e1e9-4479-9bf9-d4a3e2e09ff0
description: "Prior to deploying the Lync Server 2013 pilot pool, you must update the DNS Host A entries for the pilot pool. To successfully complete this procedure, you should be logged on to the server or domain at minimum as a member of the Domain Admins group or a member of the DnsAdmins group."
---

# Configure DNS records for pilot pool deployment [OCS 2007 R2 to W15]
[]
Prior to deploying the Lync Server 2013 pilot pool, you must update the DNS Host A entries for the pilot pool. To successfully complete this procedure, you should be logged on to the server or domain at minimum as a member of the Domain Admins group or a member of the DnsAdmins group.
  
### To configure DNS Host A records

1. On the Domain Name System (DNS) server, click **Start**, click **Administrative Tools**, and then click **DNS**.
    
2. In the console tree for your domain, expand **Forward Lookup Zones**, and then right-click the domain in which Lync Server 2013 will be installed.
    
3. Click **New Host (A or AAAA)**.
    
4. Click **Name**, type the host name for the pool (the domain name is assumed from the zone that the record is defined in and does not need to be entered as part of the A record).
    
5. Click **IP Address**, type the IP address for the Front End pool.
    
6. Click **Add Host**, and then click **OK**. 
    
7. When you are finished, click **Done**.
    

