---
title: "Testing user connection to Exchange UM voicemail in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 574da104-8823-4061-9fb6-353639f1884d

description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Testing user connection to Exchange UM voicemail in Lync Server 2013
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
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the **Test-CsExUMVoiceMail** cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsExUMVoiceMail"}```|
   
## Description
<a name="sectionSection0"> </a>

The **Test-CsExUMVoiceMail** cmdlet enables administrators to verify that a user can access and use the Microsoft Exchange Server 2013 unified messaging service. To do this, the cmdlet connects to the unified messaging service and leaves a voice mail in the specified mailbox. This can be a system-supplied voice mail, or it can be a custom .WAV file that you have recorded yourself. 
  
## Running the test
<a name="sectionSection1"> </a>

The following example tests Exchange Unified Messaging voice mail connectivity for the pool atl-cs-001.litwareinc.com. This command will work only if test users were defined for the pool atl-cs-001.litwareinc.com. If they have, then the command will determine whether the first test user can use Unified Messaging voice mail. If test users were not configured for the pool then the command will fail. 
  
```
Test-CsExUMVoiceMail -TargetFqdn "atl-cs-001.litwareinc.com" -ReceiverSipAddress "sip:kenmyer@litwareinc.com" 
```

The commands shown in the next example test Exchange Unified Messaging voice mail connectivity for the user litwareinc\kenmyer. To do this, the first command in the example uses the **Get-Credential** cmdlet to create a Windows PowerShell command-line interface credentials object for the user litwareinc\kenmyer. Note that you must supply the password for this account to create a valid credentials object and to ensure that the **Test-CsExUMVoiceMail** cmdlet can run its check. 
  
The second command in the example uses the supplied credentials object ($x) and the SIP address of the user litwareinc\kenmyer to determine whether or this user can connect to Exchange Unified Messaging voice mail. 
  
```
$credential = Get-Credential "litwareinc\pilar" 
Test-CsExUMVoiceMail -TargetFqdn "atl-cs-001.litwareinc.com" -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -SenderSipAddress "sip:pilar@litwareinc.com" -SenderCredential $credential 
```

The command shown in the next example is a variation of the command shown in Example 1; in this case, the OutLoggerVariable parameter is included to generate a detailed log of every step done by the **Test-CsExUMVoiceMail** cmdletand the success or failure of each of those steps. To do this, the OutLoggerVariable parameter is added alongside the parameter value ExumText; that causes detailed logging information to be stored in a variable named $ExumTest. In the final command in the example, the ToXML() method is used to convert the log information to XML format. That XML data is then written to a file that is named C:\Logs\VoicemailTest.xml by using the Out-File cmdlet. 
  
```
Test-CsExUMVoiceMail -TargetFqdn "atl-cs-001.litwareinc.com" -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -OutLoggerVariable VoicemailTest 
 
$VoicemailTest.ToXML() | Out-File C:\Logs\VoicemailTest.xml
```

## Determining success or failure
<a name="sectionSection2"> </a>

If Exchange integration is correctly configured, you'll receive output similar to this, with the Result property marked as **Success**:
  
Target Fqdn : atl-cs-001.litwareinc.com
  
Result : Success
  
Latency : 00:00:02.9911345
  
Error Message :
  
Diagnosis :
  
If the specified user can't connect to voicemail, the Result will be shown as **Failure**, and additional information will be recorded in the Error and Diagnosis properties:
  
WARNING: Failed to read Registrar port number for the given fully qualified
  
domain name (FQDN). Using default Registrar port number. Exception:
  
System.InvalidOperationException: No matching cluster found in topology.
  
 at 
  
Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction.TryRetri
  
eveRegistrarPortFromTopology(Int32&amp; registrarPortNumber)
  
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
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

Here are some common reasons why **Test-CsExUMVoiceMail** might fail: 
  
- An incorrect parameter value was supplied. If used, the optional parameters must be configured correctly or the test will fail. Rerun the command without the optional parameters and see whether that succeeds. 
    
- This command will fail if the Exchange Server is misconfigured or not yet deployed. 
    
## See also
<a name="sectionSection3"> </a>

#### 

[Test-CsExUMConnectivity](test-csexumconnectivity.md)

