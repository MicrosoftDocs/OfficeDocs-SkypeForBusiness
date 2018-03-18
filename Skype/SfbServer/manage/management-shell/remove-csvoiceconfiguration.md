---
title: "Remove-CsVoiceConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 9b173dde-fa8e-4966-aa58-deff34625560
description: "Resets the voice configuration to its default values. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsVoiceConfiguration
 
Resets the voice configuration to its default values. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsVoiceConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

This example resets the Global (and only) voice configuration to the default values. This action deletes all defined voice test configurations, so we added the Confirm parameter in order to receive a prompt asking whether we really want to perform this action before the removal takes place.
  
```
Remove-CsVoiceConfiguration -Identity Global -Confirm
```

## Detailed Description

Voice test configurations are used to test a phone number against a specific voice policy, route, and dial plan. This cmdlet removes the global (and only) voice configuration, which is a container for all voice test configurations defined for a Skype for Business Server 2015 deployment. "Removing" the voice configuration doesn't actually remove it; the global instance is still there. However, it does set the list of voice test configurations to the default, which is empty. 
  
WARNING: Removing the voice configuration (which sets the list of voice test configurations to empty) deletes all defined voice test configurations for a Skype for Business Server 2015 deployment. After calling this cmdlet, a call to the **Get-CsVoiceTestConfiguration** cmdlet will return no results.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The scope of the voice configuration to remove. This value must be Global.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceConfiguration object. Accepts pipelined input of a voice configuration object.
  
## Return Types

This cmdlet removes (resets) an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceConfiguration.
  
## See also

#### 

[Set-CsVoiceConfiguration](set-csvoiceconfiguration.md)
  
[Get-CsVoiceConfiguration](get-csvoiceconfiguration.md)
  
[Remove-CsVoiceTestConfiguration](remove-csvoicetestconfiguration.md)
  
[Get-CsVoiceTestConfiguration](get-csvoicetestconfiguration.md)

