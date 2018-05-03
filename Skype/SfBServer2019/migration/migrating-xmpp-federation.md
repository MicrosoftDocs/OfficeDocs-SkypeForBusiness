---
title: "Migrating XMPP federation"
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b8d2b4b9-d0ed-4b48-820a-2c257fbdd2fb
description: "Previous versions of Lync Server and Office Communications Server provided an extensible messaging and presence protocol (XMPP) gateway that could be deployed as a separate server role to allow federating with XMPP deployments. In Lync Server 2013, the XMPP functionality can be deployed as a feature. XMPP functionality is installed in two parts: as an XMPP proxy that runs on the Lync Server 2013 Edge Server, and the XMPP Gateway that runs on the Lync Server 2013 Front End Server."
---

# Migrating XMPP federation
[]
Previous versions of Lync Server and Office Communications Server provided an extensible messaging and presence protocol (XMPP) gateway that could be deployed as a separate server role to allow federating with XMPP deployments. In Lync Server 2013, the XMPP functionality can be deployed as a feature. XMPP functionality is installed in two parts: as an XMPP proxy that runs on the Lync Server 2013 Edge Server, and the XMPP Gateway that runs on the Lync Server 2013 Front End Server. 
  
From a migration perspective, a Lync Server user account can be moved to a Lync Server 2013 pool and continue to use the legacy XMPP gateway. This is possible only when the XMPP federated partner is not configured in Lync Server 2013.
  
In summary, if Lync Server 2010 has been deployed with the Office Communications Server 2007 R2 XMPP Gateway and XMPP federation has been enabled for legacy Lync Server 2010 users, to migrate the XMPP federation to Lync Server 2013:
  
1. Deploy a Lync Server 2013 pool.
    
2. Deploy a Lync Server 2013 Edge server.
    
3. Move all users to the Lync Server 2013 pool
    
4. Create XMPP access policies and certificates for the Edge Server.
    
5. Enable XMPP federation in Lync Server 2013. 
    
6. Update the DNS entries to point to the Lync Server 2013 XMPP Gateway.
    

