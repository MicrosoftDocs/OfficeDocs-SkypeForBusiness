---
title: "Test-CsUcwaConference"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 4e01c4d6-7b81-4932-a8e1-4d14989b71bd
description: "Tests the ability of a pair of users to schedule, join, and then conduct an online conference using the Unified Communications Web API (UCWA). This cmdlet was introduced in Lync Server 2013."
---

# Test-CsUcwaConference
 
Tests the ability of a pair of users to schedule, join, and then conduct an online conference using the Unified Communications Web API (UCWA). This cmdlet was introduced in Lync Server 2013.
  
```
Test-CsUcwaConference -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID | OAuth | OAuthInteractive>] [-OrganizerSipAddress <String>] [-ParticipantSipAddress <String>] [-RegistrarPort <Int32>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 verifies that a pair of test users can participate in an UCWA conference on the pool atl-cs-001.litwareinc.com. Note that this command will fail if you have not predefined a pair of health monitoring configuration test users for atl-cs-001.litwareinc.com.
  
```
Test-CsUcwaConference -TargetFqdn "atl-cs-001.litwareinc.com"
```

### Example 2

The commands shown in Example 2 test the ability of a pair of users (litwareinc\pilar and litwareinc\kenmyer) to participate in an UCWA conference. To do this, the first command in the example uses the **Get-Credential** cmdlet to create a Windows PowerShell command-line interface credential object containing the name and password of the user Pilar Ackerman. (Because the logon name, litwareinc\pilar, has been included as a parameter, the Windows PowerShell Credential Request dialog box only requires the administrator to enter the password for the Pilar Ackerman account.) The resulting credentials object is then stored in a variable named $cred1. The second command does the same thing, this time returning a credential object for the Ken Myer account.
  
With the two credential objects in hand, the third command in the example determines whether or not the two users can participate in an UCWA conference. To carry out this task, the **Test-CsUcwaConference** cmdlet is called, along with the following parameters: TargetFqdn (the FQDN of the Registrar pool); OrganizerSipAddress (the SIP address for the meeting organizer); OrganizerCredential (the Windows PowerShell object containing the credentials for this same user); ParticipantSipAddress (the SIP address for the other test user); and ParticipantCredential (the Windows PowerShell command-line interface object containing the credentials for the other user).
  
```
$cred1 = Get-Credential "litwareinc\pilar"
$cred2 = Get-Credential "litwareinc\kenmyer"

Test-CsUcwaConference -TargetFqdn atl-cs-001.litwareinc.com -OrganizerSipAddress "sip:pilar@litwareinc.com" -OrganizerCredential $cred1 -ParticipantSipAddress "sip:kenmyer@litwareinc.com" -ParticipantCredential $cred2

```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Test-CsUcwaConference** cmdlet verifies that a pair of test users can schedule, join, and then conduct an online conference using the Unified Communications Web API (UCWA). To do this, the cmdlet uses the Skype for Business Server 2015 web ticket service to authenticate the two test users and register them with Skype for Business Server 2015. The cmdlet then starts a conference using the organizer credentials and invites the participant to join the meeting. After the meeting has been joined, the **Test-CsUcwaConference** cmdlet verifies that the users can do such things as exchange instant message and conduct pools, then terminates the conference and unregisters the two test users. The scheduled conference will also be deleted when the test is finished.
  
The **Test-CsUcwaConference** cmdlet can also be used to determine whether or not anonymous users can join online conferences.
  
Note that the **Test-CsUcwaConference** cmdlet should not be run against a Skype for Business Server 2015 pool unless UCWA has been installed on that pool. If UCWA has not been installed then the call to the **Test-CsUcwaConference** cmdlet will fail.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Test-CsUcwaConference** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _OrganizerCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credential object for user account acting as the meeting organizer. The value passed to OrganizerCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\kenmyer and stores that object in a variable named $x: <br/> $x = Get-Credential "litwareinc\kenmyer"  <br/> You need to supply the user password when running this command.  <br/> The organizer credential is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _ParticipantCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credential object for the user account acting as the meeting participant. The value passed to ParticipantCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\pilar and stores that object in a variable named $y: <br/> $y = Get-Credential "litwareinc\pilar"  <br/> You need to supply the user password when running this command.  <br/> The participant credential is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _TargetFqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the pool to be tested.  <br/> |
| _Authentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+AuthenticationMechanism  <br/> |Type of authentication used when running the test. Allowed values are:  <br/> TrustedServer  <br/> Negotiate  <br/> ClientCertificate  <br/> LiveID  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _OrganizerSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address for the meeting organizer. For example: -OrganizerSipAddress "sip:pilar@litwareinc.com". The OrganizerSIPAddress parameter must reference the same user account as OrganizerCredential.  <br/> The SIP address is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/>  `-OutLoggerVariable TestOutput` <br/> Note: Do not prepend a $ character when specifying the variable name.  <br/> To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/>  `$TestOutput.ToHTML() > C:\Logs\TestOutput.html` <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/>  `$TestOutput.ToXML() > C:\Logs\TestOutput.xml` <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/>  `-OutVerboseVariable TestOutput` <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _ParticipantSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address for the meeting participant. For example: -ParticipantSipAddress "sip:kenmyer@litwareinc.com". The ParticipantSipAddress parameter must reference the same user account as ParticipantCredential.  <br/> The SIP address is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |System.Int32  <br/> |SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _HybridOnlineOrganizerCredential_ <br/> |Optional  <br/> |System.Management.Automation.PSCredential  <br/> |PARAMVALUE: PSCredential  <br/> |
| _HybridOnlineParticipantCredential_ <br/> |Optional  <br/> |System.Management.Automation.PSCredential  <br/> |PARAMVALUE: PSCredential  <br/> |
| _HybridOnlineUserAuthentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+HybridOnlineAuthenticationMechanism  <br/> |PARAMVALUE: LiveID | OAuth  <br/> |
| _IsHybridOnlineUser_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _IsPoolInMaintenanceMode_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _TelemetryTenantToken_ <br/> |Optional  <br/> |System.Security.SecureString  <br/> |PARAMVALUE: SecureString  <br/> |
| _TimeToWriteLogToConsole_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Test-CsUcwaConference** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Test-CsUcwaConference** cmdlet returns instances of the Microsoft.Rtc.SyntheticTransactions.WebTaskOutput object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Test-CsASConference](test-csasconference.md)
  
[Test-CsDataConference](test-csdataconference.md)
  
[Test-CsAVConference](test-csavconference.md)

