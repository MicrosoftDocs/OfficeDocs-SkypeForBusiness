---
title: Remove-CsUserStoreBackupData
ms.prod: SKYPEFORBUSINESS
ms.assetid: 71c8e8ee-61c7-4737-bdac-8cfc80bac126
---


# Remove-CsUserStoreBackupData
[]
Removes outdated information from the specified user store. "Outdated information" refers user data from a Registrar pool no longer paired with the specified user store. For example, suppose Pools A and B were once paired; now, however, that association has been changed, and Pools A and C are paired. When run against Pool A, the Remove-CsUserStoreBackupData cmdlet will remove information about users from Pool B. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Remove-CsUserStoreBackupData -PoolFqdn <Fqdn> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 removes outdated user store information stored by the pool atl-cs-001.litwareinc.com and its associated backup pool.
  
    
    

```

Remove-CsUserStoreBackupData -PoolFqdn "atl-cs-001.litwareinc.com"
```


## Detailed Description
<a name="DetailedDescription"> </a>

Skype for Business Server 2015 enables you to associate a pair of pools. When you do this, each pool maintains two sets of user information: information about the users homed on the pool in question and information about the users homed on the associated pool. Maintaining both sets of user information allows Pool B to register and service the users from Pool A should Pool A need to be failed over.
  
    
    
If you later change the association between these two pools, the "extra" user data is not automatically deleted from the two pools; for example, Pool A will continue to store user data for Pool B. (However, this data will no longer be updated and replicated.) The **Remove-CsUserStoreBackupData** cmdlet enables you to delete the data from Pool B that is no longer needed on Pool A.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the **Remove-CsUserStoreBackupData** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _PoolFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the pool where "outdated" user information should be removed. For example:  <br/>  `-PoolFqdn "atl-cs-001.litwareinc.com"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None. The **Remove-CsUserStoreBackupData** cmdlet does not accept pipelined input.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

None.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Get-CsBackupServiceStatus](get-csbackupservicestatus.md)
