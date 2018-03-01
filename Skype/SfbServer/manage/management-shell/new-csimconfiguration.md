---
title: "New-CsImConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f75c533b-24b3-4660-95c3-995075a779c0
description: "Use the New-CsImConfiguration cmdlet to create a new Instant Messaging (IM) configuration."
---

# New-CsImConfiguration
 
Use the **New-CsImConfiguration** cmdlet to create a new Instant Messaging (IM) configuration.
  
```
New-CsImConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableOfflineIm <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

This example creates a new IM configuration for the Redmond site and enables the offline IM feature in that new configuration.
  
```
New-CsImConfiguration -Identity "site:Redmond" -EnableOfflineIm $true
```

## Detailed Description
<a name="DetailedDescription"> </a>

Use the **New-CsImConfiguration** cmdlet to create a new Instant Messaging (IM) configuration.
  
To return a list of all the Role-Based Access Control (RBAC) roles a cmdlet has been assigned to (including any custom RBAC roles you have created), run the following command from the Windows PowerShell prompt.
  
```
Get-CsAdminRole | Where-Object {$_.Cmdlets -Match "<DesiredCmdletName>"}
```

## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Specifies the unique identifier of the new IM configuration.  <br/> You can't create a new Global IM configuration, but you can modify it with the **Set-CsImConfiguration** cmdlet. <br/> To create an IM configuration at the site scope, use the prefix "site:" followed by the site name. For example: `-Identity "site:Redmond"` <br/> To create an IM configuration at the service scope, use the prefix "service:" followed by the service name. For example: `-Identity "service:Registrar Contoso.RegistrarPool.com"` <br/> If a configuration exists with the same  _Identity_, the cmdlet will fail.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableOfflineIm_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to $true, offline Instant Messaging is enabled. If $false, offline Instant Messaging is disabled. The default is $false.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |Specifies the globally unique identifier (GUID) of the Skype for Business Online tenant account on which the cmdlet will operate. For example: `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"`. You can return the tenant ID for each of your Skype for Business Online tenants by running this command: `Get-CsTenant | Select-Object DisplayName, TenantID`.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

