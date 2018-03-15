---
title: "Remove-CsVideoInteropServerSyntheticTransactionConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: de83b57a-84ce-47f8-aa18-b2f3adbab261
description: "Use the Remove-CsVideoInteropServerSyntheticTransactionConfiguration cmdlet to remove an existing Video Interop (VIS) server synthetic transaction configuration."
---

# Remove-CsVideoInteropServerSyntheticTransactionConfiguration
 
Use the **Remove-CsVideoInteropServerSyntheticTransactionConfiguration** cmdlet to remove an existing Video Interop (VIS) server synthetic transaction configuration.
  
```
Remove-CsVideoInteropServerSyntheticTransactionConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

This example removes the Video Interop Server synthetic transaction configuration for the Redmond site. 
  
```
Remove-CsVideoInteropServerSyntheticTransactionConfiguration -Identity "site:Redmond"
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
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Identity of the VIS configuration to be removed. VIS settings can be configured at the global, site, or service scope (for the VideoInteropServer service only). To refer to the global instance, use this syntax:  <br/>  `-Identity "Global"` <br/> Use this syntax to refer to a collection at the site scope:  <br/>  `-Identity "site:Redmond"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

Accepts pipelined instances of the  `VideoInteropServerSyntheticTransactionConfiguration` object.
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsVideoInteropServerSyntheticTransactionConfiguration](get-csvideointeropserversynthetictransactionconfiguration.md)
  
[Set-CsVideoInteropServerSyntheticTransactionConfiguration](set-csvideointeropserversynthetictransactionconfiguration.md)
  
[New-CsVideoInteropServerSyntheticTransactionConfiguration](new-csvideointeropserversynthetictransactionconfiguration.md)
  
[Test-CsP2PVideoInteropServerSipTrunkAV](test-csp2pvideointeropserversiptrunkav.md)

