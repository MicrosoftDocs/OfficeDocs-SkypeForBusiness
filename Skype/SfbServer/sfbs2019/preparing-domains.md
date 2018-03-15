---
title: "Preparing domains for Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8eea541c-5f9d-4afc-92a8-a31d6f742544
description: "Domain preparation is the final step in preparing Active Directory Domain Services for Lync Server 2013. The domain preparation step adds the necessary access control entries (ACEs) to universal groups that grant permissions to host and manage users within the domain. Domain preparation creates ACEs on the domain root and three built-in containers: User, Computers, and Domain Controllers."
---

# Preparing domains for Lync Server 2013
[]
Domain preparation is the final step in preparing Active Directory Domain Services for Lync Server 2013. The domain preparation step adds the necessary access control entries (ACEs) to universal groups that grant permissions to host and manage users within the domain. Domain preparation creates ACEs on the domain root and three built-in containers: User, Computers, and Domain Controllers.
  
You can run domain preparation on any computer in the domain where you are deploying Lync Server. You must prepare every domain that will host Lync Server or users.
  
If permissions inheritance is disabled or authenticated user permissions are disabled in your organization, you must perform additional steps during domain preparation. For details, see [Preparing a locked-down Active Directory Domain Services in Lync Server 2013](preparing-a-locked-down-active-directory-domain-services.md).
  
If your organization uses organizational units (OU) instead of the three built-in containers (that is, Users, Computers, and Domain Controllers), you must grant read access to the OUs for the Authenticated Users group. Read access to the containers is required for domain preparation. If the Authenticated Users group does not have read access to the OU, run the **Grant-CsOuPermission** cmdlet as illustrated in the following code examples to grant read permissions for each OU. 
  
```
Grant-CsOuPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> -OU <DN of the OU > 
```

```
Grant-CsOuPermission -ObjectType "user","contact",inetOrgPerson" -OU "ou=Redmond,dc=contoso,dc=net"
```

For details about the **Grant-CsOuPermission** cmdlet, see the Lync Server Management Shell documentation. 
  
> [!TIP]
> For details about the ACEs created on the domain root and in the Users, Computers, and Domain Controllers containers, see [Changes made by domain preparation in Lync Server 2013](changes-made-by-domain-preparation.md). 
  
## In this section

- [Running domain preparation for Lync Server 2013](running-domain-preparation.md)
    
- [Using cmdlets to reverse domain preparation for Lync Server 2013](using-cmdlets-to-reverse-domain-preparation.md)
    

