---
title: "Remove-CsVoiceTestConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: abe27005-8325-47d7-8c7c-12bb831b87c7
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsVoiceTestConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes a voice test configuration that was used to test phone numbers against specified routes and rules. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsVoiceTestConfiguration -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example removes the voice test configuration settings with the Identity TestConfig1.
  
```
Remove-CsVoiceTestConfiguration -Identity TestConfig1
```

### EXAMPLE 2

This example removes all voice test configuration settings for any configuration with an Identity containing the string test. The command first calls the **Get-CsVoiceTestConfiguration** cmdlet with the Filter parameter to retrieve all voice test configurations that have an Identity with the string "test" anywhere in its value. The resulting set of configurations is then piped to the **Remove-CsVoiceTestConfiguration** cmdlet and removed. 
  
```
Get-CsVoiceTestConfiguration -Filter *test* | Remove-CsVoiceTestConfiguration
```

## Detailed Description
<a name="sectionSection1"> </a>

Before implementing voice routes and voice policies, it's a good idea to test them out on various phone numbers to ensure the results are what you're expecting. When you're done with those tests and won't need them again, use this cmdlet to remove them.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsVoiceTestConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsVoiceTestConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |A string uniquely identifying the test configuration you want to remove.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration object. Accepts pipelined input of voice test configuration objects.
  
## Return Types
<a name="sectionSection3"> </a>

Removes an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsVoiceTestConfiguration](new-csvoicetestconfiguration.md)
  
[Set-CsVoiceTestConfiguration](set-csvoicetestconfiguration.md)
  
[Get-CsVoiceTestConfiguration](get-csvoicetestconfiguration.md)
  
[Test-CsVoiceTestConfiguration](test-csvoicetestconfiguration.md)

