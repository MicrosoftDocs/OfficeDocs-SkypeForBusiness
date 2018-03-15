---
title: "Configure web farm FQDNs for Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: cb25dbbd-dcea-4997-8e14-e5007dd7d3ca
description: "When you defined the configuration of the Standard Edition server, Front End pool, Director or Director pool in Topology Builder, you configure an external web services fully qualified domain name (FQDN). During the log on process of a client homed in the Standard Edition server or Front End pool, the configured web services FQDNs are sent by way of in-band provisioning. If you need to add or change the external web services URL, you use Topology Builder to configure or reconfigure the web services configuration using the procedure in this topic."
---

# Configure web farm FQDNs for Lync Server 2013
[]
When you defined the configuration of the Standard Edition server, Front End pool, Director or Director pool in Topology Builder, you configure an external web services fully qualified domain name (FQDN). During the log on process of a client homed in the Standard Edition server or Front End pool, the configured web services FQDNs are sent by way of in-band provisioning. If you need to add or change the external web services URL, you use Topology Builder to configure or reconfigure the web services configuration using the procedure in this topic.
  
### To configure an external pool FQDN for web services

1. Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.
    
2. In Topology Builder, in the console tree under **Standard Edition Front Ends**, **Enterprise Edition Front Ends**, and **Directors**, right-click the pool name that you need to edit, and then click **Edit Properties**. 
    
3. In the **Web services** section, add or edit the **External web services FQDN**.
    
4. Review and adjust the **Listening ports** for both HTTP and HTTPS. The defaults will be: 
    
  - **Listening ports:** HTTP 8080, HTTPS 4443 
    
  - **Published ports:** HTTP 80, HTTPS 443 
    
    Where the **Listening ports** is the port that the external web services will be configured to receive requests from the reverse proxy, and the **Published ports** is the ports that are published externally by the reverse proxy and is communicated to clients during in-band provisioning. 
    
5. When you have completed your additions and updates, click **OK** to continue. 
    
6. Right-click **Lync Server 2013**, and then click **Publish**.
    
    > [!IMPORTANT]
    > After publishing successfully completes, a link may be presented that informs you that there are additional steps that need to be taken. The link, if clicked, opens a list of servers affected by the changes made in Topology Builder that will require you to re-run the Lync Server Deployment Wizard on each listed server to update the configuration for added, removed, or changed components. 
  
7. Repeat these steps for each Standard Edition server, Front End pool, Director or Director pool in the organization.
    

