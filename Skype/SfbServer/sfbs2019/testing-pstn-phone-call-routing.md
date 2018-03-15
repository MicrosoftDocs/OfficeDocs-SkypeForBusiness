---
title: "Testing PSTN phone call routing in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 301dd44d-03e9-41cd-9722-54e00365aa45

description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Testing PSTN phone call routing in Lync Server 2013
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
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the **Test-CsInterTrunkRouting** cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsInterTrunkRouting"}```|
   
## Description
<a name="sectionSection0"> </a>

The **Test-CsInterTrunkRouting** cmdlet verifies that calls can be routed from one SIP to another. To do this, the cmdlet is given a phone number and a trunk configuration. **Test-CsInterTrunkRouting** will then report back matching routes and matching PSTN usages for the specified number. Note that calls can be routed between trunks only if the trunks have a number pattern that matches the specified phone number and only if the trunks share at least one PSTN usage. 
  
## Running the test
<a name="sectionSection1"> </a>

The commands shown below return the matching routes and matching phone usages that enable users to call the phone number 1-206-555-1219 using the trunk configuration settings for the Redmond site.
  
```
$trunk = Get-CsTrunkConfiguration -Identity "site:Redmond"
Test-CsInterTrunkRouting -TargetNumber "tel:+12065551219" -TrunkConfiguration $trunk
```

## Determining success or failure
<a name="sectionSection2"> </a>

If calls can be routed from one SIP to another, you'll receive output similar to this: 
  
FirstMatchingRoute MatchingUsage MatchingRoutes
  
------------------ ------------- --------------
  
RedmondRoute LocalUsage {RedmondRoute}
  
If the test did not succeed, you'll receive output similar to this: 
  
Test-CsInterTrunkRouting : Cannot process argument transformation on parameter
  
'TrunkConfiguration'. Invalid TrunkConfigurationsetting (parameter). Specify a
  
valid setting (parameter) and then try again.
  
At line:1 char:79
  
+ Test-CsInterTrunkRouting -TargetNumber "tel:+12065551219"
  
-TrunkConfiguration $t ...
  
+
  
 ~~ 
  
 + CategoryInfo : InvalidData: (:) [Test-CsInterTrunkRouting], Par 
  
 ameterBindingArgumentTransformationException 
  
 + FullyQualifiedErrorId : ParameterArgumentTransformationError,Microsoft.R 
  
 tc.Management.Voice.Cmdlets.TestOcsInterTrunkRoutingCmdlet 
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

Here are some common reasons why **Test-CsInterTrunkRouting** might fail: 
  
- You specified invalid parameters. The trunk might not yet be correctly configured and the specified target number might be incorrect or invalid. 
    
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsTrunk](get-cstrunk.md)
  
[Get-CsTrunkConfiguration](get-cstrunkconfiguration.md)

