---
title: "Remove-CsVoiceConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9b173dde-fa8e-4966-aa58-deff34625560
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsVoiceConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Resets the voice configuration to its default values. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsVoiceConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example resets the Global (and only) voice configuration to the default values. This action deletes all defined voice test configurations, so we added the Confirm parameter in order to receive a prompt asking whether we really want to perform this action before the removal takes place.
  
```
Remove-CsVoiceConfiguration -Identity Global -Confirm
```

## Detailed Description
<a name="sectionSection1"> </a>

Voice test configurations are used to test a phone number against a specific voice policy, route, and dial plan. This cmdlet removes the global (and only) voice configuration, which is a container for all voice test configurations defined for a Lync Server deployment. "Removing" the voice configuration doesn't actually remove it; the global instance is still there. However, it does set the list of voice test configurations to the default, which is empty. 
  
WARNING: Removing the voice configuration (which sets the list of voice test configurations to empty) deletes all defined voice test configurations for a Lync Server deployment. After calling this cmdlet, a call to the **Get-CsVoiceTestConfiguration** cmdlet will return no results. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsVoiceConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsVoiceConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The scope of the voice configuration to remove. This value must be Global.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceConfiguration object. Accepts pipelined input of a voice configuration object.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet removes (resets) an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceConfiguration.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Set-CsVoiceConfiguration](set-csvoiceconfiguration.md)
  
[Get-CsVoiceConfiguration](get-csvoiceconfiguration.md)
  
[Remove-CsVoiceTestConfiguration](remove-csvoicetestconfiguration.md)
  
[Get-CsVoiceTestConfiguration](get-csvoicetestconfiguration.md)

