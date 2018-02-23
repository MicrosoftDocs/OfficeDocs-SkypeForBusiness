---
title: "Set-CsVideoInteropServerSyntheticTransactionConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c257fe1f-7d35-4d73-b960-897baf999ae1
description: "Use the Set-CsVideoInteropServerSyntheticTransactionConfiguration cmdlet to modify an existing Video Interop Server (VIS) synthetic transaction configuration."
---

# Set-CsVideoInteropServerSyntheticTransactionConfiguration
[]
Use the **Set-CsVideoInteropServerSyntheticTransactionConfiguration** cmdlet to modify an existing Video Interop Server (VIS) synthetic transaction configuration.
  
```
Set-CsVideoInteropServerSyntheticTransactionConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

This example sets the Global configuration to trust connections from the  _WatcherNode_ "watchernode.contoso.com".
  
```
Set-CsVideoInteropServerSyntheticTransactionConfiguration -Identity Global -WatcherNodeFqdns "watchernode.contoso.com"
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
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identity assigned to the VIS configuration when it was created. VIS settings can be configured at the global, site, or service scope (for the VideoInteropServer service only). To refer to the global instance, use this syntax:  <br/>  `-Identity "Global"` <br/> Use this syntax to refer to a collection at the site scope:  <br/>  `-Identity "site:Redmond"` <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _WatcherNodeFqdns_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Specifies the URL of the watcher node relevant to the synthetic transaction. For example: `-WatcherNodeFqdns "atl-cs-001.Contoso.com"`. Watcher nodes are computers that periodically use Microsoft System Center Operations Manager and Skype for Business Server synthetic transactions to verify that Skype for Business Server components are working as expected. For more information, see [New-CsWatcherNodeConfiguration](new-cswatchernodeconfiguration.md).  <br/> To enter multiple values and overwrite any existing entries, use the following syntax:  `<value1>,<value2>...`. If the values contain spaces or otherwise require quotation marks, you need to use the following syntax:  `"<value1>","<value2>"...`.  <br/> To add or remove one or more values without affecting any existing entries, use the following syntax:  `@{Add="<value1>","<value2>"...; Remove="<value1>","<value2>"...}`.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

Accepts pipelined instances of the  `VideoInteropServerSyntheticTransactionConfiguration` object.
  
## Return Types
<a name="ReturnTypes"> </a>

None.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsVideoInteropServerSyntheticTransactionConfiguration](get-csvideointeropserversynthetictransactionconfiguration.md)
  
[New-CsVideoInteropServerSyntheticTransactionConfiguration](new-csvideointeropserversynthetictransactionconfiguration.md)
  
[Remove-CsVideoInteropServerSyntheticTransactionConfiguration](remove-csvideointeropserversynthetictransactionconfiguration.md)
  
[Test-CsP2PVideoInteropServerSipTrunkAV](test-csp2pvideointeropserversiptrunkav.md)

