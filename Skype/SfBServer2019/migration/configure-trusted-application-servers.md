---
title: "Configure trusted application servers"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "In a mixed environment, if you create a new trusted application server, you must set the next hop pool to be a Skype for Business Server 2019 pool. In a mixed environment, both the legacy pool and the Skype for Business Server 2019 pool appear in the drop down list. Selecting the legacy pool is not supported."
---

# Configure trusted application servers

In a mixed environment, if you create a new trusted application server, you must set the next hop pool to be a Skype for Business Server 2019 pool. In a mixed environment, both the legacy pool and the Skype for Business Server 2019 pool appear in the drop-down list. Selecting the legacy pool is not supported.
  
> [!IMPORTANT]
> If you are migrating a trusted application server, you should also update the version of UCMA you are using. If you create a new Trusted Application Pool for Skype for Business Server 2019, you should update UCMA to the version that is included with Skype for Business Server 2019 or the latest version available. 
  
### Select Skype for Business Server 2019 as next hop when creating a Trusted application server

1. Open Topology Builder.
    
2. In the left pane, right-click **Trusted application servers** and click **New Trusted Application Pool**.
    
3. Enter the **Pool FQDN** of the trusted application pool and select whether it will be single-server or multiple-server. 
    
4. Click **Next**.
    
5. On the **Select the next hop** page, from the list, select the Skype for Business Server 2019 Front End pool. 
    
6. Click **Finish**.
    
7. Select the top node **Skype for Business Server**, and from the **Action** menu select **Publish**.
    
    Verify that the **Trusted Application Pool** has been created successfully and is associated with the correct Front End pool. 
    

