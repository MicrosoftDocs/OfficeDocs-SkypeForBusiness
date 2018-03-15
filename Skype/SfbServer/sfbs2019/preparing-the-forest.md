---
title: "Preparing the forest for Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3d188fcb-c64e-46cf-a3a7-9e3ebefed7fd
description: "Forest preparation creates Active Directory global settings and objects and Active Directory universal groups for use by Lync Server 2013, and grants suitable access permissions on the Active Directory objects. For a description of the universal groups and the global settings and objects created by forest preparation, see Changes made by forest preparation in Lync Server 2013."
---

# Preparing the forest for Lync Server 2013
[]
Forest preparation creates Active Directory global settings and objects and Active Directory universal groups for use by Lync Server 2013, and grants suitable access permissions on the Active Directory objects. For a description of the universal groups and the global settings and objects created by forest preparation, see [Changes made by forest preparation in Lync Server 2013](changes-made-by-forest-preparation.md).
  
Forest preparation also creates objects that contain property sets and display specifiers that are used by Lync Server 2013, and stores them in the Configuration container.
  
> [!IMPORTANT]
> Make sure that schema preparation changes have replicated to all domain controllers before performing the forest preparation procedure. If replication is not completed, an error occurs. 
  
If you are performing a new Lync Server deployment, you must store global settings in the Configuration container. If you are upgrading from an earlier version and you still store global settings in the System container, you can continue to use the System container. 
  
You must be a member of the Enterprise Admins or Domain Admins group for the forest root domain to perform this procedure.
  
## In this section

- [Running forest preparation for Lync Server 2013](running-forest-preparation.md)
    
- [Using cmdlets to reverse forest preparation for Lync Server 2013](using-cmdlets-to-reverse-forest-preparation.md)
    

