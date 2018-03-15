---
title: "Remove-CsVoiceNormalizationRule"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6a1bf26c-d95b-4a03-8d2d-c17159dcb9be
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsVoiceNormalizationRule
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes a voice normalization rule. Voice normalization rules are used to convert telephone dialing requirements (for example, dialing 9 to access an outside line) to the E.164 phone number format used by Lync Server. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsVoiceNormalizationRule -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example removes the voice normalization rule with the Identity site:Redmond/SeattleRule1.
  
```
Remove-CsVoiceNormalizationRule -Identity site:Redmond/SeattleRule1
```

### EXAMPLE 2

This example removes all voice normalization rules from site Redmond.
  
```
Remove-CsVoiceNormalizationRule -Identity site:Redmond
```

## Detailed Description
<a name="sectionSection1"> </a>

This cmdlet removes a named voice normalization rule. These rules are a required part of phone authorization and call routing. They define the requirements for converting (or translating) numbers from an internal Lync Server format to a standard (E.164) format. An understanding of regular expressions is helpful in order to define number patterns that will be translated.
  
Rules that are removed by using this cmdlet will be deleted from the dial plans of the organization, so they won't be returned by the **Get-CsVoiceNormalizationRule** cmdlet and will not appear in the NormalizationRules property returned by a call to the **Get-CsDialPlan** cmdlet. This means that calling the **Remove-CsVoiceNormalizationRule** cmdlet could leave a dial plan with no normalization rules. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsVoiceNormalizationRule** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsVoiceNormalizationRule"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identity of the rule to be removed. If the Identity specified includes the scope followed by a slash and then the name (for example: site:Redmond/Rule1, where site:Redmond is the scope and Rule1 is the name), the one rule with that unique Identity will be removed. If the value passed to the Identity contains only the scope (site:Redmond), all normalization rules at that scope will be removed.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule object. Accepts pipelined input of voice normalization rule objects.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet deletes an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsVoiceNormalizationRule](new-csvoicenormalizationrule.md)
  
[Set-CsVoiceNormalizationRule](set-csvoicenormalizationrule.md)
  
[Get-CsVoiceNormalizationRule](get-csvoicenormalizationrule.md)
  
[Test-CsVoiceNormalizationRule](test-csvoicenormalizationrule.md)
  
[Remove-CsDialPlan](remove-csdialplan.md)
  
[Get-CsDialPlan](get-csdialplan.md)

