---
title: "Set-CsImConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 02eeff0e-c2d1-4839-951c-44ff8422892c
description: "Use the Set-CsImConfiguration cmdlet to modify an existing Instant Messaging (IM) configuration."
---

# Set-CsImConfiguration
 
Use the **Set-CsImConfiguration** cmdlet to modify an existing Instant Messaging (IM) configuration.
  
```
Set-CsImConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

This example modifies the existing Redmond site IM configuration to disable the offline IM feature.
  
```
Set-CsImConfiguration -Identity "site:Redmond" -EnableOfflineIm $false
```

## Detailed Description
<a name="DetailedDescription"> </a>

Use the **Set-CsImConfiguration** cmdlet to modify an existing Instant Messaging (IM) configuration.
  
To return a list of all the Role-Based Access Control (RBAC) roles a cmdlet has been assigned to (including any custom RBAC roles you have created), run the following command from the Windows PowerShell prompt.
  
```
Get-CsAdminRole | Where-Object {$_.Cmdlets -Match "<DesiredCmdletName>"}
```

## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableOfflineIm_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to $true, offline Instant Messaging is enabled. If $false, offline Instant Messaging is disabled. The default is $true.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Specifies the unique identity of the IM configuration to be modified.  <br/> To modify the global IM configuration you can either omit  _Identity_, or use the following syntax: `-Identity Global` <br/> To modify an IM configuration at the site scope, use the prefix "site:" followed by the site name. For example: `-Identity "site:Redmond"` <br/> To modify an IM configuration at the service scope, use the prefix "service:" followed by the service name. For example: `-Identity "service:Registrar Contoso.RegistrarPool.com"` <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Specifies the globally unique identifier (GUID) of the Skype for Business Online tenant account on which the cmdlet will operate. For example: `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"`. You can return the tenant ID for each of your Skype for Business Online tenants by running this command: `Get-CsTenant | Select-Object DisplayName, TenantID`.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

