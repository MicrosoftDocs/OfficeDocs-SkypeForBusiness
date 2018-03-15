---
title: "Remove-CsQoEConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3b50e857-c524-4aad-b191-d324fc7c837c
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsQoEConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes a collection of QoE (Quality of Experience) settings. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsQoEConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

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
<a name="sectionSection1"> </a>

QoE metrics track the quality of audio and video calls made in your organization, including such things as the number of network packets lost, background noise, and the amount of "jitter" (differences in packet delay). These metrics are stored in a database apart from other data (such as call detail records), which allows you to enable and disable QoE independent of other data recording. Use this cmdlet to remove settings that configure QoE at the site level. Calling this cmdlet on the global QoE configuration will reset all properties to the defaults.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsQoEConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsQoEConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the settings you want to remove. Possible values are global and site:\<site name\>, where \<site name\> is the name of the site in your Lync Server deployment with the settings to be removed.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.QoE.QoESettings object. Accepts pipelined input of QoE configuration objects.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet does not return a value or object. Instead, it removes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.QoE.QoESettings object.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsQoEConfiguration](new-csqoeconfiguration.md)
  
[Set-CsQoEConfiguration](set-csqoeconfiguration.md)
  
[Get-CsQoEConfiguration](get-csqoeconfiguration.md)

