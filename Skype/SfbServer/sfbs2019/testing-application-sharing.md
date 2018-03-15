---
title: "Testing application sharing in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8d21db9b-10d1-4b43-b057-0deb1df1c205

description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Testing application sharing in Lync Server 2013
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
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsASConference cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsASConference"}```|
   
## Description
<a name="sectionSection0"> </a>

The **Test-CsASConference** cmdlet verifies that a pair of test users can participate in an online conference that includes application sharing. To do this, the cmdlet registers the two users with Lync Server 2013, and then it uses one of the user accounts to create a new conference that includes applications sharing. The cmdlet then verifies that the second user is able to join that conference. 
  
## Running the test
<a name="sectionSection1"> </a>

The command shown in Example 1 verifies that an Application Sharing conference can be conducted on the pool atl-cs-001.litwareinc.com. This command assumes that you have configured a pair of test users for the specified pool. If no such test users exist, the command will fail. 
  
```
Test-CsASConference -TargetFqdn "atl-cs-001.litwareinc.com"

```

Example 2 tests the ability of the Join Launcher service to participate in an Application Sharing conference on the pool atl-cs-001.litwareinc.com. Note that this command tests only the service itself; you do not need any mobile devices in order to run the command. 
  
```
Test-CsASConference -TargetFqdn "atl-cs-001.litwareinc.com" -TestJoinLauncher 
```

The commands shown in Example 2 test the ability of a pair of users (litwareinc\pilar and litwareinc\kenmyer) to log on to Lync Server 2013 and then conduct an Application Sharing conference. To do this, the first command in the example uses the Get-Credential cmdlet to create a Windows PowerShell command-line interface credential object containing the name and password of the user Pilar Ackerman. (Because the logon name, litwareinc\pilar, has been included as a parameter, the Windows PowerShell Credential Request dialog box only requires the administrator to enter the password for the Pilar Ackerman account.) The resulting credential object is then stored in a variable named $cred1. The second command does the same thing, this time returning a credential object for the Ken Myer account. 
  
With the credential objects in hand, the third command determines whether or not these two users can log on to Lync Server 2013 and conduct an Application Sharing conference. To carry out this task, the **Test-CsASConference** cmdlet is called, along with the following parameters: TargetFqdn (the FQDN of the Registrar pool); SenderSipAddress (the SIP address for the first test user); SenderCredential (the Windows PowerShell object containing the credentials for this same user); ReceiverSipAddress (the SIP address for the other test user); and ReceiverCredential (the Windows PowerShell object containing the credentials for the other test user). 
  
```
$cred1 = Get-Credential "litwareinc\pilar" 
$cred2 = Get-Credential "litwareinc\kenmyer" 
Test-CsASConference -TargetFqdn atl-cs-001.litwareinc.com -SenderSipAddress "sip:pilar@litwareinc.com" -SenderCredential $cred1 -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -ReceiverCredential $cred2
```

## Determining success or failure
<a name="sectionSection2"> </a>

If application sharing is correctly configured, you'll receive output similar to this, with the Result property marked as **Success:**
  
Target Fqdn : atl-cs-001.litwareinc.com
  
Result : Success
  
Latency : 00:00:01
  
Error Message :
  
Diagnosis :
  
If the specified users can't share applications, the Result will be shown as Failure, and additional information will be recorded in the Error and Diagnosis properties:
  
Target Fqdn : atl-cs-001.litwareinc.com
  
Result : Failure
  
Latency : 00:00:00
  
Error Message : 10060, A connection attempt failed because the connected party
  
 did not properly respond after a period of time, or 
  
 established connection failed because connected host has 
  
 failed to respond 10.188.116.96:5061 
  
 Inner Exception:A connection attempt failed because the 
  
 connected party did not properly respond after a period of 
  
 time, or established connection failed because connected host 
  
 has failed to respond 10.188.116.96:5061 
  
Diagnosis :
  
For example, the previous output includes the note "the connected party did not properly respond" That typically indicates a problem with the Edge Server.
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

Here are some common reasons why **Test-CsASConference** might fail: 
  
- An incorrect parameter value was supplied. If used, the optional parameters must be configured correctly or the test will fail. Rerun the command without the optional parameters and see whether that succeeds. 
    
- This command will fail if the test users were assigned a conferencing policy that prevents them from using application sharing.
    
- This command will fail if the Edge Server is misconfigured or not yet deployed.
    
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsConferencingPolicy](get-csconferencingpolicy.md)
  
[Test-CsDataConference](test-csdataconference.md)

