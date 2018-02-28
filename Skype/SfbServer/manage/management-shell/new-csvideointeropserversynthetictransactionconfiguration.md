---
title: "New-CsVideoInteropServerSyntheticTransactionConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 10fe9f5b-af78-40e1-ac6f-44d39705ffab
description: "Use the New-CsVideoInteropServerSyntheticTransactionConfiguration cmdlet to create a new Video Interop Server (VIS) synthetic transaction configuration. The cmdlet can be applied at the Global, Site, and Service levels."
---

# New-CsVideoInteropServerSyntheticTransactionConfiguration
[]
Use the **New-CsVideoInteropServerSyntheticTransactionConfiguration** cmdlet to create a new Video Interop Server (VIS) synthetic transaction configuration. The cmdlet can be applied at the Global, Site, and Service levels.
  
```
New-CsVideoInteropServerSyntheticTransactionConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WatcherNodeFqdns <PSListModifier>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

This example creates a new Video Interop Server synthetic transaction configuration with two watcher nodes and scoped for the Redmond site.
  
```
New-CsVideoInteropServerSyntheticTransactionConfiguration -Identity "site:Redmond" -WatcherNodeFqdns "atl-cs-001.contoso.com", "atl-cs-002.contoso.com"
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
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The  _Identity_ parameter specifies the Video Interop Server synthetic transaction configuration to create. Video Interop Server synthetic transaction configuration settings can be configured at the global, site, or service scope. To refer to the global instance, use this syntax: <br/>  `-Identity "Global"` <br/> Use this syntax to refer to a collection at the site scope:  <br/>  `-Identity "site:Redmond"` <br/> Wildcard characters such as the asterisk (*) cannot be used with the  _Identity_ parameter. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _WatcherNodeFqdns_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Specifies the FQDN of the watcher node relevant to the synthetic transaction. For example: -WatcherNodeFqdns "atl-cs-001.contoso.com". Watcher nodes are computers that periodically use System Center Operations Manager and Skype for Business Server synthetic transactions to verify that Skype for Business Server components are working as expected. For more information, see [New-CsWatcherNodeConfiguration](new-cswatchernodeconfiguration.md).  <br/> To enter multiple values and overwrite any existing entries, use the following syntax:  `<value1>,<value2>...`. If the values contain spaces or otherwise require quotation marks, you need to use the following syntax:  `"<value1>","<value2>"...`.  <br/> To add or remove one or more values without affecting any existing entries, use the following syntax:  `@{Add="<value1>","<value2>"...; Remove="<value1>","<value2>"...}`.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None
  
## Return Types
<a name="ReturnTypes"> </a>

Returns a  `VideoInteropServerSyntheticTransactionConfiguration` object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsVideoInteropServerSyntheticTransactionConfiguration](get-csvideointeropserversynthetictransactionconfiguration.md)
  
[Set-CsVideoInteropServerSyntheticTransactionConfiguration](set-csvideointeropserversynthetictransactionconfiguration.md)
  
[Remove-CsVideoInteropServerSyntheticTransactionConfiguration](remove-csvideointeropserversynthetictransactionconfiguration.md)
  
[Test-CsP2PVideoInteropServerSipTrunkAV](test-csp2pvideointeropserversiptrunkav.md)

