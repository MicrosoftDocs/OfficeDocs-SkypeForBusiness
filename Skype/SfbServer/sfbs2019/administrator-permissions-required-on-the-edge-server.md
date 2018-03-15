---
title: "Administrator Permissions Required on the Edge Server"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: eede7bfb-a337-4f94-a02e-f20ae51f3c5f
description: "Issue: Your account does not have the permissions necessary on the Edge Server to run the Lync rule checks."
---

# Administrator Permissions Required on the Edge Server
[]
 **Issue:** Your account does not have the permissions necessary on the Edge Server to run the Lync rule checks. 
  
## Description of the Issue

Your account is not a member of the local "Administrators" security group on the Edge Server. You will not be able to run all Lync checks on the Edge Server without administrator equivalent permissions.
  
## Issue Resolution

To resolve this issue, log on using an account that is a member of the local "Administrators" security group (or an account with equivalent permissions) on the Edge Server.
  
## See also

#### 

[Group membership requirements for Lync Server 2013](group-membership-requirements.md)

