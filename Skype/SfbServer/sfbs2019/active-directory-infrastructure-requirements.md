---
title: "Active Directory infrastructure requirements for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c2086f7b-662f-4179-ab99-2c0311ebd903
description: "Before you start the process of preparing Active Directory Domain Services for Lync Server 2013, make sure that your Active Directory infrastructure meets the following prerequisites:"
---

# Active Directory infrastructure requirements for Lync Server 2013
[]
Before you start the process of preparing Active Directory Domain Services for Lync Server 2013, make sure that your Active Directory infrastructure meets the following prerequisites:
  
- All domain controllers (which include all global catalog servers) in the forest where you deploy Lync Server run one of the following operating systems: 
    
  - Windows Server 2012 R2 operating system
    
  - Windows Server 2012 operating system
    
  - Windows Server 2008 R2 operating system
    
  - Windows Server 2008 operating system
    
  - Windows Server 2008 Enterprise 32-Bit
    
  - 32-bit or 64-bit versions of the Windows Server 2003 R2 operating system
    
  - 32-bit or 64-bit versions of the Windows Server 2003 operating system
    
- All domains in which you deploy Lync Server are raised to a domain functional level of Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008, or at least Windows Server 2003. 
    
- The forest in which you deploy Lync Server is raised to a forest functional level of Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008, or at least Windows Server 2003. 
    
    > [!NOTE]
    > To change your domain or forest functional level, see "Raising domain and forest functional levels" in the TechNet Library at [https://go.microsoft.com/fwlink/p/?LinkId=263775](https://go.microsoft.com/fwlink/p/?LinkId=263775). 
  
- A global catalog is deployed in every domain where you deploy Lync Server computers or users.
    
Lync Server 2013 supports the universal groups in the Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008, and Windows Server 2003 operating systems. Members of universal groups can include other groups and accounts from any domain in the domain tree or forest and can be assigned permissions in any domain in the domain tree or forest. Universal group support, combined with administrator delegation, simplifies the management of a Lync Server deployment. For example, it is not necessary to add one domain to another to enable an administrator to manage both.
  

