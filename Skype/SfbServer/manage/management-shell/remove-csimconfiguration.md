---
title: "Remove-CsImConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: daa28340-9606-4854-9162-8e233d185c7d
description: "Use the Remove-CsImConfiguration cmdlet to remove an Instant Messaging (IM) configuration."
---

# Remove-CsImConfiguration
 
Use the **Remove-CsImConfiguration** cmdlet to remove an Instant Messaging (IM) configuration.
  
```
Remove-CsImConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

This example removes the IM configuration for the Registrar pool at "Contoso.RegistrarPool.com".
  
```
Remove-CsImConfiguration -Identity "service:Registrar Contoso.RegistrarPool.com"
```

## Detailed Description
<a name="DetailedDescription"> </a>

Use the **Remove-CsImConfiguration** cmdlet to remove an Instant Messaging (IM) configuration.
  
To return a list of all the Role-Based Access Control (RBAC) roles a cmdlet has been assigned to (including any custom RBAC roles you have created), run the following command from the Windows PowerShell prompt.
  
```
Get-CsAdminRole | Where-Object {$_.Cmdlets -Match "<DesiredCmdletName>"}
```

## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Specifies the unique identity of the IM configuration to be removed.  <br/> You can't remove the Global IM configuration, but you can modify it with the **Set-CsImConfiguration** cmdlet. <br/> To remove an IM configuration at the site scope, use the prefix "site:" followed by the site name. For example: `-Identity "site:Redmond"` <br/> To remove an IM configuration at the service scope, use the prefix "service:" followed by the service name. For example: `-Identity "service:Registrar Contoso.RegistrarPool.com"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Specifies the globally unique identifier (GUID) of the Skype for Business Online tenant account on which the cmdlet will operate. For example: `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"`. You can return the tenant ID for each of your Skype for Business Online tenants by running this command: `Get-CsTenant | Select-Object DisplayName, TenantID`.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

