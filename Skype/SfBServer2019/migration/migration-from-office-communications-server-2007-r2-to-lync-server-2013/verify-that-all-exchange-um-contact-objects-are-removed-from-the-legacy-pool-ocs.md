---
title: "Verify that all Exchange UM Contact objects are removed from the legacy pool [OCS 2007 R2 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5a813169-0ed7-4f84-a242-ed2cd4ea5c43
description: "Use either the OCSUmUtil tool or the Get-CsExumContact cmdlet to verify that Exchange UM contact objects have been removed from the legacy Office Communications Server 2007 R2 pool. OCSUmUtil is located in the following folder:"
---

# Verify that all Exchange UM Contact objects are removed from the legacy pool [OCS 2007 R2 to W15]
[]
Use either the **OCSUmUtil** tool or the **Get-CsExumContact** cmdlet to verify that Exchange UM contact objects have been removed from the legacy Office Communications Server 2007 R2 pool. **OCSUmUtil** is located in the following folder: 
  
%Program Files%\Common Files\Lync Server 2013\Support\OcsUMUtil.exe
  
 **OCSUmUtil** must be run from a user account that has: 
  
- Membership in the RTCUniversalServerAdmins and RTCUniversalUserAdmins group (which includes rights to read Exchange Server Unified Messaging settings)
    
- Domain rights to create contact objects in the specified organizational unit (OU) container
    
For details about using the **Get-CsExumContact** cmdlet, see [Get-CsExUmContact](../../lync-server-management-shell/lync-server-2013-cmdlets-by-category/get-csexumcontact.md) in the Lync Server Management Shell documentation. 
  

