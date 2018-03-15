---
title: "Testing the ability of a user to log on to Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d9cd0f9b-6ef2-4050-a4ca-263c5afa93ee

description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Testing the ability of a user to log on to Lync Server 2013
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
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsRegistration cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsRegistration"}```|
   
## Description
<a name="sectionSection0"> </a>

The Test-CsRegistration cmdlet enables you to verify that users in your organization can log on to Lync Server. When you run Test-CsRegistration, the cmdlet attempts to sign in a test user to Lync Server and then, if it is successful, disconnects that test user from the system. All of this happens without any user interaction, and without affecting any actual users. For example, suppose that the test account sip:kenmyer@litwareinc.com corresponds to a real user who has a real Lync Server account. In that case, the test will be conducted without any disruption to the real Ken Myer. When the Ken Myer test account logs off from the system, Ken Myer the person will remain logged on.
  
## Running the test
<a name="sectionSection1"> </a>

The Test-CsRegistration cmdlet can be run using either a preconfigured test account (see Setting Up Test Accounts for Running Lync Server Tests) or the account of any user who is enabled for Lync Server. To run this check using a test account, you just have to specify the FQDN of the Lync Server Registrar pool being tested. For example:
  
```
Test-CsRegistration -TargetFqdn "atl-cs-001.litwareinc.com"
```

To run this check using an actual user account, you must first create a Windows PowerShell credentials object that contains the account name and password. You must then include that credentials object and the SIP address assigned to the account when you call Test-CsRegistration:
  
```
$credential = Get-Credential "litwareinc\kenmyer"
Test-CsRegistration -TargetFqdn "atl-cs-001.litwareinc.com"-UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential
```

For more information, see the Help documentation for the [Test-CsRegistration](test-csregistration.md) cmdlet. 
  
## Determining success or failure
<a name="sectionSection2"> </a>

If the specified user can log on to (and then log off from) Lync Server, you'll receive output similar to this with the Result property marked as **Success:**
  
TargetFqdn : atl-cs-001.litwareinc.com
  
Result : Success
  
Latency : 00:00:06.8630376
  
Error :
  
Diagnosis :
  
If the specified user can't log in or log out, the Result will be shown as Failure, and additional information will be recorded in the Error and Diagnosis properties:
  
TargetFqdn : atl-cs-001.litwareinc.com
  
Result : Failure
  
Latency : 00:00:00
  
Error : 404, Not Found
  
Diagnosis : ErrorCode=1003,source=atl-cs-001.litwareinc.com,Reason=User does
  
 not exist 
  
 Microsoft.Rtc.Signaling.DiagnosticHeader 
  
For example, the previous output states that the test failed because the specified user couldn't be found. You can determine whether or not a SIP address is valid (and whether the user assigned that SIP address is enabled for Lync Server) by running this command:
  
```
Get-CsUser "sip:kenmyer@litwareinc.com"
```

If Test-CsRegistration fails, then you might want to rerun the test, this time including the Verbose parameter:
  
```
Test-CsRegistration -UserSipAddress "sip:kenmyer@litwareinc.com" -TargetFqdn "atl-cs-001.litwareinc.com" -Verbose
```

When the Verbose parameter is included, Test-CsRegistration will return a step-by-step account of each action it tried when it checked the ability of the specified user to log on to Lync Server. For example:
  
VERBOSE: 'Register' activity started.
  
Sending Registration request:
  
 Target Fqdn = atl-cs-011.litwareinc.com 
  
 User Sip Address = sip:kenmyer@litwareinc.com 
  
 Registrar Port = 5061. 
  
Auth Type 'Trusted' is selected.
  
An exception 'The endpoint is unable to register. See the ErrorCode for specific reason' occurred during Workflow Microsoft.Rtc.SyntheticTransactions.Workflow.STRegistrerWorkflow execution.
  
Exception Call Stack: at Microsoft.Rtc.Signaling.SipAsyncResult'1.ThrowIfFailed()
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

Here are some common reasons why Test-CsRegistration might fail:
  
- You specified an incorrect user account. You can verify that a user account exists by running a command similar to this: 
    
  ```
  Get-CsUser "sip:kenmyer@litwareinc.com"
  ```

- The user account is valid, but the account is currently not enabled for Lync Server. To verify that a user account is enabled for Lync Server, run a command similar to the following: 
    
  ```
  Get-CsUser "sip:kenmyer@litwareinc.com" | Select-Object Enabled
  ```

    If the Enabled property is set to False, that means that the user is currently not enabled for Lync Server.
    
- You specified an incorrect Registrar pool. You can return the FQDNs of your Registrar pools by using this command: 
    
  ```
  Get-CsService -Registrar | Select-Object PoolFqdn
  ```

- The Registrar pool is currently not available. Try pinging the pool to see whether it responds: 
    
  ```
  ping atl-cs-001.litwareinc.com
  ```

