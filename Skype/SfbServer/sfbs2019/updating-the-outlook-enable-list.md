---
title: "Updating the Outlook enable list in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: End User
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5db120dc-52f9-4dde-acb9-3824ae245086
description: "You can ensure that Online Meeting Add-in for Microsoft Lync 2013 always remains enabled for users by creating a policy that includes it in the Add-in Management List for Outlook. The Add-in Management List policy is included in the Office administrative template files for the Group Policy Management Console. It creates a registry key under HKCU\Software\Policies\Microsoft\Office\15.0\Outlook15\Resiliency\AddinList. You can add a value for the ucaddin.dll to this key, and configure the ucaddin.dll value so that it is always enabled and so that users cannot manually disable it"
---

# Updating the Outlook enable list in Lync Server 2013
[]
You can ensure that Online Meeting Add-in for Microsoft Lync 2013 always remains enabled for users by creating a policy that includes it in the Add-in Management List for Outlook. The Add-in Management List policy is included in the Office administrative template files for the Group Policy Management Console. It creates a registry key under HKCU\Software\Policies\Microsoft\Office\15.0\Outlook15\Resiliency\AddinList. You can add a value for the ucaddin.dll to this key, and configure the ucaddin.dll value so that it is always enabled and so that users cannot manually disable it
  
### To Add ucaddin.dll to the Outlook Add-in List

- To the AddinList registry key, located under HKCU\Software\Policies\Microsoft\Office\15.0\Outlook15\Resiliency\AddinList, add the following value:
    
  - Registry Type = REG_SZ 
    
  - Name = ucaddin.dll
    
  - Value = 1 (specifies that the add-in is always enabled and cannot be managed by the end user)
    

