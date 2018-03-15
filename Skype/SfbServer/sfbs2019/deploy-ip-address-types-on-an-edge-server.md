---
title: "Deploy IP address types on an Edge Server for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6e2fe7e8-6e90-4d1a-8fc5-e3be92c46571
description: "Using Topology Builder, perform the steps in the following procedure to deploy IP address types on an Edge Server."
---

# Deploy IP address types on an Edge Server for Lync Server 2013
[]
Using Topology Builder, perform the steps in the following procedure to deploy IP address types on an Edge Server.
  
### To deploy IP address types on an Edge Server

1. In Topology Builder, under **Edge pools**, right-click the server within a pool, and then select **Edit Properties**. (Alternatively, select the server, and then click **Edit Properties** from the **Action** menu.) 
    
2. In the **Edit Properties** window, select the IP address configuration that you want to support. The following figures show a dual stack configuration for the internal interface and the external interface. 
    
   **Dual stacked Edge Server internal interface**

     ![Lync Server general properties page](media/Deploy_LyncServer_IPv6_Edge_EditProps.png)
  
   **Dual stacked Edge Server external interface**

     ![Lync Server next hop/external configuration page](media/Deploy_LyncServer_IPv6_Edge_EditPropsExternal.png)
  
3. For each address type that you select, you must supply appropriate internal and external addresses.
    

