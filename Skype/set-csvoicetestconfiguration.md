---
title: Set-CsVoiceTestConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: 7b95fc95-ec0e-4bb3-aed1-e8b72e305999
---


# Set-CsVoiceTestConfiguration
[]
Modifies a test scenario you can use to test phone numbers against specified routes and rules. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Set-CsVoiceTestConfiguration [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

This example sets the dialed number of the voice test configuration for TestConfig1 to 14255551212. This is the number that will be checked against the voice policy and route to ensure normalization occurs as expected, as well as to ensure the correct routes and dial plans are being applied.
  
    
    

```

Set-CsVoiceTestConfiguration -Identity TestConfig1 -DialedNumber 14255551212
```


### EXAMPLE 2

This example modifies settings for the voice test configuration TestConfig1. The command sets the TargetDialPlan to the dial plan for site:Redmond1. Because a change in dial plan could mean a change in normalization rules, the ExpectedTranslationNumber has also been changed to reflect what is expected from the normalization rules for that dial plan.
  
    
    

```
Set-CsVoiceTestConfiguration -Identity TestConfig1 -TargetDialPlan site:Redmond1 -ExpectedTranslatedNumber "+912065551212"
```


## Detailed Description

Before implementing voice routes and voice policies, it's a good idea to test them out on various phone numbers to ensure the results are what you're expecting. You can do this by modifying test scenarios with this cmdlet.
  
    
    
The **Set-CsVoiceTestConfiguration** cmdlet modifies the voice route, usage, dial plan, and voice policy against which to test a specified phone number. All of this information can be defined and retrieved using other cmdlets, as specified in the parameter descriptions for this topic.
  
    
    
The configurations modified with this cmdlet are tested using the **Test-CsVoiceTestConfiguration** cmdlet.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DialedNumber_ <br/> |Optional  <br/> |String  <br/> |The phone number you want to use to test the policies, usages, and so on.  <br/> Must be 512 characters or fewer.  <br/> |
| _ExpectedRoute_ <br/> |Optional  <br/> |String  <br/> |The name of the voice route expected to be used during the configuration test. If a different route is used, based on the target dial plan and voice policy, the test will fail. You can retrieve available voice routes by calling the **Get-CsVoiceRoute** cmdlet. <br/> Must be 256 characters or fewer.  <br/> |
| _ExpectedTranslatedNumber_ <br/> |Optional  <br/> |String  <br/> |The phone number in the format you expect to see it in after translation. This is the value of the DialedNumber parameter after normalization. If you run the **Test-CsVoiceTestConfiguration** cmdlet and the DialedNumber does not result in the value in ExpectedTranslatedNumber, the test will report as Fail. <br/> Must be 512 characters or fewer.  <br/> |
| _ExpectedUsage_ <br/> |Optional  <br/> |String  <br/> |The name of the PSTN usage expected to be used during the configuration test. If a different PSTN usage is used, based on the target dial plan and voice policy, the test will fail. You can retrieve available usages by calling the **Get-CsPstnUsage** cmdlet. <br/> Must be 256 characters or fewer.  <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |XdsGlobalRelativeIdentity  <br/> |A string uniquely identifying the test scenario you want to modify.  <br/> The value of this parameter does not include scope because this object can be created only at the global scope. Therefore only a name is required.  <br/> |
| _Instance_ <br/> |Optional  <br/> |TestConfiguration  <br/> |An object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration that contains an existing voice test configuration with the changes you'd like to make to that configuration. An object of this type can be retrieved by calling the **Get-CsVoiceTestConfiguraton** cmdlet. <br/> |
| _TargetDialplan_ <br/> |Optional  <br/> |String  <br/> |The Identity of the dial plan to be used for this test. Dial plans can be retrieved by calling the **Get-CsDialPlan** cmdlet. <br/> Must be 40 characters or fewer.  <br/> |
| _TargetVoicePolicy_ <br/> |Optional  <br/> |String  <br/> |The Identity of the voice policy against which to run this test. Voice policies can be retrieved by calling the **Get-CsVoicePolicy** cmdlet. <br/> Must be 40 characters or fewer.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration object. Accepts pipelined input of voice test configuration objects.
  
    
    

## Return Types

This cmdlet returns an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration.
  
    
    

## See also


#### 


  
    
    
 [New-CsVoiceTestConfiguration](new-csvoicetestconfiguration.md)
  
    
    
 [Remove-CsVoiceTestConfiguration](remove-csvoicetestconfiguration.md)
  
    
    
 [Get-CsVoiceTestConfiguration](get-csvoicetestconfiguration.md)
  
    
    
 [Test-CsVoiceTestConfiguration](test-csvoicetestconfiguration.md)
  
    
    
 [Get-CsVoiceRoute](get-csvoiceroute.md)
  
    
    
 [Get-CsPstnUsage](get-cspstnusage.md)
  
    
    
 [Get-CsDialPlan](get-csdialplan.md)
  
    
    
 [Get-CsVoicePolicy](get-csvoicepolicy.md)
