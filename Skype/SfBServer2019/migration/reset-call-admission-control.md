---
title: "Reset call admission control"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5873f56c-f3d6-4d73-beea-c9f37d5077f6
description: "If a Lync Server 2010 Front End pool is hosting call admission control (CAC), you must move CAC hosting to a Lync Server 2013 pool before you can remove the Lync Server 2010 Front End pool."
---

# Reset call admission control
[]
If a Lync Server 2010 Front End pool is hosting call admission control (CAC), you must move CAC hosting to a Lync Server 2013 pool before you can remove the Lync Server 2010 Front End pool.
  
### To reset CAC

1. Open Topology Builder.
    
2. Right-click the site node, and then click **Edit Properties**.
    
3. Under **Call Admission Control setting**, make sure **Enable Call Admission Control** is selected. 
    
4. Under **Front End pool to run call admission control (CAC)**, select the Lync Server 2013 pool that is to host CAC, and then click **OK**.
    
5. Publish the topology.
    

