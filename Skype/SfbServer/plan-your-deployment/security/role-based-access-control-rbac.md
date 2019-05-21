---
title: "Role-based access control (RBAC) for Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: d01fba36-eb7e-4de9-9bba-5102ae157820
description: "Skype for Business Server includes Role-Based Access Control (RBAC) groups to enable you to delegate administrative tasks while maintaining high standards for security. These groups are created during forest preparation. For details about forest preparation, see Active Directory Domain Services for Skype for Business Server. For details about the specific groups created by forest preparation, see Changes made by forest preparation in Skype for Business Server in the Deployment documentation."
---

# Role-based access control (RBAC) for Skype for Business Server
 
Skype for Business Server includes Role-Based Access Control (RBAC) groups to enable you to delegate administrative tasks while maintaining high standards for security. These groups are created during forest preparation. For details about forest preparation, see [Active Directory Domain Services for Skype for Business Server](active-directory-domain-services.md). For details about the specific groups created by forest preparation, see [Changes made by forest preparation in Skype for Business Server](../../schema-reference/active-directory-schema-extensions-classes-and-attributes/changes-made-by-forest-preparation.md) in the Deployment documentation.
  
With RBAC, administrative privilege is granted by assigning users to pre-defined administrative roles, including the 11 predefined roles that cover many common administrative tasks. Each role is associated with a specific list of Lync Server Management Shell cmdlets that users in that role are allowed to run. You can use RBAC to follow the principle of "least privilege," in which users are given only the administrative abilities that their jobs require. 
  
More details on RBAC roles can be found at: [Planning for role-based access control](https://docs.microsoft.com/lyncserver/lync-server-2013-planning-for-role-based-access-control)
