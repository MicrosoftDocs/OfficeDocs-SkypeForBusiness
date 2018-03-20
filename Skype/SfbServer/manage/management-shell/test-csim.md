---
title: "Test-CsIM"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 2fdab54c-5ec4-4db5-b29c-a3efaae68f66
description: "Tests the ability of two users to exchange instant messages. This cmdlet was introduced in Lync Server 2010."
---

# Test-CsIM
 
Tests the ability of two users to exchange instant messages. This cmdlet was introduced in Lync Server 2010.
  
```
Test-CsIM -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID | OAuth | OAuthInteractive>] [-ReceiverSipAddress <String>] [-RegistrarPort <Int32>] [-SenderSipAddress <String>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 checks to see if a pair of preconfigured test users can log on to the pool atl-cs-001.litwareinc.com and then exchange instant messages. This command will work only if test users have been defined for the pool atl-cs-001.litwareinc.com. If they have, then the command will determine whether the two users can log on to the system and, if so, can then exchange instant messages. I
  
If test users have not been defined, then the command will fail because it will not know which users to employ when doing the test. If you have not defined a Registrar for a pool, then you must include the SenderSipAddress and ReceiverSipAddress parameters, in addition to the corresponding credentials for the users involved in the IM session. The **Test-CsIM** cmdlet will then conduct its checks by using the two specified users.
  
```
Test-CsIm -TargetFqdn atl-cs-001.litwareinc.com
```

### EXAMPLE 2

The commands shown in Example 2 test the ability of a pair of users (litwareinc\pilar and litwareinc\kenmyer) to log on to Skype for Business Server 2015 and then exchange instant messages. To do this, the first command in the example uses the **Get-Credential** cmdlet to create a Windows PowerShell credential object containing the name and password of the user Pilar Ackerman. (Because the logon name, litwareinc\pilar, has been included as a parameter, the Windows PowerShell Credential Request dialog box will only require the administrator to enter the password for the Pilar Ackerman account.) The resulting credentials object is then stored in a variable named $cred1. The second command does the same thing, this time returning a credential object for the Ken Myer account.
  
With the two credential objects in hand, the third command in the example determines whether or not the two users can log on to Skype for Business Server 2015 and then exchange instant messages. To do this, the **Test-CsIM** cmdlet is called along with the following parameters: TargetFqdn (the FQDN of the Registrar pool); SenderSipAddress (the SIP address for the first test user); SenderCredential (the Windows PowerShell object containing the credentials for this user); -ReceiverSipAddress (the SIP address for the other test user); and ReceiverCredential (the Windows PowerShell object containing the credentials for the other user).
  
```
$cred1 = Get-Credential "litwareinc\pilar"
$cred2 = Get-Credential "litwareinc\kenmyer"

