---
title: "Remove-CsCpsConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 546343e1-a2e4-4bc0-bf6d-c8ae9bb3e690
description: "Removes an existing Call Park service configuration. Call parking is a service that allows a user toparkan incoming phone call. Parking a call transfers it to a number in a specified range, or orbit, and then immediately places the call on hold. Anyone (not just the person who originally answered the call) can resume the conversation from any telephone simply by entering the correct number. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsCpsConfiguration
[]
Removes an existing Call Park service configuration. Call parking is a service that allows a user to "park" an incoming phone call. Parking a call transfers it to a number in a specified range, or orbit, and then immediately places the call on hold. Anyone (not just the person who originally answered the call) can resume the conversation from any telephone simply by entering the correct number. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsCpsConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

Example 1 uses the **Remove-CsCpsConfiguration** cmdlet to delete the Call Park service configuration with the Identity site:Redmond1. Because identities are unique, this command will result in only one configuration being deleted.
  
```
Remove-CsCpsConfiguration -Identity site:Redmond1
```

### EXAMPLE 2

In Example 2, all the Call Park service configurations that have been defined at the site scope are deleted. To carry out this task, the command first uses the **Get-CsCpsConfiguration** cmdlet and the Filter parameter to return all the Call Park service configurations that have been defined at the site scope; the wildcard site:* ensures that only settings that have an Identity that begins with the string value site: will be returned. This filtered collection is then piped to the **Remove-CsCpsConfiguration** cmdlet, which proceeds to delete each item in the collection. Note that any time you remove Call Park service settings from a site, the site will automatically begin to use the Call Park service settings configured at the global scope.
  
```
Get-CsCpsConfiguration -Filter site:* | Remove-CsCpsConfiguration
```

## Detailed Description

This cmdlet is used to remove a Call Park service configuration. A Call Park service configuration specifies what happens to a call after it has been parked. For example, if a parked call isn't answered after a period of time it can be automatically forwarded to someone else, such as an administrator, or to a Response Group. Calls can be configured to ring after a certain period of time to ensure the call isn't forgotten. In addition, Call Park service can be configured to play music on hold to the caller while the call is parked.
  
This cmdlet can be used to remove any Call Park configurations, including the Global configuration. In the case of the Global configuration, however, the configuration will not actually be removed; instead, it will simply be reset to the default values.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the Call Park service configuration you want to remove. This identifier will be either Global or site:\<sitename\>, where \<sitename\> is the name of the site to which the configuration applies.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings object. Accepts pipelined input of Call Park service configuration objects.
  
## Return Types

Removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings.
  
## See also

#### 

[New-CsCpsConfiguration](new-cscpsconfiguration.md)
  
[Set-CsCpsConfiguration](set-cscpsconfiguration.md)
  
[Get-CsCpsConfiguration](get-cscpsconfiguration.md)
  
[Set-CsCallParkServiceMusicOnHoldFile](set-cscallparkservicemusiconholdfile.md)

