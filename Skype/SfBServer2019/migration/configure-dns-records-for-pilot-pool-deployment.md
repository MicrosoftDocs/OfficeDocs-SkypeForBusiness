---
title: "Configure DNS records for pilot pool deployment"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Prior to deploying the pilot pool, you must update the DNS Host A entries for the pilot pool. To successfully complete this procedure, you should be logged on to the server or domain as a member of the Domain Admins group or a member of the DnsAdmins group."
---

# Configure DNS records for pilot pool deployment

Before deploying the pilot pool, you must update the DNS Host A entries for the pilot pool. To successfully complete this procedure, you should be logged on to the server or domain as a member of the Domain Admins group or a member of the DnsAdmins group.
  
### To configure DNS Host A records

1. On the Domain Name System (DNS) server, click **Start**, click **Administrative Tools**, and then click **DNS**.
    
2. In the console tree for your domain, expand **Forward Lookup Zones**, and then right-click the domain in which Skype for Business Server 2019 will be installed.
    
3. Click **New Host (A or AAAA)**.
    
4. Click **Name**, type the host name for the Skype for Business Server 2019 pool (the domain name is assumed from the zone that the record is defined in and does not need to be entered as part of the A record).
    
5. Click **IP Address**, and then type the IP address for the Front End pool.
    
6. Click **Add Host**, and then click **OK**. 
    
7. When you are finished, click **Done**.
    

