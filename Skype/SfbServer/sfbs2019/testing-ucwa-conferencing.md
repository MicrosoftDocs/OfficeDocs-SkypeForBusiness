---
title: "Testing UCWA conferencing in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 62b3866a-0759-4b1f-99ec-5a68d6a74f00

description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Testing UCWA conferencing in Lync Server 2013
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
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the **Test-CsUcwaConference** cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsUcwaConference"}```|
   
## Description
<a name="sectionSection0"> </a>

The **Test-CsUcwaConference** cmdlet verifies that a pair of test users can schedule, join, and then conduct an online conference using the Unified Communications Web API (UCWA). To do this, the cmdlet uses the Lync Server web ticket service to authenticate the two test users and register them with Lync Server. The cmdlet then starts a conference using the organizer credentials and invites the participant to join the meeting. After the meeting is joined, the **Test-CsUcwaConference** cmdlet verifies that the users can do such things as exchange instant message and conduct pools, then disconnects the conference and unregisters the two test users. The scheduled conference will also be deleted when the test is finished. 
  
The **Test-CsUcwaConference** cmdlet can also be used to determine whether anonymous users can join online conferences. 
  
Note that the **Test-CsUcwaConference** cmdlet should not be run against a Microsoft Lync Server 2010 pool unless UCWA was installed on that pool. If UCWA has not been installed then the call to the **Test-CsUcwaConference** cmdlet will fail. 
  
## Running the test
<a name="sectionSection1"> </a>

The command shown in Example 1 verifies that a pair of test users can participate in an UCWA conference on the pool atl-cs-001.litwareinc.com. Note that this command will fail if you have not predefined a pair of health monitoring configuration test users for atl-cs-001.litwareinc.com.
  
```
Test-CsUcwaConference -TargetFqdn "atl-cs-001.litwareinc.com"
```

The commands shown in Example 2 test the ability of a pair of users (litwareinc\pilar and litwareinc\kenmyer) to participate in an UCWA conference. To do this, the first command in the example uses the Get-Credential cmdlet to create a Windows PowerShell command-line interface credential object that contains the name and password of the user Pilar Ackerman. (Because the logon name, litwareinc\pilar, was included as a parameter, the Windows PowerShell Credential Request dialog box only requires the administrator to enter the password for the Pilar Ackerman account.) The resulting credentials object is then stored in a variable named $cred1. The second command does the same thing, this time returning a credential object for the Ken Myer account. 
  
With the two credential objects in hand, the third command in the example determines whether the two users can participate in an UCWA conference. To run this task, the **Test-CsUcwaConference** cmdlet is called, together with the following parameters: TargetFqdn (the FQDN of the Registrar pool); OrganizerSipAddress (the SIP address for the meeting organizer); OrganizerCredential (the Windows PowerShell object that contains the credentials for this same user); ParticipantSipAddress (the SIP address for the other test user); and ParticipantCredential (the Windows PowerShell command-line interface object that contains the credentials for the other user). 
  
```
$cred1 = Get-Credential "litwareinc\pilar"
$cred2 = Get-Credential "litwareinc\kenmyer"
Test-CsUcwaConference -TargetFqdn atl-cs-001.litwareinc.com -OrganizerSipAddress "sip:pilar@litwareinc.com" -OrganizerCredential $cred1 -ParticipantSipAddress "sip:kenmyer@litwareinc.com" -ParticipantCredential $cred2
```

## Determining success or failure
<a name="sectionSection2"> </a>

If conferencing is correctly configured, you'll receive output similar to this, with the Result property marked as **Success:**
  
Target Fqdn : atl-cs-001.litwareinc.com
  
Target Uri : https:// LyncTest-SE.LyncTest.SelfHost.Corp.
  
 Microsoft.com:443/CertProv/CertProvisiongService.svc 
  
Result : Success
  
Latency : 00:00:14.9862716
  
Error Message :
  
Diagnosis :
  
If the specified users can't use conferencing, the Result will be shown as **Failure**, and additional information will be recorded in the Error and Diagnosis properties:
  
WARNING: Failed to read Registrar port number for the given fully qualified
  
domain name (FQDN). Using default Registrar port number. Exception: 
  
System.InvalidOperationException: No matching cluster found in topology. 
  
 at 
  
Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction.TryRetri
  
eveRegistrarPortFromTopology(Int32&amp; registrarPortNumber) 
  
Test-CsUcwaConference : There is no test user assigned for
  
[LyncTest.SelfHost.Corp.Microsoft.com]. Verify test user configuration. 
  
At line:1 char:1
  
+ Test-CsUcwaConference -TargetFqdn "LyncTest.SelfHost.Corp.Microsoft.com"
  
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  
 + CategoryInfo : ResourceUnavailable: (:) [Test-CsUcwaConference] 
  
 , InvalidOperationException 
  
 + FullyQualifiedErrorId : NotFoundTestUsers,Microsoft.Rtc.Management.Synth 
  
 eticTransactions.TestUcwaConferenceCmdlet 
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

Here are some common reasons why **Test-CsUcwaConference** might fail: 
  
- An incorrect parameter value was supplied. If used, the optional parameters must be configured correctly or the test will fail. Rerun the command without the optional parameters and see whether that succeeds. 
    
- The ability to conduct a conference depends on the conferencing policy that has been assigned to the user who organized the conference (in the case of the **Test-CsUcwaConference** cmdlet, that is the "sender"). If the organizer is not allowed to include collaborative activities in his or her meeting (for example, if his or her conferencing policy has the EnableDataCollaboration property set to False) then the **Test-CsUcwaConference** cmdlet will fail. 
    
- This command will fail if the Edge Server is misconfigured or not yet deployed.
    
## See also
<a name="sectionSection3"> </a>

#### 

[Test-CsASConference](test-csasconference.md)
  
[Test-CsDataConference](test-csdataconference.md)
  
[Test-CsAVConference](test-csavconference.md)

