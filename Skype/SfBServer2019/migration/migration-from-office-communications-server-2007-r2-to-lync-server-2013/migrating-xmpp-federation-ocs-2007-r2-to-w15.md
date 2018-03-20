---
title: "Migrating XMPP federation [OCS 2007 R2 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7368ee8f-a201-4d3a-b4e8-68396b156d4d
description: "Previous versions of Office Communications Server provided an extensible messaging and presence protocol (XMPP) gateway that could be deployed as a separate server role to allow federating with XMPP deployments. In Lync Server 2013, the XMPP functionality can be deployed as a feature. XMPP functionality is installed in two parts: as an XMPP proxy that runs on the Lync Server 2013 Edge Server, and the XMPP Gateway that runs on the Lync Server 2013 Front End Server."
---

# Migrating XMPP federation [OCS 2007 R2 to W15]
[]
Previous versions of Office Communications Server provided an extensible messaging and presence protocol (XMPP) gateway that could be deployed as a separate server role to allow federating with XMPP deployments. In Lync Server 2013, the XMPP functionality can be deployed as a feature. XMPP functionality is installed in two parts: as an XMPP proxy that runs on the Lync Server 2013 Edge Server, and the XMPP Gateway that runs on the Lync Server 2013 Front End Server. 
  
From a migration perspective, a Office Communications Server 2007 R2 user account can be moved to a Lync Server 2013 pool and continue to use the Office Communications Server 2007 R2 XMPP gateway. This is possible only when the XMPP federated partner is not configured in Lync Server 2013.
  
In summary, if Office Communications Server has been deployed with the Office Communications Server 2007 R2 XMPP Gateway and XMPP federation has been enabled for legacy Office Communications Server 2007 R2 users, to migrate the XMPP federation to Lync Server 2013:
  
1. Deploy a Lync Server 2013 pool.
    
2. Deploy a Lync Server 2013 Edge server.
    
3. Move all users to the Lync Server 2013 pool.
    
4. Create XMPP access policies and certificates for the Edge Server.
    
5. Enable XMPP federation in Lync Server 2013. 
    
6. Update the DNS entries to point to the Lync Server 2013 XMPP Gateway.
    

