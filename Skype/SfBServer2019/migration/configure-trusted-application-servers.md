---
title: "Configure trusted application servers [W14 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 20c3815f-3048-4940-8c0f-cdfcd0801d5d
description: "In a mixed environment, if you create a new trusted application server, you must set the next hop pool to be a Lync Server 2013 pool. In a mixed environment, both the legacy Lync Server 2010 pool and the Lync Server 2013 pool appear in the drop down list. Selecting the legacy pool is not supported."
---

# Configure trusted application servers [W14 to W15]
[]
In a mixed environment, if you create a new trusted application server, you must set the next hop pool to be a Lync Server 2013 pool. In a mixed environment, both the legacy Lync Server 2010 pool and the Lync Server 2013 pool appear in the drop down list. Selecting the legacy pool is not supported.
  
> [!IMPORTANT]
> If you are migrating a trusted application server from a previous version of Lync Server, you should also update the version of UCMA you are using. If you create a new Trusted Application Pool for Lync Server 2013, you should update UCMA to the version that is included with Lync Server 2013 or the latest version available. 
  
### Select Lync Server 2013 as next hop when creating a Trusted application server

1. Open Topology Builder.
    
2. In the left pane, right click **Trusted application servers** and click **New Trusted Application Pool**.
    
3. Enter the **Pool FQDN** of the trusted application pool and select whether it will be a single-server or multiple-server. 
    
4. Click **Next**.
    
5. On the **Select the next hop** page, from the list, select the Lync Server 2013 Front End pool. 
    
6. Click **Finish**.
    
7. Select the top node **Lync Server** and from the **Action** menu, select **Publish**.
    
    Verify the **Trusted Application Pool** has been created successfully and is associated with the correct Front End pool. 
    

