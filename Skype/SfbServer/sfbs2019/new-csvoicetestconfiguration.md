---
title: "New-CsVoiceTestConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: da312c27-bc89-46c3-a6c9-c098ed4e7df7
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsVoiceTestConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Creates a test scenario you can use to test phone numbers against specified routes and rules. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsVoiceTestConfiguration -Name <String> <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example creates a new voice test configuration with default values that has the Identity TestConfig1.
  
```
New-CsVoiceTestConfiguration -Identity TestConfig1
```

### EXAMPLE 2

This example creates a new voice test configuration named TestConfig1 and sets the TargetDialplan parameter to site:Redmond1. This will result in the tests for expected number, usage, and route to be run against the settings for the dial plan for the site Redmond1.
  
In this example we declared TestConfig1 without specifying the Identity parameter. Identity is a positional parameter, so the first value in the command following the cmdlet name is recognized by the cmdlet as the Identity.
  
```
New-CsVoiceTestConfiguration TestConfig1 -TargetDialplan site:Redmond1
```

### EXAMPLE 3

This example creates a new voice test configuration named TestConfig1. This configuration will use the default values to test the DialedNumber 5551212 against an expected output (ExpectedTranslatedNumber) of +5551212. This expectation is based on the normalization rules associated with the dial plan that will be used when a test is run against this object. That test must be run using the **Test-CsVoiceTestConfiguration** cmdlet. 
  
```
New-CsVoiceTestConfiguration -Identity TestConfig1 -DialedNumber 5551212 -ExpectedTranslatedNumber +5551212
```

## Detailed Description
<a name="sectionSection1"> </a>

Before implementing voice routes and voice policies, it's a good idea to test them out on various phone numbers to ensure the results are what you're expecting. You can do this testing by creating test scenarios with this cmdlet.
  
The **New-CsVoiceTestConfiguration** cmdlet defines the voice route, usage, dial plan, and voice policy against which to test a specified phone number. All of this information can be defined and retrieved using other cmdlets; see the parameter descriptions for this topic for more information. 
  
The configurations created with this cmdlet are tested using the **Test-CsVoiceTestConfiguration** cmdlet. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsVoiceTestConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsVoiceTestConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |A string uniquely identifying this test scenario.  <br/> This string can be up to 32 characters in length and may contain any alphanumeric characters plus the backslash (\), period (.) or underscore (_).  <br/> The value of this parameter does not include scope because this object can be created only at the global scope. Therefore only a unique name is required.  <br/> |
| _Name_ <br/> |Required  <br/> |System.String  <br/> |This parameter contains the same value as the Identity. If the Identity parameter is specified, you cannot include the Name parameter in your command. Likewise, if the Name parameter is specified, you cannot specify an Identity.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DialedNumber_ <br/> |Optional  <br/> |System.String  <br/> |The phone number you want to use to test the policies, usages, etc.  <br/> Must be 512 characters or fewer.  <br/> Default: 1234  <br/> |
| _ExpectedRoute_ <br/> |Optional  <br/> |System.String  <br/> |The name of the voice route expected to be used during the configuration test. If a different route is used, based on the target dial plan and voice policy, the test will fail. You can retrieve available voice routes by calling the **Get-CsVoiceRoute** cmdlet.  <br/> Must be 256 characters or fewer.  <br/> |
| _ExpectedTranslatedNumber_ <br/> |Optional  <br/> |System.String  <br/> |The phone number in the format you expect to see it after translation. This is the value of the DialedNumber parameter after normalization. If you run the **Test-CsVoiceTestConfiguration** cmdlet and the DialedNumber does not result in the value in ExpectedTranslatedNumber, the test will report as Fail.  <br/> Must be 512 characters or fewer.  <br/> Default: +1234  <br/> |
| _ExpectedUsage_ <br/> |Optional  <br/> |System.String  <br/> |The name of the PSTN usage expected to be used during the configuration test. If a different PSTN usage is used, based on the target dial plan and voice policy, the test will fail. You can retrieve available usages by calling the **Get-CsPstnUsage** cmdlet.  <br/> Must be 256 characters or fewer.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _TargetDialplan_ <br/> |Optional  <br/> |System.String  <br/> |The Identity of the dial plan to be used for this test. Dial plans can be retrieved by called the **Get-CsDialPlan** cmdlet.  <br/> Must be 40 characters or fewer.  <br/> Default: Global  <br/> |
| _TargetVoicePolicy_ <br/> |Optional  <br/> |System.String  <br/> |The Identity of the voice policy against which to run this test. Voice policies can be retrieved by calling the **Get-CsVoicePolicy** cmdlet.  <br/> Must be 40 characters or fewer.  <br/> Default: Global  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet creates an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration
  
## See also
<a name="sectionSection3"> </a>

#### 

[Remove-CsVoiceTestConfiguration](remove-csvoicetestconfiguration.md)
  
[Set-CsVoiceTestConfiguration](set-csvoicetestconfiguration.md)
  
[Get-CsVoiceTestConfiguration](get-csvoicetestconfiguration.md)
  
[Test-CsVoiceTestConfiguration](test-csvoicetestconfiguration.md)
  
[Get-CsVoiceRoute](get-csvoiceroute.md)
  
[Get-CsPstnUsage](get-cspstnusage.md)
  
[Get-CsDialPlan](get-csdialplan.md)
  
[Get-CsVoicePolicy](get-csvoicepolicy.md)

