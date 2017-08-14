---
title: Test-CsWebApp
ms.prod: SKYPEFORBUSINESS
ms.assetid: 0333a4a5-9bd5-4a45-aea8-e7af1a394ec3
---


# Test-CsWebApp
[]
Verifies that authenticated users can use Skype for Business Web App to join a Skype for Business Server 2015 conference. This cmdlet was introduced in Lync Server 2010.
  
    
    

This cmdlet has been deprecated for use with the on-premises version of Skype for Business Server 2015. Instead, administrators should use the  [Test-CsUcwaConference](test-csucwaconference.md) cmdlet to perform these tests.
```

Test-CsWebApp -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID | OAuth | OAuthInteractive>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

Example 1 verifies whether or not a pair of test users configured for the pool atl-cs-001.litwareinc.com can use Skype for Business Web App to join a conference. This command will only succeed if you have configured test users for the pool by using the **CsHealthMonitoringConfiguration** cmdlets.
  
    
    

```

Test-CsWebApp -TargetFqdn atl-cs-001.litwareinc.com

```


### EXAMPLE 2

The commands shown in Example 2 verify whether or not the users Ken Myer and Pilar Ackerman can use Skype for Business Web App to join a conference. To use actual user accounts, the first two commands in the example use the Get-Credential cmdlet to create a Windows PowerShell command-line interface credentials objects for the two users (litwareinc\\kenmyer and litwareinc\\pilar). Those credentials objects (stored in the variables $cred1 and $cred2) are then used as parameter values for the UserCredential and User2Credential parameters in the final command in the example. In addition to the user credential parameters, the UserSipAddress and User2SipAddress parameters are included, along with the SIP addresses of the two user accounts being employed in the test.
  
    
    

```

$cred1 = Get-Credential "litwareinc\\kenmyer"
$cred2 = Get-Credential "litwareinc\\pilar"

Test-CsWebApp -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $cred1 -User2SipAddress "sip:pilar@litwareinc.com" -User2Credential $cred2

```


## Detailed Description

The **Test-CsWebApp** cmdlet enables administrators to verify that authenticated users can employ Skype for Business Web App in order to join conferences. When you run the **Test-CsWebApp** cmdlet, the cmdlet attempts to obtain web tickets for a pair of test users by using the Web Ticket service. If the tickets can be obtained, and the test users authenticated, the **Test-CsWebApp** cmdlet will then try to connect to Skype for Business Server 2015 by using Skype for Business Web App. If the connection is made, the cmdlet will then attempt to establish separate conferences for instant messaging, application sharing, and data collaboration.
  
    
    
Many administrators will use the **CsHealthMonitoringConfiguration** cmdlets to set up test users for each of their Registrar pools. These test users represent a pair of user accounts that have been preconfigured for use with synthetic transactions. (Typically these are test accounts and not accounts that belong to actual users.) If test users are configured for a pool, administrators can run the **Test-CsWebApp** cmdlet against that pool without having to specify the identity of (and supply the credentials for) the user account involved in the test.
  
    
    
Alternatively, administrators can run the **Test-CsWebApp** cmdlet using actual user accounts. If you decide to conduct the test using actual user accounts you will need to supply the logon name and password for each account.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _TargetFqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the pool to be tested. For example:  <br/>  `-TargetFqdn atl-cs-001.litwareinc.com` <br/> |
| _TargetUri_ <br/> |Required  <br/> |System.String  <br/> |Uniform Resource Identifier (URI) of the Reach server. For example:  <br/>  `-TargetUri "https://atl-cs-001.litwareinc.com/reach"` <br/> You cannot use both the TargetUri parameter and the TargetFqdn parameter in the same command.  <br/> |
| _User2Credential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credential object for the second of the two user accounts to be tested. The value passed to User2Credential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\\kenmyer and stores that object in a variable named $y: <br/>  `$y = Get-Credential "litwareinc\\kenmyer"` <br/> You need to supply the user password when running this command.  <br/> |
| _User2SipAddress_ <br/> |Required  <br/> |System.String  <br/> |SIP address for the second of the two user accounts to be tested. For example:  <br/>  `-User2SipAddress "sip:pilar@litwareinc.com"` <br/> This parameter is not required if you are running the test by using test users configured via the **CsHealthMonitoringConfiguration** cmdlets. <br/> |
| _UserCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credentials object for the first of the two user accounts to be tested. The value passed to UserCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\\pilar and stores that object in a variable named $x: <br/>  `$x = Get-Credential "litwareinc\\pilar"` <br/> You need to supply the user password when running this command.  <br/> |
| _Authentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+AuthenticationMechanism  <br/> |Type of authentication used when running the test. Allowed values are:  <br/> TrustedServer  <br/> Negotiate  <br/> ClientCertificate  <br/> LiveID  <br/> |
| _External_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, causes the **Test-CsWebApp** cmdlet to test the Reach server's external web relay. If this parameter is not present, the cmdlet will test the internal web relay. The web relay serves as an intermediary between the internal network and the Internet. <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/>  `-OutLoggerVariable TestOutput` <br/> Note: Do not prepend a $ character when specifying the variable name.  <br/> To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/>  `$TestOutput.ToHTML() > C:\\Logs\\TestOutput.html` <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/>  `$TestOutput.ToXML() > C:\\Logs\\TestOutput.xml` <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/>  `-OutVerboseVariable TestOutput` <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |System.Int32  <br/> |SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.  <br/> |
| _UserSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address for the first of the two user accounts to be tested. For example:  <br/>  `-UserSipAddress "sip:kenmyer@litwareinc.com"` <br/> This parameter is not required if you are running the test by using test users configured via the CsHealthMonitoringConfiguration cmdlets.  <br/> |
| _WebCredential_ <br/> |Optional  <br/> |System.Management.Automation.PSCredential  <br/> |User credential object for the user account to be used in the test. The value passed to UserCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\\kenmyer and stores that object in a variable named $x: <br/>  `$x = Get-Credential "litwareinc\\kenmyer"` <br/> This parameter is required if either the TargetUri parameter or the UserSipAddress/User2SipAddress parameters are specified and the computer on which the command is run does not have a server certificate.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _HybridOnlineUserAuthentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+HybridOnlineAuthenticationMechanism  <br/> |PARAMVALUE: LiveID | OAuth  <br/> |
| _IsHybridOnlineUser_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _IsPoolInMaintenanceMode_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _TelemetryTenantToken_ <br/> |Optional  <br/> |System.Security.SecureString  <br/> |PARAMVALUE: SecureString  <br/> |
| _TimeToWriteLogToConsole_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
   

## Input Types

None.
  
    
    

## Return Types

The **Test-CsWebApp** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.
  
    
    

