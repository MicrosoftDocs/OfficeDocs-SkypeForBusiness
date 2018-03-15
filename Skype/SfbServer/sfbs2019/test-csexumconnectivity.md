---
title: "Test-CsExUMConnectivity"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2eb541d2-5f09-483c-adc2-4abb16391ea5
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Test-CsExUMConnectivity
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Verifies that a test user can connect to Exchange Unified Messaging. This cmdlet was introduced in Lync Server 2013.
  
```
Test-CsExUMConnectivity -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

The preceding example tests Exchange Unified Messaging connectivity for the pool atl-cs-001.litwareinc.com. This command will work only if test users have been defined for the pool atl-cs-001.litwareinc.com. If they have, then the command will determine whether or not the first test user is able to connect to Unified Messaging. If test users have not been configured for the pool then the command will fail.
  
```
Test-CsExUMConnectivity -TargetFqdn "atl-cs-001.litwareinc.com"
```

### Example 2

The commands shown in Example 2 test Exchange Unified Messaging connectivity for the user litwareinc\kenmyer. To do this, the first command in the example uses the **Get-Credential** cmdlet to create a Windows PowerShell command-line interface credentials object for the user litwareinc\kenmyer. Note that you must supply the password for this account in order to create a valid credentials object and to ensure that the **Test-CsExUMConnectivity** cmdlet can carry out its check. 
  
The second command in the example uses the supplied credentials object ($x) and the SIP address of the user litwareinc\kenmyer in order to determine whether or this user can connect to Exchange Unified Messaging.
  
```
$credential = Get-Credential "litwareinc\kenmyer"
Test-CsExUMConnectivity -TargetFqdn "atl-cs-001.litwareinc.com" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential
```

### Example 3

The command shown in Example 3 is a variation of the command shown in Example 2; in this case, however, the OutLoggerVariable parameter is included in order to generate a detailed log of every step undertaken by the **Test-CsExUMConnectivity** cmdlet, as well as the success or failure of each of those steps. To do this, the OutLoggerVariable parameter is added along with the parameter value ExumText; that causes detailed logging information to be stored in a variable named $ExumTest. In the final command in the example, the ToXML() method is used to convert the log information to XML format. That XML data is then written to a file named C:\Logs\ExumTest.xml by using the Out-File cmdlet. 
  
```
$credential = Get-Credential "litwareinc\kenmyer"
Test-CsExUMConnectivity -TargetFqdn "atl-cs-001.litwareinc.com" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential -OutLoggerVariable ExumTest
$ExumTest.ToXML() | Out-File C:\Logs\ExumTest.xml
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Test-CsExUMConnectivity** cmdlet verifies that the specified user can connect to the Microsoft Exchange Server 2013 unified messaging service. Note that this cmdlet only verifies that a connection can be made to the service; it does not test the service itself. To test the unified messaging service (by running a synthetic transaction cmdlet that actually leaves a voice mail message in a user's mailbox) use the [Test-CsExUMVoiceMail](test-csexumvoicemail.md) cmdlet. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsExUMConnectivity"}
  
 **Lync Server Control Panel:** The functions carried out by the **Test-CsExUMConnectivity** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _TargetFqdn_ <br/> |Required  <br/> |String  <br/> |Fully qualified domain name of the pool being tested for Exchange Unified Messaging connectivity.  <br/> |
| _UserCredential_ <br/> |Required  <br/> |PSCredential  <br/> |User credentials object for the user account to be used in the test. The value passed to UserCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\kenmyer and stores that object in a variable named $x:  <br/> $x = Get-Credential "litwareinc\kenmyer"  <br/> You need to supply the user password when running this command.  <br/> This parameter is not required if you are running the test by using test users configured via the CsHealthMonitoringConfiguration cmdlets.  <br/> |
| _Authentication_ <br/> |Optional  <br/> |SipSyntheticTransaction AuthenticationMechanism  <br/> |Type of authentication used when running the test. Allowed values are:  <br/> \* TrustedServer  <br/> \* Negotiate  <br/> \* ClientCertificate  <br/> \* LiveID  <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/> -OutLoggerVariable TestOutput  <br/> Note: Do not use prepend a $ character when specifying the variable name.  <br/> To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/> $TestOutput.ToHTML() \> C:\Logs\TestOutput.html  <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/> $TestOutput.ToXML() \> C:\Logs\TestOutput.xml  <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/> -OutVerboseVariable TestOutput  <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |Int32  <br/> |SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.  <br/> |
| _UserSipAddress_ <br/> |Optional  <br/> |String  <br/> |SIP address of the user to be used in the test. For example:  <br/> -UserSipAddress "sip:kenmyer@litwareinc.com"  <br/> This parameter is not required if you are running the test by using test users configured via the CsHealthMonitoringConfiguration cmdlets.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Test-CsExUMConnectivity** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

The **Test-CsExUMConnectivity** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Test-CsExUMVoiceMail](test-csexumvoicemail.md)

