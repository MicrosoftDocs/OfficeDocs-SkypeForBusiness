---
title: "Remove-CsCallViaWorkPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f2a7b538-1d95-4def-a247-fc9619290a97
description: "Use the Remove-CsCallViaWorkPolicy cmdlet to delete an existing call via work policy. Call via work policies enable and manage the characteristics of outbound calls placed through the Skype for Business client."
---

# Remove-CsCallViaWorkPolicy
[]
Use the **Remove-CsCallViaWorkPolicy** cmdlet to delete an existing call via work policy. Call via work policies enable and manage the characteristics of outbound calls placed through the Skype for Business client.
  
```
Remove-CsCallViaWorkPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

This example removes a per-user scoped policy named "CvWStandardPolicy".
  
```
Remove-CsCallViaWorkPolicy -Identity CvWStandardPolicy
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
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> | Specifies the identity of the policy to be removed. Call via work policies can be specified at the global, site, or per-user scope. <br/>  Global syntax: `-Identity Global` <br/>  The global policy will not be removed, but the parameters will be reset to the defaults. <br/>  Site syntax: `-Identity Site:Redmond` <br/>  Per-user syntax: `-Identity CallviaWorkStandard` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |This parameter is reserved for internal Microsoft use.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None.
  
## Return Types
<a name="ReturnTypes"> </a>

None.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Set-CsCallViaWorkPolicy](set-cscallviaworkpolicy.md)
  
[New-CsCallViaWorkPolicy](new-cscallviaworkpolicy.md)
  
[Grant-CsCallViaWorkPolicy](grant-cscallviaworkpolicy.md)
  
[Get-CsCallViaWorkPolicy](get-cscallviaworkpolicy.md)

