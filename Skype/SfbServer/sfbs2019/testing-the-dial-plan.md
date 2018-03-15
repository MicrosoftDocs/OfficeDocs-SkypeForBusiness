---
title: "Testing the dial plan in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 70eec03c-aca3-4106-86a7-77ae96b53779

description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Testing the dial plan in Lync Server 2013
[]
 **In this article**
  
[Description](#sectionSection0)
  
[Running the test](#sectionSection1)
  
[Determining success or failure](#sectionSection2)
  
[Reasons why the test might have failed](#sectionSection3)
  
****

|||
|:-----|:-----|
|Verification schedule  <br/> |Daily  <br/> |
|Testing tool  <br/> |Windows PowerShell  <br/> |
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsDialPlan cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsDialPlan"}```|
   
## Description
<a name="sectionSection0"> </a>

The Test-CsDialPlan cmdlet enables you to see the results of applying a dial plan to a given telephone number. Dial plans provide information, such as how normalization rules are applied, required to enable Enterprise Voice users to make telephone calls. Given a dialed number and a dial plan, this cmdlet will verify which normalization rule within the dial plan will be applied and what the translated number will be.
  
You can use this cmdlet for troubleshooting issues with number translations, or for verifying how to apply rules against certain numbers.
  
## Running the test
<a name="sectionSection1"> </a>

The Test-CsDialPlan cmdlet requires you to do two things. First, you must obtain an instance of the dial plan being tested; that can be done by using the Get-CsDialPlan cmdlet. Second, you must specify the phone number that has to be normalized. The format that is used for the phone number should match the number as dialed/entered by a user. For example, this command retrieves an instance of the dial plan, RedmondDialPlan, and checks whether the phone number 12065551219 can be normalized: 
  
```
Get-CsDialPlan -Identity "RedmondDialPlan" | Test-CsDialPlan -DialedNumber "12065551219" | Format-List
```

If you have a normalization rule that automatically adds the country code (in this example, 1) and the area code (206), then you might want to check the phone number 5551219, as follows: 
  
```
Get-CsDialPlan -Identity "RedmondDialPlan" | Test-CsDialPlan -DialedNumber "5551219" | Format-List
```

For more information, see the Help documentation for the [Test-CsDialPlan](test-csdialplan.md) cmdlet. 
  
## Determining success or failure
<a name="sectionSection2"> </a>

Test-CsDialPlan differs from many of the Lync Server test cmdlets because it only indirectly indicates whether a test succeeded or failed. When using Test-CsDialPlan you do not receive back output similar to this with the Result clearly labeled:
  
TargetFqdn : atl-cs-001.litwareinc.com
  
Result : Success
  
Latency : 00:00:06.8630376
  
Error :
  
Diagnosis :
  
Instead, if Test-CsDialPlan succeeds, then you'll receive information about the normalization rule that was able to successfully translate and use the specified phone number:
  
TranslatedNumber : +12065551219
  
MatchingRule : Description=;Pattern=^(\d(11))$;Translation=+$1;
  
 Name=Prefix All; IsInternalExtension=False 
  
If Test-CsDialPlan fails (that is, if the dial plan does not have a normalization rule that can translate the specified phone number), you'll just receive "empty" output as follows:
  
TranslatedNumber :
  
MatchingRule :
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

Here are some common reasons why Test-CsDialPlan might fail:
  
- You might have used an incorrect format when specifying the phone number. Dial plans include normalization rules that enable Lync Server to translate the phone numbers dialed or entered by a user. Therefore, your dial plan should have normalization rules that match the numbers users are likely to dial. For example, if users might dial the country code, area code, and then the phone number itself, that means that your dial plan should have a normalization rule to handle phone numbers such as this: 
    
    12065551219
    
    However, if you enter an incorrect phone number (for example, leaving off the final digit), then Test-CsDialPlan will fail. That's not because the dial plan is faulty but because you have entered a phone number than can't be interpreted.
    

