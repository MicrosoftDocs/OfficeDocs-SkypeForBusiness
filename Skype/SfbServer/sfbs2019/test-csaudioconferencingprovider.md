---
title: "Test-CsAudioConferencingProvider"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9e00081e-5825-4ee9-a838-3c91ad054589
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Test-CsAudioConferencingProvider
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Tests to see if a user can connect to his or her audio conferencing provider. An audio conferencing provider is a third-party company that provides organizations with conferencing services. Among other things, audio conferencing providers enable users located off site, and not connected to the corporate network or the Internet, to participate in the audio portion of a conference or meeting. This cmdlet was introduced in Lync Server 2013.
  
```
Test-CsAudioConferencingProvider -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

Example 1 checks to see if a test user defined for the pool atl-cs-001.litwareinc.com is able to connect to his or her audio conferencing provider. This command requires that at least one test user be defined for the pool. If no test users have been defined for atl-cs-001.litwareinc.com, then the command will fail; that's because the **Test-CsAudioConferencingProvider** cmdlet will not know which user to employ in the test. If you have not defined test users for a pool, then you must include the UserSipAddress parameter and the credentials of the user account that the command should employ when verifying the connection with an audio conferencing provider. 
  
```
Test-CsAudioConferencingProvider -TargetFqdn atl-cs-001.litwareinc.com
```

### Example 2

The commands shown in Example 2 test the ability of a specific user (litwareinc\kenmyer) to connect to his audio conferencing provider. To do this, the first command in the example uses the **Get-Credential** cmdlet to create a Windows PowerShell command-line interface credentials object containing the name and password of the user Ken Myer. (Because the logon name litwareinc\kenmyer has been included as a parameter, the Windows PowerShell Credential Request dialog box only requires the administrator to enter the password for the Ken Myer account.) The resulting credentials object is stored in a variable named $credential. 
  
The second command then checks to see if this user can connect to his audio conferencing provider. To carry out this task, the **Test-CsAudioConferencingProvider** cmdlet is called, along with three parameters: TargetFqdn (the FQDN of the Registrar pool); UserCredential (the Windows PowerShell object containing Ken Myer's user credentials); and UserSipAddress (the SIP address corresponding to the supplied user credentials). 
  
```
$credential = Get-Credential "litwareinc\kenmyer"
Test-CsAudioConferencingProvider -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential
```

## Detailed Description
<a name="DetailedDescription"> </a>

An audio conferencing provider is a third-party company that provides organizations with conferencing services. Among other things, audio conferencing providers enable users located off site, and not connected to the corporate network or the Internet, to participate in the audio portion of a conference or meeting. Audio conferencing providers often provide high-end services such as live translation, transcription, and live per-conference operator assistance.
  
The **Test-CsAudioConferencingProvider** cmdlet is used to verify that a user is able to make a connection to his or her audio conferencing provider. Note that this cmdlet can be run in one of two ways. Many administrators will use the CsHealthMonitoringConfiguration cmdlets to set up test users for each of their Registrar pools. These test users represent a pair of user accounts that have been preconfigured for use with synthetic transactions. (Typically these are test accounts and not accounts that belong to actual users.) If test users are configured for a pool, administrators can run the **Test-CsAudioConferencingProvider** cmdlet against that pool without having to specify the identity of (and supply the credentials for) the user account involved in the test. 
  
Alternatively, administrators can run the **Test-CsAudioConferencingProvider** cmdlet using an actual user account. If you decide to conduct the test using an actual user account you will need to supply the logon name and password for that account. 
  
Note that the test will fail if the user employed by the **Test-CsAudioConferencingProvider** cmdlet has not been assigned an audio conferencing provider. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Test-CsAudioConferencingProvider** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsAudioConferencingProvider"}
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _TargetFqdn_ <br/> |Required  <br/> |String  <br/> |Fully qualified domain name (FQDN) of the pool to be tested.  <br/> |
| _UserCredential_ <br/> |Required  <br/> |PSCredential  <br/> |User credential object for the account to be tested. The value passed to UserCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\kenmyer and stores that object in a variable named $x:  <br/> $x = Get-Credential "litwareinc\kenmyer"  <br/> You need to supply the user password when running this command.  <br/> This parameter is not needed if the command is using test users configured by using the CsHealthMonitoringConfiguration cmdlets.  <br/> |
| _Authentication_ <br/> |Optional  <br/> |SipSyntheticTransaction AuthenticationMechanism  <br/> |Type of authentication used when running the test. Allowed values are:  <br/> \* TrustedServer  <br/> \* Negotiate  <br/> \* ClientCertificate  <br/> \* LiveID  <br/> |
| _DialoutUserCredential_ <br/> |Optional  <br/> |PSCredential  <br/> |User credential object for the dialout user account to be tested. The value passed to DialoutUserCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\pilar and stores that object in a variable named $x:  <br/> $x = Get-Credential "litwareinc\pilar"  <br/> You need to supply the user password when running this command.  <br/> |
| _DialoutUserSipAddress_ <br/> |Optional  <br/> |String  <br/> |SIP address for the dialout user account to be tested. For example: -DialoutUserSipAddress "sip:pilar@litwareinc.com". The DialoutUserSipAddress parameter must reference the same user account as DialoutUserCredential.  <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/> -OutLoggerVariable TestOutput  <br/> Note: Do not prepend a $ character when specifying the variable name.  <br/> To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/> $TestOutput.ToHTML() \> C:\Logs\TestOutput.html  <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/> $TestOutput.ToXML() \> C:\Logs\TestOutput.xml  <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/> -OutVerboseVariable TestOutput  <br/> Do not prepend a $ character when specifying the variable name.  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |Int32  <br/> |SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.  <br/> |
| _TestJoinLauncher_ <br/> |Optional  <br/> |SwitchParameter  <br/> |When present, tests the ability of the Join Launcher to participate in a conference. The Join Launcher is used to help users of mobile devices (and, as a result, users of the Mobility Service) take part in conferences.  <br/> |
| _UserSipAddress_ <br/> |Optional  <br/> |String  <br/> |SIP address for the user account to be tested. For example: -UserSipAddress "sip:kenmyer@litwareinc.com". The UserSipAddress parameter must reference the same user account as UserCredential.  <br/> This parameter is not needed if the command is using test users configured by using the CsHealthMonitoringConfiguration cmdlets.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Test-CsAudioConferencingProvider** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

The **Test-CsAudioConferencingProvider** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object. 
  

