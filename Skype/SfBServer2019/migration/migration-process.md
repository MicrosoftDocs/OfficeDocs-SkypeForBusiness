---
title: "Migration process"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "The recommended and supported migration procedure for Skype for Business Server 2019 is side-by-side migration. This topic describes why you should use side-by-side migration and also includes information about coexistence testing."
---

# Migration process

The recommended and supported migration procedure for Skype for Business Server 2019 is side-by-side migration. This topic describes why you should use side-by-side migration and also includes information about coexistence testing.
  
## Side-By-Side Migration

In nearly every migration, you should use the side-by-side migration path. In a side-by-side migration, you deploy a new server with Skype for Business Server 2019 alongside a corresponding server that is running a previous version, and then transfer operations to the new server. If it becomes necessary to roll back to the previous version, you have only to shift operations back to the original servers. Be aware that in this situation any new meetings scheduled with upgraded clients will not work, and the clients would also need to be downgraded.
  
## Coexistence Testing

After you have deployed Skype for Business Server 2019 in parallel with the previous version, the deployment represents a coexistence testing state of Skype for Business Server 2019 and the previous version. While in this state, it is important to test and ensure that services are started, each site can be administered, and clients can communicate with current and legacy users. Prior to the migration of all users, it is very important that you understand the state of each deployment and ensure that each deployment is functional and working properly. Typically, the coexistence testing phase exists throughout the pilot testing of Skype for Business Server 2019. Legacy users are moved to Skype for Business Server 2019 for a period of time to ensure that application compatibility and features and functions are working properly. After pilot testing, users and applications are moved to the production version of Skype for Business Server 2019, and the legacy pools and applications of the previous version are retired.
  
