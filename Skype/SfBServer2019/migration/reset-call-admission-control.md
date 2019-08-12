---
title: "Reset call admission control"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "If a legacy Front End pool is hosting call admission control (CAC), you must move CAC hosting to a Skype for Business Server 2019 pool before you can remove the legacy Front End pool."
---

# Reset call admission control

If a legacy Front End pool is hosting call admission control (CAC), you must move CAC hosting to a Skype for Business Server 2019 pool before you can remove the legacy Front End pool.
  
### To reset CAC

1. Open Topology Builder.
    
2. Right-click the site node, and then click **Edit Properties**.
    
3. Under **Call Admission Control setting**, make sure **Enable Call Admission Control** is selected. 
    
4. Under **Front End pool to run call admission control (CAC)**, select the Skype for Business Server 2019 pool that is to host CAC, and then click **OK**.
    
5. Publish the topology.
    

