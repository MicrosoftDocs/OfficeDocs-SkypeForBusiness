---
title: "Migration process"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 13d71f4b-9d5e-4ea3-9e93-29fdad7ac68f
description: "The recommended and supported migration procedure for Lync Server 2013 is side-by-side migration. This topic describes why you should use side-by-side migration and also includes information about coexistence testing."
---

# Migration process
[]
The recommended and supported migration procedure for Lync Server 2013 is side-by-side migration. This topic describes why you should use side-by-side migration and also includes information about coexistence testing.
  
## Side-By-Side Migration

In nearly every migration, you should use the side-by-side migration path. In a side-by-side migration, you deploy a new server with Lync Server 2013 alongside a corresponding server that is running Lync Server 2010, and then transfer operations to the new server. If it becomes necessary to roll back to Lync Server 2010, you have only to shift operations back to the original servers. Be aware that in this situation any new meetings scheduled with upgraded clients will not work, and the clients would also need to be downgraded.
  
## Coexistence Testing

After you have deployed Lync Server 2013 in parallel with Lync Server 2010, the deployment represents a coexistence testing state of Lync Server 2013 and Lync Server 2010. While in this state, it is important to test and ensure that services are started, each site can be administered, and clients can communicate with current and legacy users. Prior to the migration of all users, it is very important that you understand the state of each deployment and ensure that each deployment is functional and working properly. Typically, the coexistence testing phase exists throughout the pilot testing of Lync Server 2013. Legacy users are moved to Lync Server 2013 for a period of time to ensure that application compatibility and features and functions are working properly. After pilot testing, users and applications are moved to the production version of Lync Server 2013, and the legacy pools and applications of Lync Server 2010 are retired.
  

