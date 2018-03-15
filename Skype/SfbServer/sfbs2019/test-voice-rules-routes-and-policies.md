---
title: "Test voice rules, routes, and policies in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ebb9c3fa-6950-4311-87ca-e1ecd9280a43
description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Test voice rules, routes, and policies in Lync Server 2013
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
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsVoiceUser cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/>  `Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsVoiceUser"}` <br/> |
   
## Description
<a name="sectionSection0"> </a>

When a user makes a phone call, the route the call takes to reach its destination depends on both the policies and dial plans assigned to that user. Given a user's SIP address and a phone number, the Test-CsVoiceUser cmdlet verifies whether the user in question can complete a call to that number. If the test succeeds, Test-CsVoiceUser returns the following: 
  
- The number translated to E.164 format (based on the user's dial plan) 
    
- The normalization rule that supplied that translation
    
- The voice route used (based on route priority); 
    
- The phone usage that linked the user's voice policy to the voice route.
    
Test-CsVoiceUser enables you to determine whether a specific phone number will route and translate as expected, and can help troubleshoot call-related problems that are experienced by individual users.
  
## Running the test
<a name="sectionSection1"> </a>

When running the Test-CsVoiceUser cmdlet you must supply two pieces of information: the number being dialed (DialedNumber) and the Identity of the user account being tested. For example, this command tests the ability of the user who has the SIP address sip:kenmyer@litwareinc.com to make a call to the phone number +1206555-1219:
  
 `Test-CsVoiceUser -DialedNumber "12065551219" -SipUri "sip:kenmyer@litwareinc.com"`
  
The phone number should be formatted in the way that you expect it to be dialed. For example, if users typically do not dial the 1 before placing a long distance call then you should use this format:
  
 `-DialedNumber "2065551219"`
  
Of course, in that case, the test will fail if you do not have a normalization rule that can correctly translate the number 2065551219 into the E.164 telephone format that is used by Lync Server. For more information, see the help topic New-CsVoiceNormalizationRule cmdlet.
  
If you want to run this same test against each of your user accounts, you can use a command similar to the following:
  
 `Get-CsUser | ForEach-Object {$_.DisplayName; Test-CsVoiceUser -DialedNumber "+12065551219" -SipUri $_.SipAddress} | Format-List`
  
For more information, see the Help documentation for the Test-CsVoiceUser cmdlet.
  
## Determining success or failure
<a name="sectionSection2"> </a>

If the test is completed successfully (that is, if the user can make a phone call to the specified number), the output will show information like the translated phone number and the matching normalization rule and voice route:
  
TranslatedNumber MatchingRule FirstMatchingRoute MatchingUsage
  
---------------- ------------ ------------------ -------------
  
+12065551219 Descripti... LocalRoute Local
  
Because of the limitations of the Windows PowerShell screen, at least some returned information (most notably the full description of the matching normalization rule) might not appear on-screen. If you are only interested in the success or failure of the test, then this might not matter. If you would prefer to see the full details of the returned data then pipe the output to the Format-List cmdlet when running the test:
  
 `Test-CsVoiceUser -DialedNumber "+12065551219" -SipUri "sip:kenmyer@litwareinc.com" -Verbose | Format-List`
  
That will display the output in a more reader-friendly format: 
  
TranslatedNumber : +12065551219
  
MatchingRule : Description=;Pattern=^(\d{11})$;Translation=+$1;
  
 Name=Prefix All;IsInternalExtension=False 
  
FirsMatchingRoute : LocalRoute
  
MatchingUsage : Local
  
If the test fails, Test-CsVoiceUser will return an empty set of property values: 
  
TranslatedNumber MatchingRule FirstMatchingRoute MatchingUsage
  
---------------- ------------ ------------------ -------------
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

There are any number of reasons why the Test-CsVoiceUser cmdlet might fail: there might not be a normalization rule that can translate the provided phone number. There could be problems with the voice route. There could be a configuration issue with the dial plan assigned to the user in question. Because of that, you might want to include the Verbose parameter when you are running the Test-CsVoiceUser cmdlet:
  
 `Test-CsVoiceUser -DialedNumber "+12065551219" -SipUri "sip:kenmyer@litwareinc.com" -Verbose`
  
When the Verbose cmdlet is included, Test-CsVoiceUser will issue a detailed account of all the steps in takes when conducting its checks. For example, you might see steps similar to these: 
  
VERBOSE: Locating user with identity "sip:kenmyer@litwareinc.com"
  
VERBOSE: Loading dial plan: "RedmondDialPlan"
  
This additional information can provide hints as to the steps that you can take to pinpoint the cause of the failure. For example, the verbose output shown here tells us that the user being tested was assigned the dial plan RedmondDialPlan. If the test has failed, one logical next step would be to verify that RedmondDialPlan can translate the supplied phone number.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Test-CsVoiceUser](test-csvoiceuser.md)

