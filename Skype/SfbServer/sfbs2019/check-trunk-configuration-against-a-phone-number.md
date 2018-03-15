---
title: "Check trunk configuration against a phone number in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0800d7a3-fc35-482b-a9a4-203d890bfa45
description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Check trunk configuration against a phone number in Lync Server 2013
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
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsTrunkConfiguration cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/>  `Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsTrunkConfiguration"}` <br/> |
   
## Description
<a name="sectionSection0"> </a>

SIP trunks connect the Lync Server internal Enterprise Voice network to any of the following:
  
- The Public Switched Telephone network (PSTN).
    
- An IP-public branch exchange (PBX).
    
- A Session Border Controller (SBC).
    
The Test-CsTrunkConfiguration cmdlet verifies that a phone number (as dialed by a user) can be converted to the E.164 network and routed over a specified SIP trunk.
  
## Running the test
<a name="sectionSection1"> </a>

To run the Test-CsTrunkConfiguration cmdlet you must first use the Get-CsTrunkConfiguration cmdlet to retrieve an instance of your SIP trunk configuration settings; that instance is then piped to Test-CsTrunkConfiguration:
  
 `Get-CsTrunkConfiguration -Identity "Global" | Test-CsTrunkConfiguration -DialedNumber "12065551219"`
  
Running Test-CsTrunkConfiguration without first running Get-CsTrunkConfiguration won't work. For example, this command will fail without returning any data:
  
 `Test-CsTrunkConfiguration -DialedNumber "12065551219" -TrunkConfiguration "Global"`
  
If you have multiple collections of SIP trunk configuration settings, you can use a command similar to the following to at the same time test each collection against the same phone number:
  
 `Get-CsTrunkConfiguration | Test-CsTrunkConfiguration -DialedNumber "12065551219"`
  
For more information, see the Help documentation for the Test-CsTrunkConfiguration cmdlet.
  
## Determining success or failure
<a name="sectionSection2"> </a>

If Test-CsTrunkConfiguration can place a call to the dialed number then the translated phone number (in the E.164 format) and the rule used to translate that phone number will both be displayed on screen: 
  
TranslatedNumber MatchingRule
  
---------------- ------------
  
+12065551219 Global/Redmond
  
If the test fails, Test-CsTrunkConfiguration will return empty property values: 
  
TranslatedNumber MatchingRule
  
---------------- ------------
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

If Test-CsTrunkConfiguration does not return a match that typically means that the trunk configuration settings being test do not have an outgoing calling number translation rule capable to converting the dialed number to the E.164 format. To retrieve the translation rules assigned to a collection of trunk configuration settings, you can use syntax similar to this:
  
 `Get-CsTrunkConfiguration -Identity "global" | Select-Object -ExpandProperty OutboundTranslationRulesList`
  
That returns information similar to this for each translation rule:
  
Description : Phone numbers without a country code or area code.
  
Pattern : ^\+(\d\*)$
  
 `Translation : $1`
  
Name : NoAreaCode
  
At that point, you check the value of the Pattern property (which is a [regular expression](https://go.microsoft.com/fwlink/?LinkId=400464) string) to see whether any of the translation rules are configured to handle the dialed number. If not, you'll either have to change one of the existing rules (Set-CsOutboundTranslationRule) or use the New-CsOutboundTranslationRule cmdlet to add a new rule to the collection. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Test-CsTrunkConfiguration](test-cstrunkconfiguration.md)

