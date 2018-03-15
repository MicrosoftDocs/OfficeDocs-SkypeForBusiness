---
title: "Testing user presence publishing and subscribing in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 27694c71-8e63-4aa4-b49f-fa06ccb81949

description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Testing user presence publishing and subscribing in Lync Server 2013
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
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsPresence cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsPresence"}```|
   
## Description
<a name="sectionSection0"> </a>

Test-CsPresence is used to determine whether a pair of test users can log on to Lync Server and then exchange presence information. To do this, the cmdlet first logs the two users on to the system. If both logons succeed, the first test user then asks to receive presence information from the second user. The second user publishes this information, and Test-CsPresence verifies that the information was successfully transmitted to the first user. After the exchange of presence information, the two test users are then logged off from Lync Server.
  
## Running the test
<a name="sectionSection1"> </a>

The Test-CsPresence cmdlet can be run using either a pair of preconfigured test accounts (see Setting Up Test Accounts for Running Lync Server Tests) or the accounts of any two users who are enabled for Lync Server. To run this check using test accounts, you just have to specify the FQDN of the Lync Server pool being tested. For example:
  
```
Test-CsPresence -TargetFqdn "atl-cs-001.litwareinc.com"
```

To run this check using actual user accounts, you must create two Windows PowerShell credentials objects (objects that contain the account name and password) for each account. You must then include those credentials objects and the SIP addresses of the two accounts when you call Test-CsPresence:
  
```
$credential1 = Get-Credential "litwareinc\kenmyer"
$credential2 = Get-Credential "litwareinc\davidlongmire"
Test-CsPresence -TargetFqdn "atl-cs-001.litwareinc.com" -PublisherSipAddress "sip:kenmyer@litwareinc.com" -PublisherCredential $credential1 -SubscriberSipAddress "sip:davidlongmire@litwareinc.com" -SubscriberCredential $credential2
```

For more information, see the Help documentation for the [Test-CsPresence](test-cspresence.md) cmdlet. 
  
## Determining success or failure
<a name="sectionSection2"> </a>

If the specified users can exchange presence information, then you'll receive output similar to this, with the Result property marked as **Success:**
  
TargetFqdn : atl-cs-001.litwareinc.com
  
Result : Success
  
Latency : 00:00:06.3280315
  
Error :
  
Diagnosis :
  
If the two users can't exchange presence information, then the Result will be shown as Failure, and additional information will be recorded in the Error and Diagnosis properties:
  
TargetFqdn : atl-cs-001.litwareinc.com
  
Result : Failure
  
Latency : 00:00:00
  
Error : 404, Not Found
  
Diagnosis : ErrorCode=4005,Source=atl-cs-001.litwareinc.com,
  
 Reason=Destination URI either not enabled for SIP or does not 
  
 exist. 
  
 Microsoft.Rtc.Signaling.DiagnosticHeader 
  
For example, the previous output states that the test failed because at least one of the two user accounts is not valid: either the account does not exist or it has not been enabled for Lync Server. You can verify that the accounts exist, and determine whether they are enabled for Lync Server, by running a command similar to this:
  
```
"sip:kenmyer@litwareinc.com", "sip:davidlongmire@litwareinc.com" | Get-CsUser | Select-Object SipAddress, Enabled
```

If Test-CsPresence fails, then you might want to rerun the test, this time including the Verbose parameter:
  
```
Test-CsPresence -TargetFqdn "atl-cs-001.litwareinc.com" -Verbose
```

When the Verbose parameter is included, Test-CsPresence will return a step-by-step account of each action it tried when it checked the ability of the specified user to log on to Lync Server. For example:
  
Registration Request hit against Unknown
  
'Register' activity completed in '0.0345791' secs.
  
'SelfSubscribeActivity' activity started.
  
'SelfSubscribeActivity' activity completed in '0.0041174' secs.
  
'SubscribePresence' activity started.
  
'SubscribePresence' activity completed in '0.0038764' secs.
  
'PublishPresence' activity started.
  
An exception 'Presence notification is not received within 25 secs.' occurred ruing Workflow Microsoft.Rtc.SyntheticTransactions.Workflows.STPresenceWorkflow execution.
  
The fact that the presence notification was not received within 25 seconds might indicate that network issues are preventing information from being exchanged.
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

Here are some common reasons why Test-CsPresence might fail:
  
- You specified an incorrect user account. You can verify that a user account exists by running a command similar to this: 
    
  ```
  Get-CsUser "sip:kenmyer@litwareinc.com"
  ```

- The user account is valid, but the account is currently not enabled for Lync Server. To verify that a user account is enabled for Lync Server, run a command similar to the following: 
    
  ```
  Get-CsUser "sip:kenmyer@litwareinc.com" | Select-Object Enabled
  
  ```

    If the Enabled property is set to False that means that the user is currently not enabled for Lync Server.
    

