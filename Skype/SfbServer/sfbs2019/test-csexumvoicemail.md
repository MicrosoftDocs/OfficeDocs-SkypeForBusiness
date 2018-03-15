---
title: "Test-CsExUMVoiceMail"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 88734ae8-1339-4080-a4bb-544181f6d1d2
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Test-CsExUMVoiceMail
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Verifies that a user can connect to Exchange Unified Messaging and leave a voice mail message for another user. This cmdlet was introduced in Lync Server 2013.
  
```
Test-CsExUMVoiceMail -ReceiverSipAddress <String> -SenderCredential <PSCredential> -SenderSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] [-WaveFile <String>] <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

The preceding example tests Exchange Unified Messaging voice mail connectivity for the pool atl-cs-001.litwareinc.com. This command will work only if test users have been defined for the pool atl-cs-001.litwareinc.com. If they have, then the command will determine whether or not the first test user is able to use Unified Messaging voice mail. If test users have not been configured for the pool then the command will fail.
  
```
Test-CsExUMVoiceMail -TargetFqdn "atl-cs-001.litwareinc.com" -ReceiverSipAddress "sip:kenmyer@litwareinc.com"
```

### Example 2

The commands shown in Example 2 test Exchange Unified Messaging voice mail connectivity for the user litwareinc\kenmyer. To do this, the first command in the example uses the **Get-Credential** cmdlet to create a Windows PowerShell command-line interface credentials object for the user litwareinc\kenmyer. Note that you must supply the password for this account in order to create a valid credentials object and to ensure that the **Test-CsExUMVoiceMail** cmdlet can carry out its check. 
  
The second command in the example uses the supplied credentials object ($x) and the SIP address of the user litwareinc\kenmyer in order to determine whether or this user can connect to Exchange Unified Messaging voice mail.
  
```
$credential = Get-Credential "litwareinc\pilar"
Test-CsExUMVoiceMail -TargetFqdn "atl-cs-001.litwareinc.com" -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -SenderSipAddress "sip:pilar@litwareinc.com" -SenderCredential $credential
```

### Example 3

The command shown in Example 3 is a variation of the command shown in Example 1; in this case, however, the OutLoggerVariable parameter is included in order to generate a detailed log of every step undertaken by the **Test-CsExUMVoiceMail** cmdlet, as well as the success or failure of each of those steps. To do this, the OutLoggerVariable parameter is added along with the parameter value ExumText; that causes detailed logging information to be stored in a variable named $ExumTest. In the final command in the example, the ToXML() method is used to convert the log information to XML format. That XML data is then written to a file named C:\Logs\VoicemailTest.xml by using the Out-File cmdlet. 
  
```
Test-CsExUMVoiceMail -TargetFqdn "atl-cs-001.litwareinc.com" -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -OutLoggerVariable VoicemailTest
$VoicemailTest.ToXML() | Out-File C:\Logs\VoicemailTest.xml
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Test-CsExUMVoiceMail** cmdlet enables administrators to verify that a user can access, and make use of, the Microsoft Exchange Server 2013 unified messaging service. To do this, the cmdlet connects to the unified messaging service and leaves a voice mail in the specified mailbox. This can be a system-supplied voice mail, or it can be a custom .WAV file that you have recorded yourself. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsExUMVoiceMail"}
  
 **Lync Server Control Panel:** The functions carried out by the Test-CsExUMVoiceMail cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _SenderCredential_ <br/> |Required  <br/> |PSCredential  <br/> |User credential object for the user account that will be leaving the voicemail message. The value passed to SenderCredential must be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\kenmyer and stores that object in a variable named $x:  <br/> $x = Get-Credential "litwareinc\kenmyer"  <br/> You need to supply the user password when running this command.  <br/> The sender credential is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _TargetFqdn_ <br/> |Required  <br/> |String  <br/> |Fully qualified domain name (FQDN) of the pool to be tested. For example:  <br/> -TargetFqdn atl-cs-001.litwareinc.com  <br/> |
| _Authentication_ <br/> |Optional  <br/> |SipSyntheticTransaction AuthenticationMechanism  <br/> |Type of authentication used when running the test. Allowed values are:  <br/> \* TrustedServer  <br/> \* Negotiate  <br/> \* ClientCertificate  <br/> \* LiveID  <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/> -OutLoggerVariable TestOutput  <br/> Note: Do not use prepend a $ character when specifying the variable name.  <br/> To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/> $TestOutput.ToHTML() \> C:\Logs\TestOutput.html  <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/> $TestOutput.ToXML() \> C:\Logs\TestOutput.xml  <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/> -OutVerboseVariable TestOutput  <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _ReceiverSipAddress_ <br/> |Optional  <br/> |String  <br/> |SIP address for the user account that should receive the test voice mail (this must be a different SIP address than the SIP address used for the sender). For example:  <br/> -ReceiverSipAddress "sip:pilar@litwareinc.com"  <br/> You do not have to include credentials for the voicemail recipient.  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |Int32  <br/> |SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.  <br/> |
| _SenderSipAddress_ <br/> |Optional  <br/> |String  <br/> |SIP address for the user account that will be leaving the voicemail message (this must be a different SIP address than the SIP address used for the receiver). For example:  <br/> -SenderSipAddress "sip:kenmyer@litwareinc.com"  <br/> The SenderSIPAddress parameter must reference the same user account as SenderCredential.  <br/> The SIP address is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _WaveFile_ <br/> |Optional  <br/> |String  <br/> |Path to .WAV audio file that can be used when testing the voice mail service. If this parameter is included, the **Test-CsExUMVoiceMail** cmdlet will play the specified .WAV file when connecting to Exchange voicemail. If this parameter is not included, a default audio file will be played instead.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The Test-CsExUMVoiceMail cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Test-CsExUMVoiceMail** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Test-CsExUMConnectivity](test-csexumconnectivity.md)

