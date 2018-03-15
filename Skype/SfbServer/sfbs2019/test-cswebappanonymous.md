---
title: "Test-CsWebAppAnonymous"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: acfb28c1-8db6-4d2b-95ad-5c824660ea71
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Test-CsWebAppAnonymous
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Verifies that anonymous users can use the Lync Web App to join a Lync Server conference. This cmdlet was introduced in Lync Server 2010.
  
This cmdlet has been deprecated for use with the on-premises version of Lync Server 2013. Instead, administrators should use the [Test-CsUcwaConference](test-csucwaconference.md) cmdlet to perform these tests. 
  
```
Test-CsWebAppAnonymous -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 verifies whether or not a test user configured for the pool atl-cs-001.litwareinc.com can use Lync Web App to anonymously join a conference. This command will only succeed if you have configured a test user for the pool by using the **CsHealthMonitoringConfiguration** cmdlets. 
  
```
Test-CsWebAppAnonymous -TargetFqdn atl-cs-001.litwareinc.com

```

### EXAMPLE 2

The commands shown in Example 2 verify whether or not the user Ken Myer can use Lync Web App to anonymously join a conference. To use an actual user account, the first command in the example uses the **Get-Credential** cmdlet to create a Windows PowerShell credentials object for the user litwareinc\kenmyer. That credentials object (stored in a variable named $cred1) is then passed to the UserCredential parameter in the second command in the example. In addition to the UserCredential parameter, the UserSipAddress parameter is also included, along with Ken Myer's SIP address. 
  
```
$cred1 = Get-Credential "litwareinc\kenmyer"
Test-CsWebApp -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $cred1 

```

## Detailed Description
<a name="sectionSection1"> </a>

The **Test-CsWebAppAnonymous** cmdlet enables administrators to verify that anonymous users can employ Microsoft Exchange Server 2013 in order to join conferences. When you run the **Test-CsWebAppAnonymous** cmdlet, the cmdlet attempts to obtain an anonymous web ticket by using the Web Ticket service. If the ticket can be obtained, the **Test-CsWebAppAnonymous** cmdlet will then try to connect to by Lync Server using Lync Web App. If the connection is made, the cmdlet will then attempt to establish separate conferences for instant messaging, application sharing, and data collaboration. 
  
Many administrators will use the **CsHealthMonitoringConfiguration** cmdlets to set up test users for each of their Registrar pools. These test users represent a pair of user accounts that have been preconfigured for use with synthetic transactions. (Typically these are test accounts and not accounts that belong to actual users.) If test users are configured for a pool, administrators can run the **Test-CsWebAppAnonymous** cmdlet against that pool without having to specify the identity of (and supply the credentials for) the user account involved in the test. 
  
Alternatively, administrators can run the **Test-CsWebAppAnonymous** cmdlet using an actual user account. If you decide to conduct the test using an actual user account you will need to supply the logon name and password for that account. 
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _TargetFqdn_ <br/> |Required  <br/> |String  <br/> |Fully qualified domain name (FQDN) of the pool to be tested. For example:  <br/> -TargetFqdn atl-cs-001.litwareinc.com  <br/> |
| _TargetUri_ <br/> |Required  <br/> |String  <br/> |Uniform Resource Identifier (URI) of the Reach server. For example:  <br/> -TargetUri "https://atl-cs-001.litwareinc.com/reach"  <br/> You cannot use both the TargetUri parameter and the TargetFqdn parameter in the same command.  <br/> |
| _UserCredential_ <br/> |Required  <br/> |PSCredential  <br/> |User credentials object for the first of the two user accounts to be tested. The value passed to UserCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\pilar and stores that object in a variable named $x:  <br/> $x = Get-Credential "litwareinc\pilar"  <br/> You need to supply the user password when running this command.  <br/> This parameter is not required if you are running the test by using test users configured via the **CsHealthMonitoringConfiguration** cmdlets.  <br/> |
| _Authentication_ <br/> |Optional  <br/> |SipSyntheticTransaction AuthenticationMechanism  <br/> |Type of authentication used when running the test. Allowed values are:  <br/> \* TrustedServer  <br/> \* Negotiate  <br/> \* ClientCertificate  <br/> \* LiveID  <br/> |
| _External_ <br/> |Optional  <br/> |SwitchParameter  <br/> |When present, causes the **Test-CsWebAppAnonymous** cmdlet to test the Reach server's external web relay. If this parameter is not present, the cmdlet will test the internal web relay. The web relay serves as an intermediary between the internal network and the Internet.  <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/> -OutLoggerVariable TestOutput  <br/> Note: Do not prepend a $ character when specifying the variable name.  <br/> To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/> $TestOutput.ToHTML() \> C:\Logs\TestOutput.html  <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/> $TestOutput.ToXML() \> C:\Logs\TestOutput.xml  <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax  <br/> -OutVerboseVariable TestOutput  <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |Int32  <br/> |SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.  <br/> |
| _UserSipAddress_ <br/> |Optional  <br/> |String  <br/> |SIP address for the first of the two user accounts to be tested. For example:  <br/> -UserSipAddress "sip:kenmyer@litwareinc.com"  <br/> This parameter is not required if you are running the test by using test users configured via the CsHealthMonitoringConfiguration cmdlets.  <br/> |
| _WebCredential_ <br/> |Optional  <br/> |PSCredential  <br/> |User credential object for the user account to be used in the test. The value passed to UserCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\kenmyer and stores that object in a variable named $x:  <br/> $x = Get-Credential "litwareinc\kenmyer"  <br/> This parameter is required if either the TargetUri parameter or the UserSipAddress parameters are specified and the computer on which the command is run does not have a server certificate.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

The **Test-CsWebAppAnonymous** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object. 
  

