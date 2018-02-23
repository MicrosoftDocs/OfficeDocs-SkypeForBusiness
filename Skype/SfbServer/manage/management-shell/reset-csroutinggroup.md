---
title: "Reset-CsRoutingGroup"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9a02d648-18fe-49a0-8c06-8cafedeb9700
description: "Enables administrators to reset a Windows fabric routing group that is not working correctly."
---

# Reset-CsRoutingGroup
[]
Enables administrators to reset a Windows fabric routing group that is not working correctly.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Reset-CsRoutingGroup -RoutingGroup <String> [-Binding <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-HostNameStorageService <String>] [-Lyss <SwitchParameter>] [-ResetType <Recreate | Permanent | Transient>] [-TargetFqdn <Fqdn>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 performs a transient on the routing group with the identity bef5fa3b-3c97-4af0-abe7-611deee7616c.
  
```
Reset-CsRoutingGroup -RoutingGroup "bef5fa3b-3c97-4af0-abe7-611deee7616c" -Type "Transient"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Reset-CsRoutingGroup cmdlet provides a way for administrators to reset Windows Fabric routing groups that are "missing" or are otherwise not working correctly. Missing routing groups can be identified by using the Get-CsPoolFabricState cmdlet and the FilterOnMissingReplicas parameter.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _RoutingGroup_ <br/> |Required  <br/> |System.String  <br/> |Globally unique identifier (GUID) of the routing group that needs to be reset. For example:  <br/>  `-RoutingGroup "bef5fa3b-3c97-4af0-abe7-611deee7616c"` <br/> |
| _Binding_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _HostNameStorageService_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _Lyss_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |PARAMVALUE: SwitchParameter  <br/> |
| _ResetType_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Hadr.ResetFabricRoutingGroupCmdlet+RgResetType  <br/> |Type of reset to be performed. Allowed values are:  <br/> Invalid  <br/> Permanent  <br/> Transient  <br/> |
| _TargetFqdn_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the pool containing the routing group that needs to be reset.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The Reset-CsRoutingGroup cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None. The Reset-CsRoutingGroup cmdlet does return objects or data.
  

