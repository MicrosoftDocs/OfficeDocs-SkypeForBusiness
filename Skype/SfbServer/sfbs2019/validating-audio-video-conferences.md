---
title: "Validating audio/video conferences in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6c8c422a-d501-42cb-820b-b002f9b2250b

description: "In this articleDescriptionRunning the testDetermining Success or FailureReasons why the test might have failed"
---

# Validating audio/video conferences in Lync Server 2013
[]
 **In this article**
  
[Description](#sectionSection0)
  
[Running the test](#sectionSection1)
  
[Determining Success or Failure](#sectionSection2)
  
[Reasons why the test might have failed](#sectionSection3)
  
****

|||
|:-----|:-----|
|||
|Verification schedule  <br/> |Daily  <br/> |
|Testing tool  <br/> |Windows PowerShell  <br/> |
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsAVConference cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsAVConference"}```|
   
## Description
<a name="sectionSection0"> </a>

The Test-CsAVConference cmdlet checks whether two test users can participate in an audio/video (A/V) conference. When the cmdlet runs, the two users are logged on to the system. After they face successfully logged on, the first user creates an A/V conference, and then waits for the second user to join that conference. After a brief exchange of data, the conference is deleted and the two tests users are logged off. 
  
Note that Test-CsAVConference does not conduct an actual A/V conference between the two test users. Instead, the cmdlet verifies that the two users can make all the connections necessary to conduct such a conference.
  
Further examples for this command can be found at [Test-CsAVConference](test-csavconference.md).
  
## Running the test
<a name="sectionSection1"> </a>

The Test-CsAVConference cmdlet can be run using either a pair of preconfigured test accounts (see Setting Up Test Accounts for Running Lync Server Tests) or the accounts of any two users who are enabled for Lync Server. To run this check using test accounts, you just have to specify the FQDN of the Lync Server pool being tested. For example:
  
```
Test-CsAVConference -TargetFqdn "atl-cs-001.litwareinc.com"
```

To run this check using actual user accounts, you must create two Windows PowerShell credentials objects (objects that contain the account name and password) for each account. You must then include those credentials objects and the SIP addresses of the two accounts when they call Test-CsAVConference:
  
```
$credential1 = Get-Credential "litwareinc\kenmyer"
$credential2 = Get-Credential "litwareinc\davidlongmire"
Test-CsAVConference -TargetFqdn "atl-cs-001.litwareinc.com" -SenderSipAddress "sip:kenmyer@litwareinc.com" -SenderCredential $credential1 -ReceiverSipAddress "sip:davidlongmire@litwareinc.com" -ReceiverCredential $credential2
```

For more information, see the Help documentation for the [Test-CsAVConference](test-csavconference.md) cmdlet. 
  
## Determining Success or Failure
<a name="sectionSection2"> </a>

If the specified users can successfully complete an A/V conference, you'll receive output similar to this, with the Result property marked as **Success:**
  
TargetFqdn : atl-cs-001.litwareinc.com
  
Result : Success
  
Latency : 00:00:02.6841765
  
Error : 
  
Diagnosis : 
  
If the users can not complete the conference, then the Result will be shown as Failure, and additional information will be recorded in the Error and Diagnosis properties:
  
TargetFqdn : atl-cs-001.litwareinc.com
  
Result : Failure
  
Latency : 00:00:00
  
Error : 404, Not Found
  
Diagnosis : ErrorCode=4005,Source=atl-cs-001.litwareinc.com,
  
 Reason=Destination URI either not enabled for SIP or does not 
  
 exist. 
  
 Microsoft.Rtc.Signaling.DiagnosticHeader 
  
For example, the previous output states that the test failed because at least one of the two user accounts was not valid, either because the account does not exist or because the account has not been enabled for Lync Server. You can verify the existence of the two test accounts, and whether they were enabled for Lync Server, by running a command similar to the following: 
  
```
"sip:kenmyer@litwareinc.com","sip:davidlongmire@litwareinc.com" | Get-CsUser | Select-Object SipAddress, enabled
```

If Test-CsAVConference fails, then you might want to rerun the test, this time including the Verbose parameter: 
  
```
Test-CsAVConference -TargetFqdn "atl-cs-001.litwareinc.com" -Verbose
```

When the Verbose parameter is included Test-CsAVConference will return a step-by-step account of each action it tried when it checked the ability of the specified users to participate in an AV conference. For example, suppose that your test fails and you receive the following Diagnosis: 
  
ErrorCode=1008,Source=accessproxy.litwareinc.com,Reason=Unable to resolve DNS SRV record
  
If you rerun the test using the Verbose parameter, the step-by-step information returned will include output similar to this: 
  
VERBOSE: 'Register' activity started.
  
Sending Registration request:
  
Target Fqdn = atl-cs-001.litwareinc.com
  
User Sip Address = sip:davidlongmire@litwareinc.com
  
Registrar Port = 5061.
  
Auth Type 'Trusted' is selected.
  
'Register' activity started.
  
Sending Registration request:
  
 Target Fqdn = atl-cs-001.litwareinc.com 
  
 User Sip Address = sip:kenmyer@litwareinc.com 
  
 Registrar Port = 5061. 
  
Auth Type 'Trusted' is selected.
  
An exception 'The endpoint was unable to register. See the ErrorCode for specific reason.' occurred during Workflow
  
The last line in that output indicates that the user sip:kenmyer@litwareinc.com was unable to register with Lync Server. That means that you should verify that the SIP address sip:kenmyer@litwareinc.com is valid, and that the associated user is enabled for Lync Server.
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

Here are some common reasons why Test-CsAVConference might fail:
  
- You specified a user account that is not valid. You can verify that a user account exists by running a command similar to this: 
    
  ```
  Get-CsUser "sip:kenmyer@litwareinc.com"
  ```

- The user account is valid, but the account is currently not enabled for Lync Server. To verify that a user account is enabled for Lync Server, run a command similar to the following: 
    
  ```
  Get-CsUser "sip:kenmyer@litwareinc.com" | Select-Object Enabled
  ```

    If the Enabled property is set to False that means that the user is currently not enabled for Lync Server.
    

