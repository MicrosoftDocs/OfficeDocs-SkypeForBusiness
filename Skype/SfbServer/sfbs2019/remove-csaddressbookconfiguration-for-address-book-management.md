---
title: "Remove-CsAddressBookConfiguration for Address Book management in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5d173ebe-ec4d-4640-8432-a25071ea9cc5
description: "Who can run this cmdlet: By default, members of the following groups are authorized to run the Remove-CsAddressBookConfiguration cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:"
---

# Remove-CsAddressBookConfiguration for Address Book management in Lync Server 2013
[]
Who can run this cmdlet: By default, members of the following groups are authorized to run the Remove-CsAddressBookConfiguration cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:
  
```
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsAddressBookConfiguration"}

```

As the name implies, Remove-CsAddressBookConfiguration will remove the configuration based on the defined Site Identity.
  
For example:
  
```
Remove-CsAddressBookConfiguration -Identity site:Redmond
```

## See also

#### 

[Remove-CsAddressBookConfiguration](remove-csaddressbookconfiguration.md)

