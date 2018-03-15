---
title: "Testing LIS server configuration in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6b06e7ab-522f-41a2-878b-e89cd4e3c6da

description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Testing LIS server configuration in Lync Server 2013
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
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsLisConfiguration cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsLisConfiguration"}```|
   
## Description
<a name="sectionSection0"> </a>

The Test-CsLisConfiguration cmdlet verifies your ability to contact the LIS web service. If the web service can be contacted, then the test will be considered a success, regardless of whether any specific locations can be found. 
  
## Running the test
<a name="sectionSection1"> </a>

The Test-CsLisConfguration cmdlet can be run using either a preconfigured test account (see Setting Up Test Accounts for Running Lync Server Tests) or the account of any user who is enabled for Lync Server. To run this check using a test account, you just have to specify the FQDN of the Lync Server pool being tested. For example:
  
```
Test-CsLisConfiguration -TargetFqdn "atl-cs-001.litwareinc.com"
```

To run this check using an actual user account, you must first create a Windows PowerShell credentials object that contains the account name and password. You must then include that credentials object and the SIP address assigned to the account when you call Test-CsLisConfiguration: 
  
```
$credential = Get-Credential "litwareinc\kenmyer"
Test-CsLisConfiguration -TargetFqdn "atl-cs-001.litwareinc.com"-UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential
```

For more information, see the Help documentation for the [Test-CsLisConfiguration](test-cslisconfiguration.md) cmdlet. 
  
## Determining success or failure
<a name="sectionSection2"> </a>

If the LIS is correctly configured, you'll receive output similar to this, with the Result property marked as **Success:**
  
TargetUri : https://atl-cs-001.litwareinc.com:443/locationinformation/
  
 liservice.svc 
  
TargetFqdn : atl-cs-001.litwareinc.com
  
Result : Success
  
Latency : 00:00:06.1616913
  
Error :
  
Diagnosis :
  
If the specified user can't log on or log off, the Result will be shown as Failure, and additional information will be recorded in the Error and Diagnosis properties:
  
TargetUri :
  
TargetFqdn : atl-cs-001.litwareinc.com
  
Result : Failure
  
Latency : 00:00:00
  
Error : 11004, The requested name is valid but no data of the requested
  
 type was found 
  
Diagnosis :
  
Test-CsLisConfiguration : No matching cluster found in topology.
  
For example, the previous output includes the note "No matching cluster found in topology." That typically indicates a problem with the Edge Server: the LIS using the Edge Server to connect to the service provider and validate addresses. 
  
If Test-CsLisConfiguration fails then you might want to rerun the test, this time including the Verbose parameter: 
  
```
Test-CsLisConfiguration -TargetFqdn "atl-cs-001.litwareinc.com" -Verbose
```

When the Verbose parameter is included, Test-CsLisConfiguration will return a step-by-step account of each action it tried when it checked the ability of the specified user to log on to Lync Server. For example: 
  
Calling Location Information Service.
  
 Service Path = https://atl-cs-001.litwareinc.com:443/locationinformation/liservice.svc 
  
 Subnet = 
  
 BssId = 5 
  
 ChassisId = 
  
 PortId = 
  
 PortIdSubType = Undefined Type 
  
 Mac 
  
An exception 'Location Information Web Service request has failed with a response code Item400.' occurred during Workflow Microsoft.Rtc.SyntheticTrsnactions.Workflows.STLisConfigurationWorkflow execution.
  
If you examine the previous output closely, you'll see that the cmdlet failed after it tried to call the Location Information Service. One of the parameters that were used in that call was this: 
  
BssId = 5
  
That's not a valid value for the Basic Service Set Identifier (BssID). Instead, a BssID should resemble this: 
  
12-34-56-78-90-ab
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

Here are some common reasons why Test-CsLisConfiguration might fail:
  
- An incorrect parameter value was supplied. As shown in the previous example, the optional parameters must be configured correctly or the test will fail. Rerun the command without the optional parameters and see whether that succeeds. 
    

