---
title: Update-CsAdminRole
ms.prod: SKYPEFORBUSINESS
ms.assetid: 42cc9cc2-c408-4d0c-814a-6c6367cba834
---


# Update-CsAdminRole
[]
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

The **Update-CsAdminRole** cmdlet provides a way for you to update the RBAC role definitions stored in the Central Management database. This cmdlet is typically used in coexistence/migration.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the **Update-CsAdminRole** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None. The **Update-CsAdminRole** cmdlet does not accept pipelined input.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

None. The **Update-CsAdminRole** cmdlet does not return any data or objects.
  
    
    

