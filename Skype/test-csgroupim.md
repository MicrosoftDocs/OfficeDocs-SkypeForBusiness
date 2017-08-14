---
title: Test-CsGroupIM
ms.prod: SKYPEFORBUSINESS
ms.assetid: 1e73fd7a-5727-4688-8d4c-a3107c3985e9
---


# Test-CsGroupIM
[]
Tests the ability of two users to conduct an instant messaging (IM) conference. The **Test-CsGroupIM** cmdlet is a "synthetic transaction": a simulation of common Skype for Business Server 2015 activities used for health and performance monitoring. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Test-CsGroupIM -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID | OAuth | OAuthInteractive>] [-ReceiverSipAddress <String>] [-RegistrarPort <Int32>] [-SenderSipAddress <String>] <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

Example 1 checks to see if a pair of preconfigured test users can log on to the pool atl-cs-001.litwareinc.com and participate in an IM conference. This command will work only if test users have been defined for the pool atl-cs-001.litwareinc.com. If they have, then the command will determine whether the two test users can log on to the system, and then check to see if these users can participate in an instant messaging conference. 
  
    
    
If test users have not been defined, then the command will fail because it will not know which users to employ when doing the test. If you have not defined test users for a pool, then you must include the SenderSipAddress and ReceiverSipAddress parameters and the corresponding credentials for the users involved in the instant messaging session. The **Test-CsGroupIM** cmdlet will then conduct its checks using the two specified users.
  
    
    



```

Test-CsGroupIm -TargetFqdn atl-cs-001.litwareinc.com
```


### EXAMPLE 2

The commands shown in Example 2 test the ability of a pair of users (litwareinc\\pilar and litwareinc\\kenmyer) to log on to Skype for Business Server 2015, and then participate in an instant messaging conference. To do this, the first command in the example uses the **Get-Credential** cmdlet to create a Windows PowerShell credential object containing the name and password of the user Pilar Ackerman. (Because the logon name, litwareinc\\pilar, has been included as a parameter, the resulting Windows PowerShell Credential Request dialog box only requires the administrator to enter the password for the Pilar Ackerman account.) The resulting credentials object is then stored in a variable named $cred1. The second command does the same thing, this time returning a credential object for the Ken Myer account.
  
    
    
With the two credential objects in hand, the third command in the example determines whether or not the two users can log on to Skype for Business Server 2015 and then participate in an instant messaging conference. To carry out this task, the **Test-CsGroupIM** cmdlet is called, along with the following parameters: TargetFqdn (the FQDN of the Registrar pool); SenderSipAddress (the SIP address the first user); SenderCredential (the user credentials for the first user); ReceiverSipAddress (the SIP address for the second user); and ReceiverCredential (user credentials for the second user).
  
    
    



```
$cred1 = Get-Credential "litwareinc\\pilar"
$cred2 = Get-Credential "litwareinc\\kenmyer"

Test-CsGroupIm -TargetFqdn atl-cs-001.litwareinc.com -SenderSipAddress "sip:pilar@litwareinc.com" -SenderCredential $cred1 -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -ReceiverCredential $cred2
```


## Detailed Description

The **Test-CsGroupIM** cmdlet is an example of a Skype for Business Server 2015 synthetic transaction. Synthetic transactions are used in Skype for Business Server 2015 to verify that users are able to successfully complete common tasks such as logging on to the system, exchanging instant messages, or making calls to a phone located on the public switched telephone network (PSTN). These tests can be conducted manually by an administrator, or they can be automatically run by an application such as Microsoft System Center Operations Manager (formerly Microsoft Operations Manager).
  
    
    
Synthetic transactions are typically conducted in two different ways. Many administrators will use the **CsHealthMonitoringConfiguration** cmdlets to set up test users for each of their Registrar pools. These test users are a pair of users who have been preconfigured for use with synthetic transactions. (Typically these are test accounts and not accounts that belong to actual users.) With test users configured for a pool, administrators can simply run a synthetic transaction against that pool without having to specify the identities of (and supply the credentials for) the user accounts involved in the test.
  
    
    
Alternatively, administrators can run a synthetic transaction using actual user accounts. For example, if two users are unable to exchange instant messages, an administrator could run a synthetic transaction using the two user accounts in question (as opposed to a pair of test accounts), and then try to diagnose and resolve the problem. If you decide to conduct a synthetic transaction using actual user accounts, you will need to supply credentials for each user.
  
    
    
