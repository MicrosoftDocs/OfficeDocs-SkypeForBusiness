---
title: "Verify pilot pool coexistence with legacy pool"
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 11/17/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Process to verify pilot pool coexistence with legacy pool."
---

# Verify pilot pool coexistence with legacy pool

 **In this article**
  
[Verify that Skype for Business Server 2019 services have started](#sectionSection0)
  
[Open the Skype for Business Server 2019 Control Panel](#sectionSection1)
  
[Don't attempt to open the topology in the legacy Topology Builder](#sectionSection2)
  
After you deploy the pilot pool, you need to verify the coexistence of the two pools by using the administrative tools to view the pool information. For the Skype for Business Server 2019 pools and legacy pools, you must use the Skype for Business Server 2019 Control Panel and Topology Builder tools. 
  
## Verify that Skype for Business Server 2019 services have started
<a name="sectionSection0"> </a>

1. From the Skype for Business Server 2019 Front End Server, navigate to the Administrative Tools\Services applet.
    
2. Verify that the following services are running on the Front End Server:
    
**Skype for Business Server 2019 services**

![List of Skype for Business Server Services Started](../media/Migration_LyncServer_from_LyncServer2010_ServicesStarted.png)
  
## Open the Skype for Business Server 2019 Control Panel
<a name="sectionSection1"> </a>

From the Front End Server in your Skype for Business Server 2019 deployment, open the Skype for Business Server 2019 Control Panel and select the legacy pool. Repeat the procedure to open the Skype for Business Server 2019 pool.
  
**Open Skype for Business Server 2019 Control Panel**

![Select URL dialog box](../media/Migration_LyncServer_from_LyncServer2010_CPanelOpenDialog.png)
  
> [!IMPORTANT]
> On Skype for Business Server 2019, you must upgrade Silverlight to Silverlight version 5 prior to using the Skype for Business Server Control Panel. 
  
This topology now includes legacy and Skype for Business Server 2019 server roles. 
  
**Skype for Business Server 2019 Control Panel Topology page**

![Skype for Business Server Control Panel - Topology page](../media/migration_lyncserver_config_w15_lcsp_topology.JPG)
  
## Don't attempt to open the topology in the legacy Topology Builder
<a name="sectionSection2"> </a>

If you attempt to open the topology using the legacy Topology Builder, you will encounter the error below. The topology can only be viewed using Skype for Business Server 2019 Topology Builder. The Skype for Business Server 2019 Topology Builder must be used to create pools for both Skype for Business Server 2019 and the legacy install.
  
**Topology Builder error message**

![Topology Builder MMC Snap Error](../media/Migration_LyncServer_from_LyncServer2010_TopoBuilderErrorMsg.png)
  

