---
title: "Remove-CsPresenceProvider"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7e8b540e-484f-4003-8665-18e2b3974f33
description: "Removes a presence provider previously configured for use in the organization. Presence providers represent the PresenceProviders property of a collection of user services configuration settings. This cmdlet was introduced in Lync Server 2013."
---

# Remove-CsPresenceProvider
[]
Removes a presence provider previously configured for use in the organization. Presence providers represent the PresenceProviders property of a collection of user services configuration settings. This cmdlet was introduced in Lync Server 2013.
  
```
Remove-CsPresenceProvider -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 removes the presence provider with the Identity "global/fabrikam.com".
  
```
Remove-CsPresenceProvider -Identity "global/fabrikam.com"
```

### Example 2

In Example 2, all the presence providers configured for use in the organization are removed. To do this, the command first calls the **Get-CsPresenceProvider** cmdlet without any parameters; that returns a collection of all the configured presence providers. That collection is then piped to the **Remove-CsPresenceProvider** cmdlet, which deletes each item (that is, each provider) in the collection.
  
```
Get-CsPresenceProvider | Remove-CsPresenceProvider
```

### Example 3

Example 3 shows how you can delete all the presence providers that have an Fqdn that includes the string value "fabrikam.com". To carry out this task, the command first uses the **Get-CsPresenceProvider** cmdlet to return a collection of all the available presence providers. That collection is then piped to the **Where-Object** cmdlet, which picks out only those providers where the Fqdn property includes (-match) the string value "fabrikam.com". In turn, that filtered collection is then piped to the **Remove-CsPresenceProvider** cmdlet, which deletes each provider in the filtered collection.
  
```
Get-CsPresenceProvider | Where-Object {$_.Fqdn -match "fabrikam.com"} | Remove-CsPresenceProvider
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **CsPresenceProvider** cmdlets are used to manage the PresenceProviders property found in the User Services configuration settings. Among other things, these settings are used to maintain presence information, including a collection of authorized presence providers. That collection is stored in the PresenceProviders property.
  
The **Remove-CsPresenceProvider** cmdlet enables you to remove a presence provider from the PresenceProviders property of one or more collections of User Services configuration settings.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Remove-CsPresenceProvider** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the presence provider to be removed. To remove a single provider, use the actual Identity of the provider, which includes both the scope and the provider Fqdn:  <br/>  `-Identity "global/fabrikam.com"` <br/> To remove all the presence providers configured at a particular scope, simply use the scope as the Identity. This syntax removes all the providers configured at the global scope:  <br/>  `-Identity "global"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Remove-CsPresenceProvider** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PresenceProvider#Decorated object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Remove-CsPresenceProvider** cmdlet deletes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PresenceProvider#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsPresenceProvider](get-cspresenceprovider.md)
  
[Get-CsUserServicesConfiguration](get-csuserservicesconfiguration.md)
  
[New-CsPresenceProvider](new-cspresenceprovider.md)
  
[Set-CsPresenceProvider](set-cspresenceprovider.md)

