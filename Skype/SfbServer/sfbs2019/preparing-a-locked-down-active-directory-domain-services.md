---
title: "Preparing a locked-down Active Directory Domain Services in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 68bde963-3fa3-4102-88d6-ac931c1dd2d7
description: "Organizations often lock down Active Directory Domain Services to help mitigate security risks. However, a locked-down Active Directory environment can limit the permissions that Lync Server 2013 requires. Properly preparing a locked-down Active Directory environment for Lync Server 2013 involves some additional considerations and steps."
---

# Preparing a locked-down Active Directory Domain Services in Lync Server 2013
[]
Organizations often lock down Active Directory Domain Services to help mitigate security risks. However, a locked-down Active Directory environment can limit the permissions that Lync Server 2013 requires. Properly preparing a locked-down Active Directory environment for Lync Server 2013 involves some additional considerations and steps. 
  
Two common ways in which permissions are limited in a locked-down Active Directory environment are as follows:
  
- Authenticated user access control entries (ACEs) are removed from containers.
    
- Permissions inheritance is disabled on containers of User, Contact, InetOrgPerson, or Computer objects.
    
## In This Section

- [Authenticated user permissions are removed in Lync Server 2013](authenticated-user-permissions-are-removed.md)
    
- [Permissions inheritance Is disabled on computers, users, or InetOrgPerson containers in Lync Server 2013](permissions-inheritance-is-disabled-on-computers-users-or-inetorgperson-containe.md)
    

