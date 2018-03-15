---
title: "Get-CsAddressBookConfiguration for Address Book management in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: bd62f916-caf3-4e10-ada4-631bbb331ef1
description: "Who can run this cmdlet: By default, members of the following groups are authorized to run the Get-CsAddressBookConfiguration cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:"
---

# Get-CsAddressBookConfiguration for Address Book management in Lync Server 2013
[]
Who can run this cmdlet: By default, members of the following groups are authorized to run the Get-CsAddressBookConfiguration cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:
  
```
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsAddressBookConfiguration"}

```

The cmdlet Get-CsAddressBookConfiguration returns information about a configuration that already exists. 
  
For example:
  
```
Get-CsAddressBookConfiguration -Identity site:Redmond

```

Combining the functionality of Get-CsAddressBookConfiguration and Set-CsAddressBookConfiguration allows the administrator to define which configurations to modify and then apply the modifications. For example, this combined:
  
```
Get-CsAddressBookConfiguration -Filter site:* | Set-CsAddressBookConfiguration -RunTimeOfDay 23:00

```

Returns all configurations in all sites and applies the RunTimeOfDay of 23:00 hours to the configurations.
  
## See also

#### 

[Get-CsAddressBookConfiguration](get-csaddressbookconfiguration.md)

