---
title: "Remove-CsManagementConnection"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2fe69a3d-0154-418f-b6ee-99a88e5a9c7d
description: "Resets the management connection to the Active Directory service control point for the Central Management store. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsManagementConnection
 
Resets the management connection to the Active Directory service control point for the Central Management store. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsManagementConnection [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 removes the existing management connection information and replaces it with the default connection information stored in Active Directory.
  
```
Remove-CsManagementConnection
```

## Detailed Description

Configuration data for Skype for Business Server 2015 is stored in the Central Management store; it is crucial that both Windows PowerShell and the management replication services be able to locate this database. When you install Skype for Business Server 2015, a service control point is created in Active Directory Domain Services that provides location information for this database. Typically, computers rely on this service control point in order to connect to the Central Management store. To see the details behind this connection (that is, if you want to know which computer the Central Management store is running on, as well information about the SQL Server connection to that Central Management store), you can run the **Get-CsManagementConnection** cmdlet.
  
As a general rule, you will not need to change your management connection. However, it is possible that you might need to temporarily use a new management connection. When you are ready to switch back to the default connection all you need to do is run the **Remove-CsManagementConnection** cmdlet; this cmdlet erases the current connection information and replaces it with the connection information stored in the Active Directory service control point. This means you do not have to recreate the original connection information; the **Remove-CsManagementConnection** cmdlet will do that for you.
  
Note that no problems will occur if you call this cmdlet while using the default connection. If you do so, you will simply continue to use the default connection information stored in Active Directory. Note, too that this cmdlet only affects the management connection information for your current Windows PowerShell session: any changes to the management connection are limited to your local computer and local instance of Windows PowerShell.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

None. The **Remove-CsManagementConnection** cmdlet does not accept pipelined input.
  
## Return Types

None. Instead, the **Remove-CsManagementConnection** cmdlet deletes instances of the Microsoft.Rtc.Management.Xds.ManagementConnection object.
  
## See also

#### 

[Get-CsManagementConnection](get-csmanagementconnection.md)
  
[Remove-CsConfigurationStoreLocation](remove-csconfigurationstorelocation.md)
  
[Set-CsManagementConnection](set-csmanagementconnection.md)

