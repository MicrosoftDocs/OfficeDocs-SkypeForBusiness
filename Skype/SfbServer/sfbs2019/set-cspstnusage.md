---
title: "Set-CsPstnUsage"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ecba9ed6-4845-4035-933e-0c540d530b72
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsPstnUsage
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Modifies a set of strings that identify the allowed public switched telephone network (PSTN) usages. This cmdlet can be used to add usages to the list of PSTN usages or remove usages from the list. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsPstnUsage [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This command adds the string "International" to the current list of available PSTN usages.
  
```
Set-CsPstnUsage -Identity global -Usage @{add="International"}
```

### EXAMPLE 2

This command removes the string "Local" from the list of available PSTN usages.
  
```
Set-CsPstnUsage -Identity global -Usage @{remove="Local"}
```

### EXAMPLE 3

The command in this example performs the exact same action as the command in Example 2: it removes the "Local" PSTN usage. This example shows the command without the Identity parameter specified. The only Identity available to the **Set-CsPstnUsage** cmdlet is the Global identity; omitting the Identity parameter defaults to Global. 
  
```
Set-CsPstnUsage -Usage @{remove="Local"}
```

### EXAMPLE 4

This command replaces everything in the usage list with the values International and Restricted. All previously existing usages are removed.
  
```
Set-CsPstnUsage -Usage @{replace="International","Restricted"}
```

## Detailed Description
<a name="sectionSection1"> </a>

PSTN usages are string values that are used for call authorization. A PSTN usage links a voice policy to a route. The **Set-CsPstnUsage** cmdlet is used to add or remove phone usages to or from the usage list. This list is global so it can be used by policies and routes throughout the Lync Server deployment. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsPstnUsage** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsPstnUsage"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The scope at which these settings are applied. The Identity for this cmdlet is always Global.  <br/> |
| _Instance_ <br/> |Optional  <br/> |PstnUsages  <br/> |A reference to a PSTN usage object. This object must be of type PstnUsages and can be retrieved by calling the **Get-CsPstnUsage** cmdlet.  <br/> |
| _Usage_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Contains a list of allowable usage strings. These entries can be any string value.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PstnUsages object. Accepts pipelined input of PSTN usage objects.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet does not return a value or object. Instead, it configures instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PstnUsages object.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsPstnUsage](get-cspstnusage.md)

