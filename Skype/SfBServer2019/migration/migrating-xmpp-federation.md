---
title: "Migrating XMPP federation"
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 11/17/2018
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Previous versions provided an extensible messaging and presence protocol (XMPP) gateway that could be deployed as a separate server role to allow federating with XMPP deployments. In Skype for Business Server 2019, the XMPP functionality can be deployed as a feature. XMPP functionality is installed in two parts: as an XMPP proxy that runs on the Skype for Business Server 2019 Edge Server, and the XMPP Gateway that runs on the Skype for Business Server 2019 Front End Server."
---

# Migrating XMPP federation

Previous versions provided an extensible messaging and presence protocol (XMPP) gateway that could be deployed as a separate server role to allow federating with XMPP deployments. In Skype for Business Server 2019, the XMPP functionality can be deployed as a feature. XMPP functionality is installed in two parts: as an XMPP proxy that runs on the Skype for Business Server 2019 Edge Server, and the XMPP Gateway that runs on the Skype for Business Server 2019 Front End Server. 
  
From a migration perspective, a user account can be moved to a Skype for Business Server 2019 pool and continue to use the legacy XMPP gateway. This is possible only when the XMPP federated partner is not configured in Skype for Business Server 2019.
  
In summary, if the legacy install has been deployed with XMPP Gateway and XMPP federation has been enabled, then to migrate to Skype for Business Server 2019:
  
1. Deploy a Skype for Business Server 2019 pool.
    
2. Deploy a Skype for Business Server 2019 Edge server.
    
3. Move all users to the Skype for Business Server 2019 pool
    
4. Create XMPP access policies and certificates for the Edge Server.
    
5. Enable XMPP federation in Skype for Business Server 2019. 
    
6. Update the DNS entries to point to the Skype for Business Server 2019 XMPP Gateway.
    

