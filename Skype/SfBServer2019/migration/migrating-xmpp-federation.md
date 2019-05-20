---
title: "Migrating XMPP federation"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Previous versions provided an extensible messaging and presence protocol (XMPP) gateway that could be deployed as a separate server role to allow federating with XMPP deployments. The XMPP functionality is no longer available & deprecated in Skype for Business Server 2019. If you want to continue with the XMPP functionality, that can be availed in coexitence environment with legacy version (Skype for Business Server 2015/ Lync Server 2013). XMPP functionality is installed in two parts: as an XMPP proxy that runs on the legacy Edge Server, and the XMPP Gateway that runs on the legacy Front End Server."
---

# Migrating XMPP federation

Previous versions provided an extensible messaging and presence protocol (XMPP) gateway that could be deployed as a separate server role to allow federating with XMPP deployments. The XMPP functionality is no longer available and is deprecated in Skype for Business Server 2019. If you want to continue with the XMPP functionality, you can do so in a coexistence environment with a legacy version (Skype for Business Server 2015 or Lync Server 2013). XMPP functionality is installed in two parts: as an XMPP proxy that runs on the legacy Edge Server, and the XMPP Gateway that runs on the legacy Front End Server. 
  
From a migration perspective, users who want to avail the XMPP feature should remain in the legacy server and should not be moved to a Skype for Business Server 2019 pool but continue to use the legacy XMPP gateway. This is possible only when the XMPP federated partner is configured in Skype for Business Server 2015 or Lync Server 2013. You should not migrate the legacy Edge Server to Skype for Business Server 2019 if you want to continue with XMPP functionality. However, you can have coexistence of the legacy Edge Server (with XMPP Proxy) and the Skype for Business 2019 Edge Server.
  

    

