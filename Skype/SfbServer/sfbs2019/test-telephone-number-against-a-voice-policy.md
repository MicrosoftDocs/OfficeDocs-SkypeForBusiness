---
title: "Test telephone number against a voice policy in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 30c51700-17c6-4c57-891a-8d5ec30b50ee
description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Test telephone number against a voice policy in Lync Server 2013
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
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsVoicePolicy cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/>  `Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsVoicePolicy"}` <br/> |
   
## Description
<a name="sectionSection0"> </a>

The ability of Enterprise Voice users to make outgoing phone calls over the Public Switched Telephone network (PSTN) hinges, in large part, on three things:
  
- The voice policy assigned to the user.
    
- The voice routes used to route calls from Lync Server to the PSTN network.
    
- The PSTN usage, a Lync Server property that connects a voice policy to a voice route.
    
The PSTN usage is especially important: it's the property that connects a voice policy to a voice route. (A voice policy and a voice route are said to be connected if they have at least one PSTN usage in common.) Voice policies can be configured without specifying a PSTN usage. In that case, users who were assigned that policy won't be able to make outgoing calls over the PSTN network. Likewise, voice routes that do not have at least one specified PSTN usage will be unable to route calls to the PSTN network.
  
The Test-CsVoicePolicy cmdlet verifies that a given voice policy has a PSTN usage and that the usage is shared by at least one voice route. If the verification run by Test-CsVoicePolicy succeeds, the cmdlet will report back the name of the first valid voice route it finds, and also the name of the PSTN usage that connects the policy to the route.
  
## Running the test
<a name="sectionSection1"> </a>

To run the Test-CsVoicePolicy cmdlet you must first use the Get-CsVoicePolicy cmdlet retrieve an instance of the voice policy to be tested; that instance must then be piped to Test-CsVoicePolicy. For example:
  
 `Get-CsVoicePolicy -Identity "Global" | Test-CsVoicePolicy -TargetNumber "+12065551219"`
  
Note that this command, which does not use Get-CsVoicePolicy to retrieve a voice policy instance, will fail:
  
 `Test-CsVoicePolicy -TargetNumber "+12065551219" -VoicePolicy "Global"`
  
If you want to check all the voice policies against a specified phone number then use a command similar to this:
  
 `Get-CsVoicePolicy | Test-CsVoicePolicy -TargetNumber "+12065551219"`
  
Note that the TargetNumber must be specified by using the E.164 format. Test-CsVoicePolicy won't attempt to normalize or translate phone numbers into the E.164 format.
  
For more information, see the Help documentation for the Test-CsVoicePolicy cmdlet.
  
## Determining success or failure
<a name="sectionSection2"> </a>

If the voice policy can find both a matching voice route and a matching PSTN usage, then both the route and the usage will be displayed on-screen: 
  
FirstMatchingRoute MatchingUsage
  
------------------ -------------
  
RedmondVoiceRoute RedmondPstnUsage
  
If either an appropriate voice route or an appropriate PSTN usage cannot be found then blank property values will be displayed on-screen: 
  
FirstMatchingRoute MatchingUsage
  
------------------ -------------
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

If Test-CsVoicePolicy does not return a match that could mean that the voice policy does not share a PSTN usage with a voice route. To verify that, use a cmdlet similar to the following to verify that PSTN usages assigned to the voice policy: 
  
 `Get-CsVoicePolicy -Identity "Global" | Select-Object PstnUsages | Format-List`
  
Next, run this command to determine the PSTN usages assign to each of your voice routes: 
  
 `Get-CsVoiceRoute | Select-Object Identity, PstnUsages`
  
If you see any matches (that is, if you see one or more voice routes that share at least one PSTN usage with your voice policy), you should then run the Test-CsVoiceRoute cmdlet to verify that the voice route can dial the supplied phone number. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Test-CsVoicePolicy](test-csvoicepolicy.md)

