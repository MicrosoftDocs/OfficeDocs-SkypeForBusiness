---
title: "Test-CsUnifiedContactStore"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0aeca874-87da-4bc8-b2f2-c9c7e0d86883
description: "Verifies whether or not a user's contacts can be accessed through the Unified Contact Store. The Unified Contact Store provides a way for users to maintain a single set of contacts that can be accessed using Skype for Business, Outlook, and/or Outlook Web App. This cmdlet was introduced in Lync Server 2013."
---

# Test-CsUnifiedContactStore
[]
Verifies whether or not a user's contacts can be accessed through the Unified Contact Store. The Unified Contact Store provides a way for users to maintain a single set of contacts that can be accessed using Skype for Business, Outlook, and/or Outlook Web App. This cmdlet was introduced in Lync Server 2013.
  
```
Test-CsUnifiedContactStore -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID | OAuth | OAuthInteractive>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The commands shown in Example 2 verify whether or not contacts for the user litwareinc\kenmyer can be found in the unified contact store. To do this, the first command in the example uses the **Get-Credential** cmdlet to create a Windows PowerShell command-line interface credentials object for the user litwareinc\kenmyer. Note that you must supply the password for this account in order to create a valid credentials object and to ensure that the **Test-CsUnifiedContactStore** cmdlet can carry out its check.
  
The second command in the example uses the supplied credentials object ($x) and the SIP address of the user litwareinc\kenmyer in order to determine whether or not his contacts can be found in the unified contact store.
  
```
$credential = Get-Credential "litwareinc\kenmyer"

Test-CsUnifiedContactStore -TargetFqdn "atl-cs-001.litwareinc.com" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential
```

## Detailed Description
<a name="DetailedDescription"> </a>

The unified contact store introduced in Lync Server 2013 gives administrators the option of storing a user's contacts in Exchange instead of in Skype for Business Server 2015; in turn that allows the user to access the same set of contacts in Outlook and Outlook Web Access as well as in Skype for Business. (Alternatively, you can continue to store contacts in Skype for Business Server 2015. In that case, users will have to maintain two separate sets of contacts: one for use with Outlook and Outlook Web App, and one for use with Skype for Business.)
  
You can verify whether or not a user's contacts have been moved to the unified contact store by running the **Test-CsUnifiedContactStore** cmdlet. The **Test-CsUnifiedContactStore** cmdlet will take the specified user account, connect to the unified contact store, and attempt to retrieve a contact for the user. If no contacts can be retrieved then the command will fail along with the message "No contacts were received for the user. Verify that contacts exist for the user."
  
Note that the **Test-CsUnifiedContactStore** cmdlet will fail if the user has successfully migrated to the unified contact store but does not have any contacts on his or her Contacts list. The specified user must have at least one contact in order for the **Test-CsUnifiedContactStore** cmdlet to complete successfully.
  
Lync Server Control Panel: The functions carried out by the **Test-csUnifiedContactStore** cmdlet are not available in the Lync Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _TargetFqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the pool to be tested.  <br/> |
| _UserCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credentials object for the user account to be used in the test. The value passed to UserCredential should be an object reference obtained by using the G **et-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\kenmyer and stores that object in a variable named $x: <br/>  `$x = Get-Credential "litwareinc\kenmyer"` <br/> You need to supply the user password when running this command.  <br/> .This parameter is not required if you are running the test by using test users configured via the **CsHealthMonitoringConfiguration** cmdlets <br/> |
| _Authentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+AuthenticationMechanism  <br/> |Type of authentication used when running the test. Allowed values are:  <br/> \* TrustedServer  <br/> \* Negotiate  <br/> \* ClientCertificate  <br/> \* LiveID  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/>  `-OutLoggerVariable TestOutput` <br/> Note: Do not prepend a $ character when specifying the variable name.  <br/> To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/>  `$TestOutput.ToHTML() > C:\Logs\TestOutput.html` <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/>  `$TestOutput.ToXML() > C:\Logs\TestOutput.xml` <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/>  `-OutVerboseVariable TestOutput` <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |System.Int32  <br/> |SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.  <br/> |
| _UserSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address of the user to be used in the test. For example:  <br/>  `-UserSipAddress "sip:kenmyer@litwareinc.com"` <br/> This parameter is not required if you are running the test by using test users configured via the **CsHealthMonitoringConfiguration** cmdlets. <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _HybridOnlineUserAuthentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+HybridOnlineAuthenticationMechanism  <br/> |PARAMVALUE: LiveID | OAuth  <br/> |
| _HybridOnlineUserCredential_ <br/> |Optional  <br/> |System.Management.Automation.PSCredential  <br/> |PARAMVALUE: PSCredential  <br/> |
| _IsHybridOnlineUser_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _IsPoolInMaintenanceMode_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _TelemetryTenantToken_ <br/> |Optional  <br/> |System.Security.SecureString  <br/> |PARAMVALUE: SecureString  <br/> |
| _TimeToWriteLogToConsole_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Test-CsUnifiedContactStore** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Test-CsUnifiedContactStore** cmdlet returns instances of the Microsoft.Rtc.SyntheticTransactions.WebTaskOutput object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[New-CsUserServicesPolicy](new-csuserservicespolicy.md)
  
[Set-CsUserServicesPolicy](set-csuserservicespolicy.md)

