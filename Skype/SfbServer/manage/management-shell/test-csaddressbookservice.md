---
title: "Test-CsAddressBookService"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 8398c9ea-eaab-4a4d-9e09-473ea2b27e22
description: "Tests the ability of a user to access the server that hosts the Address Book Download Web service. This cmdlet was introduced in Lync Server 2010."
---

# Test-CsAddressBookService
 
Tests the ability of a user to access the server that hosts the Address Book Download Web service. This cmdlet was introduced in Lync Server 2010.
  
```
Test-CsAddressBookService -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID | OAuth | OAuthInteractive>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 tests the Address Book Download Web service for the pool atl-cs-001.litwareinc.com. This command tests the Address Book Download Web service by using test users preconfigured for the pool atl-cs-001.litwareinc.com.
  
```
Test-CsAddressBookService -TargetFqdn atl-cs-001.litwareinc.com 
```

### EXAMPLE 2

The commands shown in Example 2 also test the availability of the server that runs the Address Book Download Web service; in this case, however, the commands are running under the credentials for the user Ken Myer (litwareinc\kenmyer). To do this, the first command uses the **Get-Credential** cmdlet to create a Windows PowerShell credential object containing the name and password of the user Ken Myer. (Because the logon name -- litwareinc\kenmyer -- has been included as a parameter, the Windows PowerShell Credential Request dialog box only requires the administrator to enter the password for the Ken Myer account.) The resulting credential object is then stored in a variable named $cred1.
  
In the second command, the **Test-CsAddressBookService** cmdlet is used to test the Address Book Download Web service for the pool atl-cs-001.litwareinc.com. To run this command under Ken Myer's user credentials, the UserCredential parameter is included, along with the parameter value $cred1. In addition, Ken's SIP address must be supplied using the UserSipAddress parameter.
  
```
$cred1 = Get-Credential "litwareinc\kenmyer"

Test-CsAddressBookService -TargetFqdn atl-cs-001.litwareinc.com -UserCredential $cred1 -UserSipAddress "sip:kenmyer@litwareinc.com"
```

### EXAMPLE 3

Example 3 shows how you can test the Address Book Download Web service for atl-cs-001.litwareinc.com. To do this, the **Test-CsAddressBookService** cmdlet is called along with two parameters: TargetUri, which specifies the URI of the Address Book Download Web service; and UserSipAddress, which contains the Windows PowerShell SIP address for the user account being used in the test.
  
```

Test-CsAddressBookService -TargetUri https://atl-cs-001.litwareinc.com/abs/handler -UserSipAddress "sip:kenmyer@litwareinc.com"
```

## Detailed Description

The **Test-CsAddressBookService** cmdlet is an example of a "synthetic transaction." Synthetic transactions are used in Skype for Business Server 2015 to verify that users are able to successfully complete common tasks such as logging on to the system, exchanging instant messages, or making calls to a phone located on the public switched telephone network (PSTN). These tests can be conducted manually by an administrator, or they can be automatically run by an application such as Microsoft System Center Operations Manager (formerly Microsoft Operations Manager).
  
Synthetic transactions are typically conducted in two different ways. Many administrators will use the **CsHealthMonitoringConfiguration** cmdlets to set up test users for each of their Registrar pools. These test users are a pair of users who have been preconfigured for use with synthetic transactions. (Typically these are test accounts and not accounts that belong to actual users.) With test users configured for a pool, administrators can run a synthetic transaction against that pool without having to specify the identities of (and supply the credentials for) the user accounts involved in the test.
  
Alternatively, administrators can run a synthetic transaction by using actual user accounts. For example, if two users are unable to exchange instant messages, an administrator could run a synthetic transaction using those two user accounts (as opposed to a pair of test accounts), and then try to diagnose and resolve the problem. If you decide to conduct a synthetic transaction using actual user accounts, you will need to supply the logon names and passwords for each user.
  
The **Test-CsAddressBookService** cmdlet provides a way for you to verify that a user can connect to the Address Book Download Web service. When run, the **Test-CsAddressBookService** cmdlet connects to the Address Book Download Web service on the specified pool and requests the location of the Address Book files. If the Address Book Download Web service supplies that location, the test is considered successful. If the request is denied, then the test is considered a failure.
  
You can test the Address Book Download Web service in two different ways: by testing the service itself or by testing the associated Web service.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _TargetFqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the Registrar pool where the Address Book Download Web service is to be tested. For example:  `-TargetFqdn "atl-cs-001.litwareinc.com"`.  <br/> You cannot use both the TargetUri parameter and the TargetFqdn parameter in the same command.  <br/> |
| _TargetUri_ <br/> |Required  <br/> |System.String  <br/> |Uniform Resource Identifier (URI) of the Address Book Web Query service. For example:  `-TargetUri "https://atl-cs-001.litwareinc.com/abs/handler"`.  <br/> You cannot use both the TargetUri parameter and the TargetFqdn parameter in the same command.  <br/> |
| _UserCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credential object for the user account to be used in the test. The value passed to UserCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\kenmyer and stores that object in a variable named $x: <br/>  `$x = Get-Credential "litwareinc\kenmyer"` <br/> You need to supply the user password when running this command.  <br/> |
| _Authentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+AuthenticationMechanism  <br/> |Type of authentication used in the test. Allowed values are:  <br/> \* TrustedServer  <br/> \* Negotiate  <br/> \* ClientCertificate  <br/> \* LiveID  <br/> |
| _External_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to verify that external users can use the Address Book Download Web service.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/>  `-OutLoggerVariable TestOutput` <br/> Note: Do not use prepend a $ character when specifying the variable name.To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/>  `$TestOutput.ToHTML() > C:\Logs\TestOutput.html` <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/>  `$TestOutput.ToXML() > C:\Logs\TestOutput.xml` <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/>  `-OutVerboseVariable TestOutput` <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |System.Int32  <br/> |SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.  <br/> |
| _UserSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address of the user to be used in the test. If this parameter is not specified then **Test-CsAddressBookService** will conduct its checks by using the account of the logged-in user. <br/> |
| _WebCredential_ <br/> |Optional  <br/> |System.Management.Automation.PSCredential  <br/> |An object containing user credentials for accessing the Location Information service. This object can be retrieved by calling the **Get-Credential** cmdlet and supplying the appropriate credentials. <br/> This parameter is required if the TargetUri and UserSipAddress parameters are specified, and the computer on which the command is run does not have a server certificate.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _HybridOnlineUserAuthentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+HybridOnlineAuthenticationMechanism  <br/> |PARAMVALUE: LiveID | OAuth  <br/> |
| _IsHybridOnlineUser_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _IsPoolInMaintenanceMode_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _TelemetryTenantToken_ <br/> |Optional  <br/> |System.Security.SecureString  <br/> |PARAMVALUE: SecureString  <br/> |
| _TimeToWriteLogToConsole_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
   
## Input Types

None. The **Test-CsAddressBookService** cmdlet does not accept pipelined input.
  
## Return Types

The **Test-CsAddressBookService** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.
  
## See also

#### 

[Test-CsAddressBookWebQuery](test-csaddressbookwebquery.md)
  
[Update-CsAddressBook](update-csaddressbook.md)

