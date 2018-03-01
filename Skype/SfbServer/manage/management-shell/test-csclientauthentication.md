---
title: "Test-CsClientAuthentication"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6a25b2c6-0cb2-473c-af92-0be5cead8a19
description: "Determines whether or not a user can log on to Skype for Business Server 2015 by using a certificate downloaded from the certificate provisioning service. This cmdlet was introduced in Lync Server 2013."
---

# Test-CsClientAuthentication
 
Determines whether or not a user can log on to Skype for Business Server 2015 by using a certificate downloaded from the certificate provisioning service. This cmdlet was introduced in Lync Server 2013.
  
```
Test-CsClientAuthentication -UserCredential <PSCredential> -UserSipAddress <String> [-Force <SwitchParameter>] [-LiveIdAuthentication <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] [-TargetUri <String>]

```

## Examples

### EXAMPLE 1

The commands shown in Example 1 test the ability of the user litwareinc\kenmyer to log on to the Registrar pool atl-cs-001.litwareinc.com by using a client certificate. To carry out this task, the first command in the example uses the **Get-Credential** cmdlet to create credential object for the user in question. The resulting credential object (which requires you to enter the password for the user) is stored in a variable named $cred1.
  
The second command then calls the **Test-CsClientAuthentication** cmdlet, specifying the FQDN of the Registrar pool (TargetFqdn), the user's SIP address (UserSipAddress) and the credential object created in the initial command (UserCredential).
  
```
$cred1 = Get-Credential "litwareinc\kenmyer"

Test-CsClientAuthentication -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $cred1
```

## Detailed Description

Client certificates provide an alternate way for users to be authenticated by Skype for Business Server 2015. In order to determine whether or not a user can log on to the system by using a client certificate, you can run the **Test-CsClientAuthentication** cmdlet. When you run the **Test-CsClientAuthentication** cmdlet you must specify the Registrar pool and SIP address of the user account being tested; you must also be able to supply the user's logon name and password. After calling the **Test-CsClientAuthentication** cmdlet, the cmdlet will contact the certificate provisioning service and download a copy of any client certificates for the specified user. If a client certificate can be found and downloaded, the **Test-CsClientAuthentication** cmdlet will then attempt to log on using that certificate. If logon succeeds, the **Test-CsClientAuthentication** cmdlet will log off and report that the test succeeded.
  
If a certificate cannot be found or downloaded, or if the cmdlet is unable to logon using that certificate, then the **Test-CsClientAuthentication** cmdlet will report that the test failed.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _UserCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credential object for the user account to be used in the test. The value passed to UserCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\kenmyer and stores that object in a variable named $x: <br/>  `$x = Get-Credential "litwareinc\kenmyer"` <br/> You need to supply the user password when running this command.  <br/> |
| _UserSipAddress_ <br/> |Required  <br/> |System.String  <br/> |SIP address of the user to be used in the test. For example:  `-UserSipAddress sip:kenmyer@litwareinc.com`.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _LiveIdAuthentication_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Verifies the ability of the test user to log on using their OrgId (Business LiveId) credentials.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/>  `-OutLoggerVariable TestOutput` <br/> Note: Do not use prepend a $ character when specifying the variable name.To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/>  `$TestOutput.ToHTML() > C:\Logs\TestOutput.html` <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/>  `$TestOutput.ToXML() > C:\Logs\TestOutput.xml` <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/>  `-OutVerboseVariable TestOutput` <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |System.Int32  <br/> |SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.  <br/> |
| _TargetFqdn_ <br/> |Optional  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the Registrar pool where client authentication is to be tested. For example:  `-TargetFqdn "atl-cs-001.litwareinc.com"`.  <br/> |
| _TargetUri_ <br/> |Optional  <br/> |System.String  <br/> |URL of the certificate provisioning service. If this parameter is not included then the **Test-CsClientAuthentication** cmdlet will use the certificate provisioning service configured for the Registrar pool. <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _IsPoolInMaintenanceMode_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _TelemetryTenantToken_ <br/> |Optional  <br/> |System.Security.SecureString  <br/> |PARAMVALUE: SecureString  <br/> |
| _TimeToWriteLogToConsole_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
   
## Input Types

None.
  
## Return Types

The **Test-CsClientAuthentication** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.
  
## See also

#### 

[Get-CsWebServiceConfiguration](get-cswebserviceconfiguration.md)
  
[Test-CsRegistration](test-csregistration.md)

