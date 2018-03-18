---
title: "Test-CsGroupExpansion"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e41db33d-d028-4171-9418-ec04885be2fc
description: "Tests the ability of a user to employ group expansion. Skype for Business Server 2015 enables users to configure an Active Directory distribution group as a contact. When youexpanda group you will see the name and presence information for each member of the group. This cmdlet was introduced in Lync Server 2010."
---

# Test-CsGroupExpansion
 
Tests the ability of a user to employ group expansion. Skype for Business Server 2015 enables users to configure an Active Directory distribution group as a contact. When you "expand" a group you will see the name and presence information for each member of the group. This cmdlet was introduced in Lync Server 2010.
  
```
Test-CsGroupExpansion -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID | OAuth | OAuthInteractive>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 connects to the Registrar pool atl-cs-001.litwareinc.com in order to verify group expansion. To run the test, the command uses the group FinanceGroup@litwareinc.com.
  
```
Test-CsGroupExpansion -TargetFqdn atl-cs-001.litwareinc.com -GroupEmailAddress FinanceGroup@litwareinc.com 
```

## Detailed Description

Users sometimes need to communicate on a regular basis with all the members of an Active Directory distribution group; for example, that group might comprise all the members of a team or all the people assigned to a particular project. In recognition of this, Skype for Business Server 2015 allows you to configure a distribution group as a contact. If you do this, you can then send the same instant message to all the group members simply by addressing the message to the group rather than each individual member of that group. 
  
There might also be times when you need to communicate with (or check the presence of) certain individuals in the group. Group expansion enables you to quickly and easily view all the group members and their current status. In addition to that, you can also select one or more group members, and then send an instant message just to those users rather than to all the members of the group.
  
Group expansion is enabled and disabled by using the **Set-CsWebServiceConfiguration** cmdlet. If group expansion is enabled, you can determine whether the feature is working by running the **Test-CsGroupExpansion** cmdlet. With this cmdlet, you specify an Active Directory distribution group by using the group's email address. The **Test-CsGroupExpansion** cmdlet then uses group expansion to retrieve the group membership and compare the retrieved list with the membership of the group email address that you supplied. If the two lists match, then group expansion is working correctly.
  
Note that you can test group expansion in two different ways: by testing the service itself or by testing the associated web service.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _GroupEmailAddress_ <br/> |Required  <br/> |System.String  <br/> |Email address of the targeted distribution group. For example:  `-GroupEmailAddress "FinanceGroup@litwareinc.com"`.  <br/> |
| _TargetFqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the Registrar pool where group expansion is to be tested. For example:  `-TargetFqdn "atl-cs-001.litwareinc.com"`.  <br/> Note that you cannot use both the TargetUri parameter and the TargetFqdn parameter in the same command.  <br/> |
| _TargetUri_ <br/> |Required  <br/> |System.String  <br/> |Uniform Resource Identifier (URI) of the Group Expansion Web service. For example:  `-TargetUri "https://atl-cs-001.litwareinc.com/groupexpansion"`.  <br/> Note that you cannot use both the TargetUri parameter and the TargetFqdn parameter in the same command.  <br/> |
| _UserCredential_ <br/> |Required  <br/> |System.Management.Automation.PSCredential  <br/> |User credential object for the user account to be used in the test. The value passed to UserCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\kenmyer and stores that object in a variable named $x: <br/>  `$x = Get-Credential "litwareinc\kenmyer"` <br/> You will need to supply the user password when running this command.  <br/> The user credential is not required if you are running the test under the credentials of the logged-on user and using the TargetFqdn parameter. The user credential is required if you are using the TargetUri parameter.  <br/> |
| _Authentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+AuthenticationMechanism  <br/> |Type of authentication used in the test. Allowed values are:  <br/> \* TrustedServer  <br/> \* Negotiate  <br/> \* ClientCertificate  <br/> \* LiveID  <br/> |
| _DomainController_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _External_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to verify that external users can use group expansion.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/>  `-OutLoggerVariable TestOutput` <br/> Note: Do not use prepend a $ character when specifying the variable name.To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/>  `$TestOutput.ToHTML() > C:\Logs\TestOutput.html` <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/>  `$TestOutput.ToXML() > C:\Logs\TestOutput.xml` <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/>  `-OutVerboseVariable TestOutput` <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |System.Int32  <br/> |SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.  <br/> |
| _UserSipAddress_ <br/> |Optional  <br/> |System.String  <br/> |SIP address of the user to be used in the test. If this parameter is not specified, then the **Test-CsGroupExpansion** cmdlet will conduct its checks using the account of the logged-on user. <br/> |
| _WebCredential_ <br/> |Optional  <br/> |System.Management.Automation.PSCredential  <br/> |An object containing user credentials for accessing the Location Information service. This object can be retrieved by calling the **Get-Credential** cmdlet and supplying the appropriate credentials. <br/> This parameter is required if the TargetUri and UserSipAddress parameters are specified, and the computer on which the command is run does not have a server certificate.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _HybridOnlineUserAuthentication_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+HybridOnlineAuthenticationMechanism  <br/> |PARAMVALUE: LiveID | OAuth  <br/> |
| _IsHybridOnlineUser_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _IsPoolInMaintenanceMode_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _TelemetryTenantToken_ <br/> |Optional  <br/> |System.Security.SecureString  <br/> |PARAMVALUE: SecureString  <br/> |
| _TimeToWriteLogToConsole_ <br/> |Optional  <br/> |System.UInt32  <br/> |PARAMVALUE: UInt32  <br/> |
   
## Input Types

None. The **Test-CsGroupExpansion** cmdlet does not accept pipelined input.
  
## Return Types

The **Test-CsGroupExpansion** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.
  
## See also

#### 

[Test-CsAddressBookService](test-csaddressbookservice.md)
  
[Test-CsAddressBookWebQuery](test-csaddressbookwebquery.md)