Test-CsIm -TargetFqdn atl-cs-001.litwareinc.com -SenderSipAddress "sip:pilar@litwareinc.com" -SenderCredential $cred1 -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -ReceiverCredential $cred2
```

## Detailed Description

The **Test-CsIM** cmdlet is an example of a Skype for Business Server 2015 "synthetic transaction." Synthetic transactions are used in Skype for Business Server 2015 to verify that users are able to successfully complete common tasks such as logging on to the system, exchanging instant messages, or making calls to a phone located on the public switched telephone network (PSTN). These tests can be conducted manually by an administrator, or they can be automatically run by an application such as Microsoft System Center Operations Manager (formerly Microsoft Operations Manager).
  
Synthetic transactions are typically conducted in two different ways. Many administrators will use the **CsHealthMonitoringConfiguration** cmdlets to set up test users for each of their Registrar pools. These test users are a pair of users who have been preconfigured for use with synthetic transactions. (Typically these are test accounts and not accounts that belong to actual users.) With test users configured for a pool, administrators can simply run a synthetic transaction against that pool without having to specify the identities of (and supply the credentials for) the user accounts involved in the test.
  
Alternatively, administrators can run a synthetic transaction using actual user accounts. For example, if two users are unable to exchange instant messages, an administrator can run a synthetic transaction using the two user accounts in question (as opposed to a pair of test accounts) to try to diagnose and resolve the problem. If you decide to conduct a synthetic transaction using actual user accounts you will need to supply credentials for each user.
  
The **Test-CsIM** cmdlet starts off by trying to log a pair of test users on to Skype for Business Server 2015. Assuming the two logons are successful, the cmdlet then initiates an instant messaging (IM) session between the two test users. (User 1 invites User 2 to an IM session, and User 2 accepts the invitation.) After verifying that messages can be exchanged between the two users, the **Test-CsIM** cmdlet then ends the IM session and logs both users off of the system.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ReceiverCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credential object for the first of the two user accounts to be tested. The value passed to ReceiverCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\pilar and stores that object in a variable named $y: <br/>  `$y = Get-Credential "litwareinc\pilar"` <br/> You need to supply the user password when running this command.  <br/> The receiver credential is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _SenderCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credential object for the second of the two user accounts to be tested. The value passed to SenderCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\kenmyer and stores that object in a variable named $x: <br/>  `$x = Get-Credential "litwareinc\kenmyer"` <br/> You need to supply the user password when running this command.  <br/> The sender credential is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _TargetFqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the pool to be tested.  <br/> |
| _Authentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+AuthenticationMechanism  <br/> |Type of authentication used in the test. Allowed values are:  <br/>  TrustedServer <br/> Negotiate  <br/> ClientCertificate  <br/> LiveID  <br/> |
| _EmailHost_ <br/> |Optional  <br/> |System.String  <br/> |Email host for user employed in the Legal Intercept test. For example:  <br/>  `-EmailHost "litwareinc.com"` <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _IsSsl_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, specifies that that test is being conducted using the Secure Socket Layer (SSL) protocol.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/>  `-OutLoggerVariable TestOutput` <br/> Note: Do not use prepend a $ character when specifying the variable name.To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/>  `$TestOutput.ToHTML() > C:\Logs\TestOutput.html` <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/>  `$TestOutput.ToXML() > C:\Logs\TestOutput.xml` <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/>  `-OutVerboseVariable TestOutput` <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _Password_ <br/> |Optional  <br/> |System.String  <br/> |Password for the employed in the Legal Intercept test.  <br/> |
| _Port_ <br/> |Optional  <br/> |System.UInt16  <br/> |Port used for the Legal Intercept service.  <br/> |
| _ReceiverSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address for the first of the two user accounts to be tested. For example:  `-ReceiverSipAddress "sip:jhaas@litwareinc.com"`. The ReceiverSipAddress parameter must reference the same user account as ReceiverCredential.  <br/> The SIP address is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |System.Int32  <br/> |SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.  <br/> |
| _SenderSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address for the second of the two user accounts to be tested. For example:  `-SenderSipAddress "sip:kenmyer@litwareinc.com"`. The SenderSipAddress parameter must reference the same user account as SenderCredential.  <br/> The SIP address is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _TestLegalIntercept_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When used, instructs Test-CsIM to test the Legal Intercept service for the specified user.  <br/> |
| _Username_ <br/> |Optional  <br/> |System.String  <br/> |User name for the user employed in the Legal Intercept test.  <br/> |
| _WaitSeconds_ <br/> |Optional  <br/> |System.Int16  <br/> |Specifies the amount of time (in seconds) that the system should wait for the Legal Intercept service to respond.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _HybridOnlineUserAuthentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+HybridOnlineAuthenticationMechanism  <br/> |PARAMVALUE: LiveID | OAuth  <br/> |
| _IsHybridOnlineUser_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _IsPoolInMaintenanceMode_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _TelemetryTenantToken_ <br/> |Optional  <br/> |System.Security.SecureString  <br/> |PARAMVALUE: SecureString  <br/> |
| _TimeToWriteLogToConsole_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
   
## Input Types

None. The **Test-CsIM** cmdlet does not accept pipelined input.
  
## Return Types

The **Test-CsIM** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.
  
## See also

#### 

[Test-CsGroupIM](test-csgroupim.md)

