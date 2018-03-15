---
title: "Remove-CsMediaConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8af2b8cb-4d58-4f8a-9acb-9b5104880bc9
description: "Removes the specified collection of media configuration settings. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsMediaConfiguration
 
Removes the specified collection of media configuration settings. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsMediaConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

In Example 1, the **Remove-CsMediaConfiguration** cmdlet is used to delete the media configuration collection with the Identity site:Redmond1. When media settings are removed from the site scope, that site will automatically begin to use the global media settings.
  
```
Remove-CsMediaConfiguration -Identity site:Redmond1
```

### EXAMPLE 2

In Example 2, three cmdlets—the **Get-CsMediaConfiguration** cmdlet, the **Where-Object** cmdlet, and the **Remove-CsMediaConfiguration** cmdlet—are used to remove all the media configuration collections where encryption is required of all parties involved in the conversation. To do this, the **Get-CsMediaConfiguration** cmdlet is first used to return all the media configuration collections in the organization. That information is then piped to the **Where-Object** cmdlet, which applies a filter that restricts the pipeline data to those collections where the EncryptionLevel property is equal to (-eq) RequireEncryption. Finally, that filtered set of data is passed to the **Remove-CsMediaConfiguration** cmdlet, which deletes each item in the set.
  
```
Get-CsMediaConfiguration | Where-Object {$_.EncryptionLevel -eq "RequireEncryption"} | Remove-CsMediaConfiguration
```

### EXAMPLE 3

In this example all media configurations defined at the service scope (meaning the configuration applies to a specific service) are removed. This is accomplished by first calling the **Get-CsMediaConfiguration** cmdlet using the Filter service:*. This filter retrieves all media configuration collections with an Identity starting with service, which means all collections at the service scope. That set of collections is then piped the **Remove-CsMediaConfiguration** cmdlet, which removes them all.
  
```
Get-CsMediaConfiguration -Filter service:* | Remove-CsMediaConfiguration
```

## Detailed Description

This cmdlet removes a collection of media settings. These settings relate to audio and video calls between client endpoints.
  
This cmdlet can also be used to remove the global media settings. In that case, however, the settings will not actually be removed; instead, they will simply be reset to their default values.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the media configuration settings you want to remove. This identifier specifies the scope at which this configuration is applied (global, site, or service).  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.Media.MediaSettings object. Accepts pipelined input of media configuration objects.
  
## Return Types

Removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.Media.MediaSettings.
  
## See also

#### 

[New-CsMediaConfiguration](new-csmediaconfiguration.md)
  
[Set-CsMediaConfiguration](set-csmediaconfiguration.md)
  
[Get-CsMediaConfiguration](get-csmediaconfiguration.md)

