---
title: "Test-CsPresence"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 09a5faf6-4e80-4a3b-ac84-aec9778ee9b5
description: "Tests the ability of a user to log on to Skype for Business Server 2015, publish his or her presence information, and then subscribe to the presence information published by a second user. This cmdlet was introduced in Lync Server 2010."
---

# Test-CsPresence
[]
Tests the ability of a user to log on to Skype for Business Server 2015, publish his or her presence information, and then subscribe to the presence information published by a second user. This cmdlet was introduced in Lync Server 2010.
  
```
Test-CsPresence -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID | OAuth | OAuthInteractive>] [-PublisherSipAddress <String>] [-RegistrarPort <Int32>] [-SubscriberSipAddress <String>] [-TimeoutInSeconds <UInt32>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 checks to see if a pair of preconfigured test users can log on to the pool atl-cs-001.litwareinc.com; after the test users are logged on, the **Test-CsPresence** cmdlet then checks to see if the two users are able to exchange presence information. This command will work only if test users have been defined for the pool atl-cs-001.litwareinc.com. If they have, then the command will determine whether the first test user can log on to the system and then check to see if this user can exchange presence information with the second test user defined for the pool.
  
If a Registrar has not been defined then the command will fail because it will not know which users to employ when doing the test. If you have not defined test users for a pool, then you must include the SubscriberSipAddress and PublisherSipAddress parameters in addition to the corresponding credentials for the users acting as the presence subscriber and the presence publisher. The **Test-CsPresence** cmdlet will then conduct its checks using the two specified users.
  
```
Test-CsPresence -TargetFqdn atl-cs-001.litwareinc.com 
```

### EXAMPLE 2

The commands shown in Example 2 test the ability of a pair of users (litwareinc\pilar and litwareinc\kenmyer) to log on to Skype for Business Server 2015, and then exchange presence information. To do this, the first command in the example uses the **Get-Credential** cmdlet to create a Windows PowerShell credential object containing the name and password of the user Pilar Ackerman. (Because the logon name litwareinc\pilar has been included as a parameter, the Windows PowerShell Credential Request dialog box will only require the administrator to enter the password for the Pilar Ackerman account.) The resulting credentials object is then stored in a variable named $cred1. The second command does the same thing, this time returning a credential object for the Ken Myer account.
  
With the two credential objects in hand, the third command in the example determines whether or not the two users can log on to Skype for Business Server 2015 and exchange presence information. To carry out this task, the **Test-CsPresence** cmdlet is called, along with the following parameters: TargetFqdn (the FQDN of the Registrar pool); SubscriberSipAddress (the SIP address for one test user); SubscriberCredential (the Windows PowerShell object containing the credentials for this same user); PublisherSipAddress (the SIP address for the other test user); and PublisherCredential (the Windows PowerShell object containing the credentials for the other user).
  
```
$cred1 = Get-Credential "litwareinc\pilar"
$cred2 = Get-Credential "litwareinc\kenmyer"

Test-CsPresence -TargetFqdn atl-cs-001.litwareinc.com -SubscriberSipAddress "sip:pilar@litwareinc.com" -SubscriberCredential $cred1 -PublisherSipAddress "sip:kenmyer@litwareinc.com" -PublisherCredential $cred2
```

## Detailed Description

The **Test-CsPresence** cmdlet is an example of a Skype for Business Server 2015 synthetic transaction. Synthetic transactions are used in Skype for Business Server 2015 to verify that users are able to successfully complete common tasks such as logging on to the system, exchanging instant messages, or making calls to a phone located on the public switched telephone network (PSTN). These tests can be conducted manually by an administrator, or they can be automatically run by an application such as Microsoft System Center Operations Manager (formerly Microsoft Operations Manager).
  
Synthetic transactions are typically conducted in two different ways. Many administrators will use the **CsHealthMonitoringConfiguration** cmdlets to set up test users for each of their Registrar pools. Typically, these are test accounts and not accounts belonging to actual users. With these user accounts configured for a pool, administrators can simply run a synthetic transaction against that pool without having to specify the identities of (and supply the credentials for) the user accounts involved in the test.
  
Alternatively, administrators can run a synthetic transaction using actual user accounts. For example, if two users are unable to exchange instant messages, an administrator can run a synthetic transaction using the two user accounts in question (as opposed to a pair of test accounts) and try to diagnose and resolve the problem. If you decide to conduct a synthetic transaction using actual user accounts, you will need to supply the logon names and passwords for each user.
  
The **Test-CsPresence** cmdlet is used to determine whether a pair of test users can log on to Skype for Business Server 2015 and then exchange presence information. To do this, the cmdlet first logs the two users on to the system. If both logons succeed, the first test user then asks to receive presence information from the second user. The second user publishes this information, and the **Test-CsPresence** cmdlet verifies that the information was successfully transmitted to the first user. After the exchange of presence information, the two test users are then logged off from Skype for Business Server 2015.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _PublisherCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credential object for the first of the two user accounts to be tested. The value passed to PublisherCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\kenmyer and stores that object in a variable named $x: <br/>  `$x = Get-Credential "litwareinc\kenmyer"` <br/> You need to supply the user password when running this command.  <br/> The publisher credential is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _SubscriberCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credential object for the second of the two user accounts to be tested. The value passed to SubscriberCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\pilar and stores that object in a variable named $y: <br/>  `$y = Get-Credential "litwareinc\pilar"` <br/> You need to supply the user password when running this command.  <br/> The subscriber credential is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _TargetFqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the pool to be tested.  <br/> |
| _Authentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+AuthenticationMechanism  <br/> |Type of authentication used in the test. Allowed values are:  <br/> \* TrustedServer  <br/> \* Negotiate  <br/> \* ClientCertificate  <br/> \* LiveID  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/>  `-OutLoggerVariable TestOutput` <br/> Note: Do not use prepend a $ character when specifying the variable name.To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/>  `$TestOutput.ToHTML() > C:\Logs\TestOutput.html` <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/>  `$TestOutput.ToXML() > C:\Logs\TestOutput.xml` <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/>  `-OutVerboseVariable TestOutput` <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _PublisherSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address for the first of the two user accounts to be tested. For example:  <br/>  `-PublisherSipAddress "sip:kenmyer@litwareinc.com"` <br/> The PublisherSipAddress parameter must reference the same user account as PublisherCredential.  <br/> The SIP address is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |System.Int32  <br/> |SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.  <br/> |
| _SubscriberSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address for the second of the two user accounts to be tested. For example:  <br/>  `-SubscriberSipAddress "sip:pilar@litwareinc.com"` <br/> The SubscriberSipAddress parameter must reference the same user account as SubscriberCredential.  <br/> The SIP address is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _TimeoutInSeconds_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _HybridOnlineUserAuthentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+HybridOnlineAuthenticationMechanism  <br/> |PARAMVALUE: LiveID | OAuth  <br/> |
| _IsHybridOnlineUser_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _IsPoolInMaintenanceMode_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _TelemetryTenantToken_ <br/> |Optional  <br/> |System.Security.SecureString  <br/> |PARAMVALUE: SecureString  <br/> |
| _TimeToWriteLogToConsole_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
   
## Input Types

None. The **Test-CsPresence** cmdlet does not accept pipelined input.
  
## Return Types

The **Test-CsPresence** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.
  
## See also

#### 

[Test-CsRegistration](test-csregistration.md)

