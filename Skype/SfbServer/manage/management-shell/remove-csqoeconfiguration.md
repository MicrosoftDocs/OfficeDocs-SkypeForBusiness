---
title: "Remove-CsQoEConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3b50e857-c524-4aad-b191-d324fc7c837c
description: "Removes a collection of QoE (Quality of Experience) settings. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsQoEConfiguration
[]
Removes a collection of QoE (Quality of Experience) settings. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsQoEConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

Example 1 uses the **Remove-CsQoEConfiguration** cmdlet to remove the QoE settings assigned to the site Redmond. Using the Identity parameter ensures that only the settings assigned to the specified site will be removed.
  
```
Remove-CsQoEConfiguration -Identity site:Redmond
```

### EXAMPLE 2

The command shown in Example 2 removes all the QoE settings that have been assigned at the site scope. To do this, the command first uses the **Get-CsQoEConfiguration** cmdlet and the Filter parameter to retrieve the appropriate QoE settings; the wildcard string "site:*" ensures that only those settings that have an identity beginning with the string value site: are returned. The filtered collection is then passed to the **Remove-CsQoEConfiguration** cmdlet, which deletes all the items in the collection.
  
```
Get-CsQoEConfiguration -Filter site:* | Remove-CsQoEConfiguration
```

### EXAMPLE 3

In Example 3, any QoE settings where the KeepQoEDataForDays property is less than 30 are deleted. To carry out this task, the command calls the **Get-CsQoEConfiguration** cmdlet without any parameters in order to return a collection of all the QoE settings currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the KeepQoEDataForDays property is less than (-lt) 30 days. In turn, the filtered collection is piped to the **Remove-CsQoEConfiguration** cmdlet, which deletes each item in that collection.
  
```
Get-CsQoEConfiguration | Where-Object {$_.KeepQoEDataForDays -lt 30} | Remove-CsQoEConfiguration
```

## Detailed Description

QoE metrics track the quality of audio and video calls made in your organization, including such things as the number of network packets lost, background noise, and the amount of "jitter" (differences in packet delay). These metrics are stored in a database apart from other data (such as call detail records), which allows you to enable and disable QoE independent of other data recording. Use this cmdlet to remove settings that configure QoE at the site level. Calling this cmdlet on the global QoE configuration will reset all properties to the defaults.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the settings you want to remove. Possible values are global and site:\<site name\>, where \<site name\> is the name of the site in your Skype for Business Server 2015 deployment with the settings to be removed.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.QoE.QoESettings object. Accepts pipelined input of QoE configuration objects.
  
## Return Types

This cmdlet does not return a value or object. Instead, it removes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.QoE.QoESettings object.
  
## See also

#### 

[New-CsQoEConfiguration](new-csqoeconfiguration.md)
  
[Set-CsQoEConfiguration](set-csqoeconfiguration.md)
  
[Get-CsQoEConfiguration](get-csqoeconfiguration.md)

