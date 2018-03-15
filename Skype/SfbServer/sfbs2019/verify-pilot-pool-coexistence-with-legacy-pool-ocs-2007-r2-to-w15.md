---
title: "Verify pilot pool coexistence with legacy pool [OCS 2007 R2 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 597d0fa6-ca04-4521-b1c2-72d7f35ecd08
description: "In this articleVerify the Pool in Office Communications Server 2007 R2 Administrative ToolVerify the Pilot Pool in Lync Server 2013 Control PanelVerify Lync Server 2013 services have started"
---

# Verify pilot pool coexistence with legacy pool [OCS 2007 R2 to W15]
[]
 **In this article**
  
[Verify the Pool in Office Communications Server 2007 R2 Administrative Tool](#sectionSection0)
  
[Verify the Pilot Pool in Lync Server 2013 Control Panel](#sectionSection1)
  
[Verify Lync Server 2013 services have started](#sectionSection2)
  
## Verify the Pool in Office Communications Server 2007 R2 Administrative Tool
<a name="sectionSection0"> </a>

1. Open the Office Communications Server 2007 R2 administrative tool.
    
2. Expand the **Forest** node, expand the **Standard Edition Servers** or **Enterprise pools** node, and then expand the pool or server name. 
    
3. Ensure that the Office Communications Server 2007 R2 services are running on the pool.
    
     ![Office Communications Server 2007 R2 Admin Console](media/migration_ocs_topo_w13adminconsole.JPG)
  
## Verify the Pilot Pool in Lync Server 2013 Control Panel
<a name="sectionSection1"> </a>

1. From a user account that is a member of the CsAdministrator role, log on to the Lync Server 2013 Front End server. 
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. Click **Topology**.
    
4. Verify that the servers you deployed are present in your pilot pool. 
    
     ![Lync Server Control Panel Topology page](media/migration_ocs_topo_w14adminconsole.JPG)
  
## Verify Lync Server 2013 services have started
<a name="sectionSection2"> </a>

1. On the Lync Server 2013 Front End Server, open the **Services** applet from the **Administrative Tools** group. 
    
2. Verify that the services listed match the list in the following figure.
    
     ![Services page showing Lync services started](media/migration_lyncserver_config_w15_services.jpg)
  

