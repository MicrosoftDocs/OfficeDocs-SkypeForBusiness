---
title: "Get-CsVoiceTestConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c23235db-500c-4303-8c75-b4ae341b3807
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsVoiceTestConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Retrieves a test scenario you can use to test phone numbers against specified routes and rules. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsVoiceTestConfiguration [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Retrieves all the voice test configuration settings.
  
```
Get-CsVoiceTestConfiguration
```

### EXAMPLE 2

This example retrieves all the voice test configuration settings, displaying only the Identity, DialedNumber, and ExpectedTranslatedNumber parameter of each. The settings returned by the **Get-CsVoiceTestConfiguration** cmdlet are piped to the **Select-Object** cmdlet, where the output is narrowed down to the Identity, DialedNumber, and ExpectedTranslatedNumber properties. 
  
```
Get-CsVoiceTestConfiguration | Select-Object Identity, DialedNumber, ExpectedTranslatedNumber
```

### EXAMPLE 3

This example uses the Filter parameter to retrieve all the voice test configuration settings with Identities that contain the string "test". The wildcard characters (\*) at the beginning and end of the filter value indicate that the string "test" can be located anywhere within the Identity, with any characters before or after that string. For example, this command would return voice test configurations with names such as TestConfig, VoiceNumberTest, and VoiceTest1.
  
```
Get-CsVoiceTestConfiguration -Filter *test*
```

## Detailed Description
<a name="sectionSection1"> </a>

This cmdlet retrieves the voice route, usage, dial plan, and voice policy against which to test a specified phone number. Before implementing voice routes and voice policies, it's a good idea to test them out on various phone numbers to ensure the results are what you're expecting. You can do this testing by retrieving a test configuration with this cmdlet, and then running that scenario with the **Test-CsVoiceConfiguration** cmdlet. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsVoiceTestConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsVoiceTestConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |This parameter provides a way to do a wildcard search of the defined voice test configurations. (For details, see the examples in this topic.)  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |A string uniquely identifying the test configuration you want to retrieve.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the voice test configuration from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

Returns one of more objects of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsVoiceTestConfiguration](new-csvoicetestconfiguration.md)
  
[Remove-CsVoiceTestConfiguration](remove-csvoicetestconfiguration.md)
  
[Set-CsVoiceTestConfiguration](set-csvoicetestconfiguration.md)
  
[Test-CsVoiceTestConfiguration](test-csvoicetestconfiguration.md)

