---
title: "Update-CsAdminRole"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 42cc9cc2-c408-4d0c-814a-6c6367cba834
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Update-CsAdminRole
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Updates the role-based access control (RBAC) definitions stored in the Central Management database without affecting any other database tables. This cmdlet was introduced in Lync Server 2013.
  
```
Update-CsAdminRole [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 updates the RBAC definitions stored in the Central Management database.
  
```
Update-CsAdminRole
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Update-CsAdminRole** cmdlet provides a way for you to update the RBAC role definitions stored in the Central Management database. This cmdlet is typically used in coexistence/migration scenarios where the Central Management database is currently located in a Microsoft Lync Server 2010 pool. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Update-CsAdminRole"}
  
 **Lync Server Control Panel:** The functions carried out by the **Update-CsAdminRole** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Update-CsAdminRole** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

None. The **Update-CsAdminRole** cmdlet does not return any data or objects. 
  

