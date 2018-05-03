---
title: "Verify Lync Server 2010 environment"
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: bfc7c620-556a-43cd-b1ed-2c268ec2b5cc
description: "Before deploying Lync Server 2013 in a coexistence state with Lync Server 2010, you need to verify that Lync Server 2010 services have been configured and started. It is important to identify key services and features that exist in your legacy environment, prior to deploying a Lync Server 2013 pilot pool. Before deploying Microsoft Lync Server 2013 XMPP in a coexistence state with a legacy XMPP deployment, you need to verify the legacy XMPP services have been configured and started, and identify which federated partner the legacy XMPP configuration is supporting. Verifying your legacy Lync Server 2010 deployment entails the following:"
---

# Verify Lync Server 2010 environment
[]
Before deploying Lync Server 2013 in a coexistence state with Lync Server 2010, you need to verify that Lync Server 2010 services have been configured and started. It is important to identify key services and features that exist in your legacy environment, prior to deploying a Lync Server 2013 pilot pool. Before deploying Microsoft Lync Server 2013 XMPP in a coexistence state with a legacy XMPP deployment, you need to verify the legacy XMPP services have been configured and started, and identify which federated partner the legacy XMPP configuration is supporting. Verifying your legacy Lync Server 2010 deployment entails the following:
  
- Verifying the Lync Server 2010 services are started
    
- Reviewing the topology and users in Lync Server 2010.
    
- Verifying the federation and Edge server settings.
    
- Verifying XMPP services and federated partners.
    
### Verify Lync Server 2010 Services are started

1. From the Lync Server 2010 Front End Server, navigate to the Administrative Tools\Services applet.
    
2. Verify that the following services are running on the Front End Server:
    
     ![List of services running on Front End Server](../../media/migration_lyncserver_config_w14_services.jpg)
  
### Review the Lync Server 2010 topology in Lync Server Control Panel

1. Log on to the Front End Server with an account that is a member of the RTCUniversalServerAdmins group or a member of the CsAdministrator or CsUserAdministrator administrative role.
    
2. Open the Lync Server Control Panel.
    
3. Select **Topology**. Verify that the various servers in your Lync Server 2010 deployment are listed.
    
     ![Lync Server 2010 Control Panel topology page](../../media/migration_lyncserver_2010_topology.JPG)
  
### To review Lync Server 2010 users in Lync Server Control Panel

1. Open the Lync Server Control Panel.
    
2. Select **Users** and then click **Find**.
    
3. Verify that the **Registrar Pool** column points to the Lync Server 2010 pool for each user listed. 
    
     ![Lync Server 2010 Control Panel listing users](../../media/migration_lyncserver_2010_allusers.JPG)
  
### To verify Lync Server 2010 Edge and Federation Settings

1. Start Topology Builder.
    
2. Select **Download Topology from existing deployment**.
    
3. Choose a file name and save the topology with the default .tbxml file type.
    
4. Expand the Lync Server 2010 node to reveal the various server roles in the deployment.
    
5. Select the site node and verify if a **Site federation route assignment** value is set. 
    
     ![Topology Builder, Site Federation Route](../../media/migration_lyncserver_w14_federation.jpg)
  
6. Next, select the Standard Edition Server or Enterprise Edition front end pool. Determine if an Edge pool has been configured for Media below **Associations**. 
    
     ![Topology Builder showing servers and pools](../../media/migration_lyncserver_w14_edgepool_media.jpg)
  
7. Finally, select the Edge pool and identify if a Next hop pool is configured below **Next hop selection**.
    
     ![Topology Builder, Next hop selection](../../media/migration_lyncserver_w14_nexthop.jpg)
  
### Verify legacy XMPP Federated Partner Configuration

1. From the legacy XMPP server, navigate to the Administrative Tools\Services applet.
    
2. Verify that the Office Communications Server XMPP Gateway service is started. 
    
     ![Office Communications Server XMPP Gateway Service](../../media/migration_lyncserver_15_xmpp_legacyservicesstarted.JPG)
  

