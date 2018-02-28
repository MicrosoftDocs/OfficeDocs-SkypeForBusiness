---
title: "Test-CsRegistration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9e38cb36-c97a-43f2-97fe-64759f663be2
description: "Tests the ability of a user to log on to Skype for Business Server 2015. The Test-CsRegistration cmdlet is asynthetic transaction: a simulation of common Skype for Business Server 2015 activities used for health and performance monitoring. This cmdlet was introduced in Lync Server 2010."
---

# Test-CsRegistration
[]
Tests the ability of a user to log on to Skype for Business Server 2015. The **Test-CsRegistration** cmdlet is a "synthetic transaction": a simulation of common Skype for Business Server 2015 activities used for health and performance monitoring. This cmdlet was introduced in Lync Server 2010.
  
```
Test-CsRegistration -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID | OAuth | OAuthInteractive>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 tests the Registrar service for the pool atl-cs-001.litwareinc.com. This command will work only if test users have been defined for the pool atl-cs-001.litwareinc.com. If they have, then the command will determine whether or not the first test user is able to log on to Skype for Business Server 2015. 
  
If test users have not been defined, then the command will fail because it will not know which user to log on as. If you have not defined test users for a pool, then you must include the UserSipAddress parameter and the credentials of the user that the command should use when trying to log on.
  
```
Test-CsRegistration -TargetFqdn atl-cs-001.litwareinc.com 
```

### EXAMPLE 2

The commands shown in Example 2 test the ability of a specific user (litwareinc\pilar) to log on to Skype for Business Server 2015. To do this, the first command in the example uses the **Get-Credential** cmdlet to create a Windows PowerShell credential object containing the name and password of the user Pilar Ackerman. (Because the logon name litwareinc\pilar has been included as a parameter, the Windows PowerShell Credential Request dialog box only requires the administrator to enter the password for the Pilar Ackerman account.) The resulting credentials object is then stored in a variable named $cred1.
  
The second command then checks to see if this user can log on to the pool atl-cs-001.litwareinc.com. To carry out this task, the **Test-CsRegistration** cmdlet is called, along with three parameters: TargetFqdn (the FQDN of the Registrar pool); UserCredential (the Windows PowerShell object containing Pilar Ackerman's user credentials); and UserSipAddress (the SIP address corresponding to the supplied user credentials).
  
```
$cred1 = Get-Credential "litwareinc\pilar"

Test-CsRegistration -TargetFqdn atl-cs-001.litwareinc.com -UserCredential $cred1 -UserSipAddress "sip:pilar@litwareinc.com"
```

## Detailed Description

The **Test-CsRegistration** cmdlet is an example of a Skype for Business Server 2015 "synthetic transaction." Synthetic transactions are used in Skype for Business Server 2015 to verify that users are able to successfully complete common tasks such as logging on to the system, exchanging instant messages, or making calls to a phone located on the public switched telephone network (PSTN). These tests can be conducted manually by an administrator, or they can be automatically run by an application such as Microsoft System Center Operations Manager (formerly Microsoft Operations Manager).
  
Synthetic transactions are typically conducted in two different ways. Many administrators will use the CsHealthMonitoringConfiguration cmdlets to set up test users for each of their Registrar pools. These test users are a pair of users who have been preconfigured for use with synthetic transactions. (Typically these are test accounts and not accounts that belong to actual users.) With test users configured for a pool, administrators can simply run a synthetic transaction against that pool without having to specify the identities of (and supply the credentials for) the user accounts involved in the test.
  
Alternatively, administrators can run a synthetic transaction using actual user accounts. For example, if two users are unable to exchange instant messages, an administrator could run a synthetic transaction using the two user accounts in question (as opposed to a pair of test accounts) and try to diagnose and resolve the problem. If you decide to conduct a synthetic transaction using actual user accounts you will need to supply the logon names and passwords for each user.
  
The **Test-CsRegistration** cmdlet enables you to verify that users in your organization can log on to Skype for Business Server 2015. In order to perform this check, the **Test-CsRegistration** cmdlet requires a single test account. If you have set up test users for the pool where the test is to be conducted, then you do not need to specify an account; instead, the **Test-CsRegistration** cmdlet will automatically use the first test account that was assigned to the pool. (For details, see the[New-CsHealthMonitoringConfiguration](new-cshealthmonitoringconfiguration.md) cmdlet help topic.) Alternatively, you can conduct the test using an account that has not been assigned to the pool. This allows you run tests even if you have not configured test users. It also allows you to test the ability of a specific user to log on to Skype for Business Server 2015. (If you choose to use this approach, you will need to provide the user name and password for the account being tested.)
  
When you run the **Test-CsRegistration** cmdlet, the cmdlet attempts to sign the test user on to Skype for Business Server 2015 and then, if successful, disconnects that test user from the system. All of this happens without any user interaction, and without affecting any actual users. For example, suppose the test account sip:kenmyer@litwareinc.com corresponds to a real user with a real Skype for Business Server 2015 account. In that case, the test will be conducted without any disruption to the real Ken Myer. When the Ken Myer test account logs off from the system, Ken Myer the person will remain logged on.
  
Adding the Verbose parameter enables you to get a detailed account of all the actions taken by the **Test-CsRegistration** cmdlet in order to complete its test.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _TargetFqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the pool to be tested.  <br/> |
| _UserCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credentials object for the account to be tested. The value passed to UserCredential must be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credential object for the user litwareinc\kenmyer and stores that object in a variable named <br/> $x: $x = Get-Credential "litwareinc\kenmyer"  <br/> You need to supply the user password when running this command. This parameter is not required if you are conducting the test under the health monitoring configuration settings for the pool.  <br/> |
| _Authentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+AuthenticationMechanism  <br/> |Type of authentication used in the test. Allowed values are:  <br/>  TrustedServer <br/> Negotiate  <br/> ClientCertificate  <br/> LiveID  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/>  `-OutLoggerVariable TestOutput` <br/> Note: Do not use prepend a $ character when specifying the variable name.To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/>  `$TestOutput.ToHTML() > C:\Logs\TestOutput.html` <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/>  `$TestOutput.ToXML() > C:\Logs\TestOutput.xml` <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/>  `-OutVerboseVariable TestOutput` <br/> Do not use prepend a $ character when specifying the variable name.  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |System.Int32  <br/> |SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.  <br/> |
| _UserSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address for user account to be tested; for example:  <br/>  `-UserSipAddress "sip:kenmyer@litwareinc.com"` <br/> The UserSipAddress parameter must reference the same user account as UserCredential. This parameter is not required if you are conducting the test under the health monitoring configuration settings for the pool.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _HybridOnlineUserAuthentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+HybridOnlineAuthenticationMechanism  <br/> |PARAMVALUE: LiveID | OAuth  <br/> |
| _HybridOnlineUserCredential_ <br/> |Optional  <br/> |System.Management.Automation.PSCredential  <br/> |PARAMVALUE: PSCredential  <br/> |
| _IsHybridOnlineUser_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _IsPoolInMaintenanceMode_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _TelemetryTenantToken_ <br/> |Optional  <br/> |System.Security.SecureString  <br/> |PARAMVALUE: SecureString  <br/> |
| _TimeToWriteLogToConsole_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
   
## Input Types

None. The **Test-CsRegistration** cmdlet does not accept pipelined input.
  
## Return Types

The **Test-CsRegistration** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.
  

