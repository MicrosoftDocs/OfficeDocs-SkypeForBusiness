---
title: 'Lync Server 2013: Active Directory infrastructure requirements'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Active Directory infrastructure requirements
ms:assetid: c2086f7b-662f-4179-ab99-2c0311ebd903
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412955(v=OCS.15)
ms:contentKeyID: 48185318
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Active Directory infrastructure requirements for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-11-07_

Before you start the process of preparing Active Directory Domain Services for Lync Server 2013, make sure that your Active Directory infrastructure meets the following prerequisites:

  - All domain controllers (which include all global catalog servers) in the forest where you deploy Lync Server run one of the following operating systems:
    
      - Windows Server 2012 R2 operating system
    
      - Windows Server 2012 operating system
    
      - Windows Server 2008 R2 operating system
    
      - Windows Server 2008 operating system
    
      - Windows Server 2008 Enterprise 32-Bit
    
      - 32-bit or 64-bit versions of the Windows Server 2003 R2 operating system
    
      - 32-bit or 64-bit versions of the Windows Server 2003 operating system

  - All domains in which you deploy Lync Server are raised to a domain functional level of Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008, or at least Windows Server 2003.

  - The forest in which you deploy Lync Server is raised to a forest functional level of Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008, or at least Windows Server 2003.
    
    <div>
    

    > [!NOTE]  
    > To change your domain or forest functional level, see "Raising domain and forest functional levels" in the TechNet Library at <A href="http://go.microsoft.com/fwlink/p/?linkid=263775">http://go.microsoft.com/fwlink/p/?LinkId=263775</A>.

    
    </div>

  - A global catalog is deployed in every domain where you deploy Lync Server computers or users.

Lync Server 2013 supports the universal groups in the Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008, and Windows Server 2003 operating systems. Members of universal groups can include other groups and accounts from any domain in the domain tree or forest and can be assigned permissions in any domain in the domain tree or forest. Universal group support, combined with administrator delegation, simplifies the management of a Lync Server deployment. For example, it is not necessary to add one domain to another to enable an administrator to manage both.

</div>

<span> </span>

</div>

</div>

</div>

