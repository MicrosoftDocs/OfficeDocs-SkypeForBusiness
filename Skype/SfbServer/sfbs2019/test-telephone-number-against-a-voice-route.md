---
title: "Test telephone number against a voice route in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9a77ed6d-9394-4bef-9344-3d91b6959b97
description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Test telephone number against a voice route in Lync Server 2013
[]
 **In this article**
  
[Description](#sectionSection0)
  
[Running the test](#sectionSection1)
  
[Determining success or failure](#sectionSection2)
  
[Reasons why the test might have failed](#sectionSection3)
  
****

|||
|:-----|:-----|
|Verification schedule  <br/> |Monthly  <br/> |
|Testing tool  <br/> |Windows PowerShell  <br/> |
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsVoiceRoute cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/>  `Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsVoiceRoute"}` <br/> |
   
## Description
<a name="sectionSection0"> </a>

Voice routes work together with voice policies to help route Enterprise Voice calls to the PSTN network. Each voice route includes a regular expression (a number pattern) that identifies the phone numbers that will be routed through a given voice route: the route will be able to handle any phone numbers that match this regular expression. For example, a voice route might have a regular expression that enables it to handle any 10-digit number. That means the route would be able to handle a phone number such as this: 
  
- 2065551219
    
The route would not be able to handle either of the following two numbers, neither of which has 10 digits:
  
- 5551219
    
- 12065551219
    
The Test-CsVoiceRoute cmdlet verifies whether a given voice route can route a specified phone number.
  
## Running the test
<a name="sectionSection1"> </a>

Verifying the ability of a voice route to route a specified phone number is a two-step process. First you have to use the Get-CsVoiceRoute cmdlet to return an instance of that voice route, and then you have to use the Test-CsVoiceRoute cmdlet to verify the ability of that route to handle the target phone number. For example, this command verifies whether the RedmondVoiceRoute voice route can route the phone number 2065551219:
  
 `Get-CsVoiceRoute -Identity "RedmondVoiceRoute" | Test-CsVoiceRoute -TargetNumber "2065551219"`
  
Note that the phone number should be typed as you expect users to dial that number. For example, if you do not expect users to include the country code and area code when dialing, then use syntax similar to this:
  
 `-TargetNumber "5551219"`
  
In this case, the target number leaves out both the country code and the area code.
  
To use a single command to test all the voice routes against a specified target number, use syntax such as the following:
  
 `Get-CsVoiceRoute | Test-CsVoiceRoute -TargetNumber "2065551219"`
  
For more information, see the Help documentation for the Test-CsVoiceRoute cmdlet.
  
## Determining success or failure
<a name="sectionSection2"> </a>

If the voice route can route the target phone number the Test-CsVoiceRoute cmdlet just returns the value True:
  
MatchesPattern
  
--------------
  
True
  
That means that route can handle numbers similar to the target number. If the voice route is can't handle the target number then Test-CsVoiceRoute returns the value False:
  
MatchesPattern
  
--------------
  
False
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

When testing voice routes, "failure" is a relative term. In this case, it doesn't mean that the route is somehow "broken;" instead, it just means that the route can't handle the target number. That could be because the voice route was configured incorrectly. It could also mean that the route was never intended to handle numbers using this pattern. For example, if you do not want to route calls to other countries over a given route that route might be configured to reject all phone numbers that include a country code. If Test-CsVoiceRoute returns False when you expected it to return True, verify that you typed the target number in correctly. If you did, then use a command similar to this one to view the NumberPattern configured for the route:
  
 `Get-CsVoiceRoute -Identity "RedmondVoiceRoute" | Select-Object NumberPattern`
  
## See also
<a name="sectionSection3"> </a>

#### 

[Test-CsVoiceRoute](test-csvoiceroute.md)