The **Test-CsGroupIM** cmdlet enables you to verify that users in your organization can conduct conferences. The **Test-CsGroupIM** cmdlet requires two user accounts in order to conduct its tests. If you have set up test users for the pool where the test is to be conducted, then you do not need to specify these accounts; instead, the **Test-CsGroupIM** cmdlet will automatically use the test accounts assigned to pool. (For details, see the [New-CsHealthMonitoringConfiguration](new-cshealthmonitoringconfiguration.md) cmdlet help topic.) Alternatively, you can conduct the test using accounts other than the ones assigned to the Registrar. This allows you run tests even if you have not configured test users for the pool. It also allows you to test the ability of two specific users to conduct a conference. If you choose to use this approach, you will need to provide the user name and password for both users.
  
    
    
When you run the **Test-CsGroupIM** cmdlet, the cmdlet attempts to sign both test users on to Skype for Business Server 2015. If successful, the **Test-CsGroupIM** cmdlet creates a new conference using the first test user, then invites the second user to join the conference. After an exchange of messages, both users are then disconnected from the system. All of this happens without any user interaction, and without affecting any actual users. For example, suppose the test account sip:kenmyer@litwareinc.com corresponds to a real user with a real Skype for Business Server 2015 account. In that case, the test will be conducted without any disruption to the real Ken Myer. For example, even when the Ken Myer test account logs off from the system, Ken Myer the person will remain logged on. Likewise, the real Ken Myer will not receive an invitation to join the conference. That invitation will be sent to, and accepted by, the test account.
  
    
    
Adding the Verbose parameter enables you to get a detailed account of all the actions taken by the **Test-CsGroupIM** cmdlet in order to complete its test.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ReceiverCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credential object for the first of the two user accounts to be tested. The value passed to ReceiverCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\\pilar and stores that object in a variable named $y: <br/>  `$y = Get-Credential "litwareinc\\pilar"` <br/> You need to supply the user password when running this command.  <br/> The receiver credential is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _SenderCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credential object for the second of the two user accounts to be tested. The value passed to SenderCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\\kenmyer and stores that object in a variable named $x: <br/>  `$x = Get-Credential "litwareinc\\kenmyer"` <br/> You need to supply the user password when running this command.  <br/> The sender credential is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _TargetFqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the pool to be tested.  <br/> |
| _Authentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+AuthenticationMechanism  <br/> |Type of authentication used in the test. Allowed values are:  <br/> * TrustedServer  <br/> * Negotiate  <br/> * ClientCertificate  <br/> * LiveID  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/>  `-OutLoggerVariable TestOutput` <br/> Note: Do not use prepend a $ character when specifying the variable name.To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/>  `$TestOutput.ToHTML() > C:\\Logs\\TestOutput.html` <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/>  `$TestOutput.ToXML() > C:\\Logs\\TestOutput.xml` <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/>  `-OutVerboseVariable TestOutput` <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _ReceiverSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address for the first of the two user accounts to be tested. For example:  `-ReceiverSipAddress "sip:pilar@litwareinc.com"`. The ReceiverSipAddress parameter must reference the same user account as ReceiverCredential.  <br/> The SIP address is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |System.Int32  <br/> |SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.  <br/> |
| _SenderSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address for the second of the two user accounts to be tested. For example:  `-SenderSipAddres "sip:kenmyer@litwareinc.com"`. The SenderSipAddress parameter must reference the same user account as SenderCredential.  <br/> The SIP address is not required if you are running the test under the health monitoring configuration settings for the pool.  <br/> |
| _TestJoinLauncher_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, tests the ability of the Join Launcher to participate in an AV conference. The Join Launcher is used to help users of mobile devices (and, as a result, users of the Mobility Service) take part in conferences.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _HybridOnlineUserAuthentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+HybridOnlineAuthenticationMechanism  <br/> |PARAMVALUE: LiveID | OAuth  <br/> |
| _IsHybridOnlineUser_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _IsPoolInMaintenanceMode_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _TelemetryTenantToken_ <br/> |Optional  <br/> |System.Security.SecureString  <br/> |PARAMVALUE: SecureString  <br/> |
| _TimeToWriteLogToConsole_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
   

## Input Types

None. The **Test-CsGroupIM** cmdlet does not accept pipelined input.
  
    
    

## Return Types

The **Test-CsGroupIM** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.
  
    
    

## See also


#### 


  
    
    
 [Test-CsIM](test-csim.md)
