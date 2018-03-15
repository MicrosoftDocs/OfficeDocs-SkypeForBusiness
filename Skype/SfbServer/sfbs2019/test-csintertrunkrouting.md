---
title: "Test-CsInterTrunkRouting"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2248d29a-8a2a-42b1-ab6b-a6c1d74b0455
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Test-CsInterTrunkRouting
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Verifies the route and the PSTN usage used when routing a phone call made from a specified SIP trunk. This cmdlet was introduced in Lync Server 2013.
  
```
Test-CsInterTrunkRouting -TargetNumber <PhoneNumber> -TrunkConfiguration <TrunkConfiguration> [-Force <SwitchParameter>] [-RouteSettings <PstnRoutingSettings>]
```

## Examples
<a name="Examples"> </a>

### Example 1

The commands shown in Example 1 return the matching routes and matching phone usages that enable users to call the phone number 1-206-555-1219 using the trunk configuration settings for the Redmond site.
  
```
$trunk = Get-CsTrunkConfiguration -Identity "site:Redmond"
Test-CsInterTrunkRouting -TargetNumber "tel:+12065551219" -TrunkConfiguration $trunk
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Test-CsInterTrunkRouting verifies that calls can be routed from one SIP to another. To do this, the cmdlet is given a phone number and a trunk configuration; Test-CsInterTrunkRouting will then report back matching routes and matching PSTN usages for the specified number. Note that calls can be routed between trunks only if the trunks have a number pattern that matches the specified phone number and only if the trunks share at least one PSTN usage.
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsInterTrunkRouting"}
  
 **Lync Server Control Panel:** The functions carried out by the Test-CsInterTrunkRouting cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _TargetNumber_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Voice.PhoneNumber  <br/> |PSTN telephone number to be called when conducting the test. The target phone number should specified using the E.164 format, which means that the number will look something like this:  <br/> -TargetNumber "tel:+12065551219"  <br/> The phone number should include the "tel:" prefix followed by a plus sign (+), the country/region calling code (1), the area code (206) and the phone number (5551219). Do not use dashes, parentheses, or any other characters when specifying the phone number.  <br/> |
| _TrunkConfiguration_ <br/> |Required  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration  <br/> |Object reference to the trunk configuration being tested. To create this object reference, use a command similar to this:  <br/> $trunk = Get-CsTrunkConfiguration -Identity "site:Redmond"  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _RouteSettings_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PstnRoutingSettings  <br/> |Object reference that enables you to specify a collection of voice routing configuration settings when calling Test-CsInterTrunkRouting. To create this object reference, use a command similar to this:  <br/> $route = Get-CsRoutingConfiguration -Identity "global"  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. Test-CsInterTrunkRouting does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

Test-CsInterTrunkRouting returns instances of the Microsoft.Rtc.Management.Voice.InterTrunkRoutingTestResult object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsTrunk](get-cstrunk.md)
  
[Get-CsTrunkConfiguration](get-cstrunkconfiguration.md)

