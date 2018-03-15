---
title: "Remove-CsVoiceTestConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: abe27005-8325-47d7-8c7c-12bb831b87c7
description: "Removes a voice test configuration that was used to test phone numbers against specified routes and rules. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsVoiceTestConfiguration
 
Removes a voice test configuration that was used to test phone numbers against specified routes and rules. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsVoiceTestConfiguration -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

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

Before implementing voice routes and voice policies, it's a good idea to test them out on various phone numbers to ensure the results are what you're expecting. When you're done with those tests and won't need them again, use this cmdlet to remove them.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |A string uniquely identifying the test configuration you want to remove.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration object. Accepts pipelined input of voice test configuration objects.
  
## Return Types

Removes an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration.
  
## See also

#### 

[New-CsVoiceTestConfiguration](new-csvoicetestconfiguration.md)
  
[Set-CsVoiceTestConfiguration](set-csvoicetestconfiguration.md)
  
[Get-CsVoiceTestConfiguration](get-csvoicetestconfiguration.md)
  
[Test-CsVoiceTestConfiguration](test-csvoicetestconfiguration.md)

