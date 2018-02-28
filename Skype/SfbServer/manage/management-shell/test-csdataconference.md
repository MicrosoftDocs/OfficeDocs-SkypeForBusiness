---
title: "Test-CsDataConference"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: bd7f3c98-7b10-494e-adce-a9b20428b6cc
description: "Verifies whether or not a pair of users can participate in a Skype for Business Server 2015 web conference that includes activities such as sharing or viewing PowerPoint slides, whiteboards, or polls. The cmdlet also verifies that the Skype for Business Server 2015 web conferencing service can discover Office Web Apps Server and that a client can upload a PowerPoint file for broadcast by Office Web Apps Server."
---

# Test-CsDataConference
[]
Verifies whether or not a pair of users can participate in a Skype for Business Server 2015 web conference that includes activities such as sharing or viewing PowerPoint slides, whiteboards, or polls. The cmdlet also verifies that the Skype for Business Server 2015 web conferencing service can discover Office Web Apps Server and that a client can upload a PowerPoint file for broadcast by Office Web Apps Server.
  
This cmdlet was introduced in Lync Server 2013. 
  
```
Test-CsDataConference -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID | OAuth | OAuthInteractive>] [-ReceiverSipAddress <String>] [-RegistrarPort <Int32>] [-SenderSipAddress <String>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 verifies that a data conference can be conducted on the pool atl-cs-001.litwareinc.com. This command assumes that you have configured a pair of test users for the specified pool. If no such test users exist, the command will fail.
  
```
Test-CsDataConference -TargetFqdn "atl-cs-001.litwareinc.com"

```

### Example 2

The commands shown in Example 2 test the ability of a pair of users (litwareinc\pilar and litwareinc\kenmyer) to log on to Skype for Business Server 2015 and then conduct an data conference. To do this, the first command in the example uses the **Get-Credential** cmdlet to create a Windows PowerShell command-line interface credential object containing the name and password of the user Pilar Ackerman. (Because the logon name, litwareinc\pilar, has been included as a parameter, the Windows PowerShell Credential Request dialog box only requires the administrator to enter the password for the Pilar Ackerman account.) The resulting credential object is then stored in a variable named $cred1. The second command does the same thing, this time returning a credential object for the Ken Myer account.
  
With the credential objects in hand, the third command determines whether or not these two users can log on to Skype for Business Server 2015 and conduct a data conference. To carry out this task, the **Test-CsDataConference** cmdlet is called, along with the following parameters: TargetFqdn (the FQDN of the Registrar pool); SenderSipAddress (the SIP address for the first test user); SenderCredential (the Windows PowerShell object containing the credentials for this same user); ReceiverSipAddress (the SIP address for the other test user); and ReceiverCredential (the Windows PowerShell object containing the credentials for the other test user).
  
```
$credential1 = Get-Credential "litwareinc\pilar"
$credential2 = Get-Credential "litwareinc\kenmyer"

Test-CsDataConference -TargetFqdn "atl-cs-001.litwareinc.com" -SenderSipAddress "sip:pilar@litwareinc.com" -SenderCredential $credential1 -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -ReceiverCredential $credential2
```

## Detailed Description
<a name="DetailedDescription"> </a>

In Skype for Business Server 2015, a data conference is any conference where collaborative activities such as whiteboarding or annotations are used. The **Test-CsDataConference** cmdlet enables you to verify that a pair of users are able to take part in a data conference.
  
The ability to conduct a data conference depends on the conferencing policy that has been assigned to the user who organized the conference (in the case of the **Test-CsDataConference** cmdlet, that is the "sender"). If the organizer is not allowed to include collaborative activities in his or her meeting (for example, if his or her conferencing policy has the EnableDataCollaboration property set to False) then the **Test-CsDataConference** cmdlet will fail.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Test-CsDataConference** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ReceiverCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credential object for the first of the two user accounts to be tested. The value passed to ReceiverCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\pilar and stores that object in a variable named $y: <br/>  `$y = Get-Credential "litwareinc\pilar"` <br/> You need to supply the user password when running this command.  <br/> The receiver credential is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _SenderCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credential object for the second of the two user accounts to be tested. The value passed to SenderCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\kenmyer and stores that object in a variable named $x: <br/> $x = Get-Credential "litwareinc\kenmyer"  <br/> You need to supply the user password when running this command.  <br/> The sender credential is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _TargetFqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the Persistent Chat pool to be tested.  <br/> |
| _Authentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+AuthenticationMechanism  <br/> |Type of authentication used when running the test. Allowed values are:  <br/> \* TrustedServer  <br/> \* Negotiate  <br/> \* ClientCertificate  <br/> \* LiveID  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _IPVersion_ <br/> |Optional  <br/> |System.String  <br/> |IP addressing type used to connect to the test conference. Allowed values are:  <br/> IPv4  <br/> IPv6  <br/> Both  <br/> Auto  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/>  `-OutLoggerVariable TestOutput` <br/> Note: Do not prepend a $ character when specifying the variable name.  <br/> To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/>  `$TestOutput.ToHTML() > C:\Logs\TestOutput.html` <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/>  `$TestOutput.ToXML() > C:\Logs\TestOutput.xml` <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/>  `-OutVerboseVariable TestOutput` <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _ReceiverSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address for the first of the two user accounts to be tested. For example:  <br/>  `-ReceiverSipAddress "sip:pilar@litwareinc.com"` <br/> The ReceiverSIPAddress parameter must reference the same user account as ReceiverCredential.  <br/> The SIP address is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |System.Int32  <br/> |SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.  <br/> |
| _SenderSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address for the second of the two user accounts to be tested. For example:  <br/>  `-SenderSipAddress "sip:kenmyer@litwareinc.com"` <br/> The SenderSipAddress parameter must reference the same user account as SenderCredential.  <br/> The SIP address is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _TestJoinLauncher_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, tests the ability of the Join Launcher to participate in a conference. The Join Launcher is used to help users of mobile devices (and, as a result, users of the Mobility Service) take part in conferences.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _HybridOnlineUserAuthentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+HybridOnlineAuthenticationMechanism  <br/> |PARAMVALUE: LiveID | OAuth  <br/> |
| _IsHybridOnlineUser_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _IsPoolInMaintenanceMode_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _SkipWacPptTestScenario_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _TelemetryTenantToken_ <br/> |Optional  <br/> |System.Security.SecureString  <br/> |PARAMVALUE: SecureString  <br/> |
| _TimeToWriteLogToConsole_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Test-CsDataConference** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Test-CsDataConference** cmdlet returns instances of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Test-CsASConference](test-csasconference.md)

