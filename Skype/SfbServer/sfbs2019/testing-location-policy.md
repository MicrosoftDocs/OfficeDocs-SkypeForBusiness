---
title: "Testing location policy in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 23d06fd3-31ee-4480-ba1e-d179a55b8b14

description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Testing location policy in Lync Server 2013
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
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsLocationPolicy cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsLocationPolicy"}```|
   
## Description
<a name="sectionSection0"> </a>

The Test-CsLocationPolicy cmdlet verifies that a location policy is assigned to a user. The location policy is used to apply settings that relate to E9-1-1 functionality and client location. The location policy determines whether a user is enabled for E9-1-1, and, if the answer is "yes,", what the behavior is of an emergency call. For example, you can use the location policy to define what number makes up an emergency call (911 in the United States), whether corporate security should be automatically notified, and how the call should be routed. 
  
You can test location policies on users or on network subnets. If you run the test against a subnet (by specifying a value for the Subnet parameter), the cmdlet will attempt to resolve the location policy for that subnet. If no location policy is assigned to the subnet, the location policy for the configured user will be retrieved. If the subnet policy is retrieved successfully, the output will include a LocationPolicyTagID value that begins with subnet-tagid. If a location policy for the subnet was not found, the LocationPolicyTagID will begin with user-tagid.
  
## Running the test
<a name="sectionSection1"> </a>

The Test-CsLocationPolicy cmdlet can be run using either a preconfigured test account (see Setting Up Test Accounts for Running Lync Server Tests) or the account of any user who is enabled for Lync Server. To run this check using a test account, you just have to specify the FQDN of the Lync Server pool being tested. For example:
  
```
Test-CsLocationPolicy -TargetFqdn "atl-cs-001.litwareinc.com"
```

To run this check using an actual user account, you must first create a Windows PowerShell credentials object that contains the account name and password. You must then include that credentials object and the SIP address assigned to the account when you call Test-CsLocationPolicy:
  
```
$credential = Get-Credential "litwareinc\kenmyer"
Test-CsLocationPolicy -TargetFqdn "atl-cs-001.litwareinc.com"-UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential
```

For more information, see the Help documentation for the [Test-CsLocationPolicy](test-cslocationpolicy.md) cmdlet. 
  
## Determining success or failure
<a name="sectionSection2"> </a>

If the specified user has a valid location policy, then you'll receive output similar to this, with the Result property marked as **Success:**
  
EnhancedEmergencyServicesEnabled : true
  
LocationPolicyTagID : user-tagid
  
TargetFqdn : atl-cs-001.litwareinc.com
  
Result : Success
  
Latency : 00:00:06.8630376
  
Error :
  
Diagnosis :
  
If a valid location policy cannot be found for the specified user, then Result will be shown as Failure, and additional information will be recorded in the Error and Diagnosis properties: 
  
TargetFqdn : atl-cs-001.litwareinc.com
  
Result : Failure
  
Latency : 00:00:00
  
Error : 404, Not Found
  
Diagnosis : ErrorCode=4005,Source=atl-cs-001.litwareinc.com,
  
 Reason=Destination URI either not enabled for SIP or does not 
  
 exist. 
  
 Microsoft.Rtc.Signaling.DiagnosticHeader 
  
The previous output states that the test failed because the specified user is not valid: either the account does not exist or the user has not been enabled for Lync Server. You can verify the validity of an account, and determine whether or not that account has been enabled for nm-ocs-14-3rd, by running a command similar to this:
  
```
Get-CsUser "sip:kenmyer@litwareinc.com" | Select-Object SipAddress, Enabled
```

If Test-CsLocationPolicy fails, then you might want to rerun the test, this time including the Verbose parameter: 
  
```
Test-CsLocationPolicy -TargetFqdn "atl-cs-001.litwareinc.com" -Verbose
```

When the Verbose parameter is included, Test-CsLocationPolicy will return a step-by-step account of each action it tried when verifying the location policy. For example, this output indicates that Lync Server couldn't log on the test user, probably because an invalid password was supplied: 
  
Sending Registration request :
  
 Target Fqdn = atl-cs-011.litwareinc.com 
  
 User Sip Address = sip:kenmyer@litwareinc.com 
  
 Registrar Port = 5061 
  
Auth Type 'IWA' is selected.
  
Registration hit against sip/atl-cs-001.litwareinc.com
  
'Register' activity completed in '0.0601795' secs.
  
An exception 'The log on was denied. Check that the correct credentials are being used and the account is active.' occurred during the Workflow.
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

Here are some common reasons why Test-CsLocationPolicy might fail:
  
- You specified a user account that is not valid. You can verify that a user account exists by running a command similar to this: 
    
  ```
  Get-CsUser "sip:kenmyer@litwareinc.com"
  ```

- The user account is valid, but the account is currently not enabled for Lync Server. To verify that a user account is enabled for Lync Server, run a command similar to the following: 
    
  ```
  Get-CsUser "sip:kenmyer@litwareinc.com" | Select-Object Enabled
  ```

    If the Enabled property is set to False, that means that the user is currently not enabled for Lync Server.
    

