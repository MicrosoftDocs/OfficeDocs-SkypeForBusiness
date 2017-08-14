---
title: Start-CsPool
ms.prod: SKYPEFORBUSINESS
ms.assetid: 6bf66ee1-33de-487a-94eb-026646c56ccd
---


# Start-CsPool
[]
Use the **Start-CsPool** cmdlet to start a Skype for Business Server pool. A pool is a set of servers, configured identically, that work together to provide services for a common group of users.
  
    
    

This cmdlet only applies to Front End Servers (not Edge servers).
```

Start-CsPool -PoolFqdn <Fqdn> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-QuorumLossRecovery <SwitchParameter>] [-SkipRoutingGroup <String[]>] [-SkipServer <String[]>] [-WhatIf [<SwitchParameter>]]

```


## Examples
<a name="Examples"> </a>


### Example 1

This example starts the "atl-cs-001.litwareinc.com" pool and skips one routing group specified by its GUID.
  
    
    

```

Start-CsPool -PoolFqdn "atl-cs-001.litwareinc.com" -SkipRoutingGroup "bef5fa3b-3c97-4af0-abe7-611deee7616c"
```


## Detailed Description
<a name="DetailedDescription"> </a>

To return a list of all the Role-Based Access Control (RBAC) roles a cmdlet has been assigned to (including any custom RBAC roles you have created), run the following command from the Windows PowerShell prompt.
  
    
    

```
Get-CsAdminRole | Where-Object {$_.Cmdlets -Match "<DesiredCmdletName>"}
```


## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _PoolFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the pool being started. For example: `-PoolFqdn "atl-cs-001.litwareinc.com"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _QuorumLossRecovery_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If true ($True), user data is reloaded from the backup store for any routing groups currently in quorum loss. (A quorum loss occurs when neither a database nor its replicas are available.) The default is false ($False.)  <br/> |
| _SkipRoutingGroup_ <br/> |Optional  <br/> |System.String[]  <br/> |Specifies one or more routing groups by GUID to skip during startup. Use this parameter if one or more of the routing groups are having problems getting placed on servers.  <br/> Note that some of the users included in the skipped routing groups might not be able to sign in, or will have limited functionality.  <br/> For example, to specify a single routing group use the following syntax:  `-SkipRoutingGroup "bef5fa3b-3c97-4af0-abe7-611deee7616c"`. The specify more than one routing group use the syntax:  `-SkipRoutingGroup "bef5fa3b-3c97-4af0-abe7-611deee7616c","cid4de2-3d86-3be9-bcf8-700fesi3923q"`.  <br/> |
| _SkipServer_ <br/> |Optional  <br/> |System.String[]  <br/> |Specifies one or more servers to skip during startup. Use this parameter if one or more of the front end servers cannot be started. Note that there is a minimum number of servers required for the pool to be functional. The cmdlet will check for those conditions while trying to implement this parameter.  <br/> For example, to specify a single server use the following syntax:  `-SkipServer "AtlServerOne"`. To specify more than one server use the syntax:  `-SkipServer "AtlServerOne","AtlServerTwo"` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _ShowAll_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |PARAMVALUE: SwitchParameter  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

None
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Backup-CsPool](backup-cspool.md)
  
    
    
 [Get-CsPool](get-cspool.md)
