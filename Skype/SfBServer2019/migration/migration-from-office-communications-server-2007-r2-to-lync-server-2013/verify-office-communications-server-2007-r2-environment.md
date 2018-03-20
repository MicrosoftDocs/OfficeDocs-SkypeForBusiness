---
title: "Verify Office Communications Server 2007 R2 environment"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e051bdd5-e7ef-4754-8705-900b2c57f37c
description: "Prior to deploying Lync Server 2013 in a coexistence state with Office Communications Server 2007 R2, you need to verify the Office Communications Server 2007 R2 services are configured and started."
---

# Verify Office Communications Server 2007 R2 environment
[]
Prior to deploying Lync Server 2013 in a coexistence state with Office Communications Server 2007 R2, you need to verify the Office Communications Server 2007 R2 services are configured and started. 
  
### Verify the Pool is started using the Office Communications Server 2007 R2 Administrative Tool

1. Open the Office Communications Server 2007 R2 administrative tool.
    
2. Expand the **Forest** node, expand the **Standard Edition Servers** or **Enterprise pools** node, and then expand the pool or server name. 
    
3. Ensure that the services are running on the Standard Edition server or Enterprise pool.
    
     ![Office Communications Server 2007 R2 Admin Console](../../media/migration_ocs_topo_w13adminconsole.JPG)
  
### Review Users configured for Office Communications Server 2007 R2

1. Open the Office Communications Server 2007 R2 administrative tool.
    
2. Expand the **Forest** node, expand the **Standard Edition Servers** or **Enterprise pools** node, and then expand the pool or server name. 
    
3. Click **Users**. 
    
4. Verify the list of Office Communications Server 2007 R2 users. 
    
     ![List fo users in OCS Admin tool](../../media/migration_ocs_topo_w13services_userslist.JPG)
  
### Verify legacy XMPP Federated Partner Configuration

1. From the legacy XMPP server, navigate to the Administrative Tools\Services applet.
    
2. Verify that the Office Communications Server XMPP Gateway service is started. 
    
     ![Office Communications Server XMPP Gateway Service](../../media/migration_lyncserver_15_xmpp_legacyservicesstarted.JPG)
  

