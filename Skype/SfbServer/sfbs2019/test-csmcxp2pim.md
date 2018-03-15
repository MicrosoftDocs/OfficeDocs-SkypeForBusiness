---
title: "Test-CsMcxP2PIM"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 443a3b31-6f58-4570-9eaa-310e73c39e03
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Test-CsMcxP2PIM
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Tests the ability of a pair of users to exchange instant messages by using the Lync Server Mobility Service. The Mobility Service enables users of mobile phones such as iPhones and Windows Phones to do such things as exchange instant messages and presence information; store and retrieve voice mail internally instead of with their wireless provider; and take advantage of Lync Server capabilities such as Call via Work and dial-out conferencing. This cmdlet was introduced in the cumulative update for Lync Server 2010: November 2011.
  
```
Test-CsMcxP2PIM -ReceiverSipAddress <String> -SenderSipAddress <String> <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The commands shown in Example 1 test to see whether or not a pair of users - Ken Myer and Pilar Ackerman - are able to exchange instant messages by using the Mobility Service. To do this, the first two commands in the example use the **Get-Credential** cmdlet to create credentials objects for the two users; the credentials for Ken Myer are stored in a variable named $credential1 and the credentials for Pilar Ackerman are stored in a variable named $credential2. 
  
After the credential objects have been created, the final command calls the **Test-CsMcxP2PIM** cmdlet, making sure to specify the target Registrar pool (atl-cs-001.litwareinc,com), the authentication type (Negotiate), and the SIP addresses and credentials of the two users. 
  
```
$credential1 = Get-Credential "litwareinc\kenmyer"
$credential2 = Get-Credential "litwareinc\pilar"
Test-CsMcxP2PIM -TargetFqdn "atl-cs-001.litwareinc.com" -Authentication Negotiate -SenderSipAddres "sip:kenmyer@litwareinc.com" -SenderCredential $credential1 -ReceiverSipAddress "sip:packerman@litwareinc.com" -ReceiverCredential $credential2

```

## Detailed Description
<a name="sectionSection1"> </a>

Lync Server Mobility Service extends many of the capabilities of Lync Server to mobile devices such as Apple iPhones, Windows Phone, Android phones, and Nokia phones. Among other things, users can use these phones to exchange instant message and presence information, and to receive notifications of new voice mails. Thanks to the push notification service (Apple Push Notification Service and Microsoft Push Notification Service), users with iPhones or Windows Phones can receive these notifications even if Lync Server is running in the background. The Mobility Service also provides the opportunity for organizations to enable Call via Work. With Call via Work, users can make a call from their mobile phone and make it appear as though the call originated from their work phone; for example, Caller ID systems will display the user's work number instead of his or her mobile phone number.
  
The **Test-CsMcxP2PIM** cmdlet is used to determine whether or not a pair of users is able to exchange instant messages by using the Mobility Service. Note that running this cmdlet does not require the use of mobile phones nor does it actually send any instant messages. Instead, the cmdlet verifies that the two users are able to log on to Lync Server and that the Mobility Service is able to make the connections required to exchange instant messages between the two users. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Test-CsMcxP2PIM** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsMcxP2PIM"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Authentication_ <br/> |Required  <br/> |SipSyntheticTransaction AuthenticationMechanism  <br/> |Allowed values are: TrustedServer; Negotiate; ClientCertificate; and LiveID.  <br/> |
| _ReceiverCredential_ <br/> |Required  <br/> |PSCredential  <br/> |User credentials object for the first of the two user accounts to be tested. The value passed to ReceiverCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\pilar and stores that object in a variable named $y:  <br/> $y = Get-Credential "litwareinc\pilar"  <br/> You need to supply the user password when running this command.  <br/> |
| _ReceiverSipAddress_ <br/> |Required  <br/> |String  <br/> |SIP address for the first of the two user accounts to be tested. For example:  <br/> -ReceiverSipAddress "sip:pilar@litwareinc.com"  <br/> The ReceiverSipAddress parameter must reference the same user account as the ReceiverCredential parameter.  <br/> |
| _SenderCredential_ <br/> |Required  <br/> |PSCredential  <br/> |User credentials object for the second of the two user accounts to be tested. The value passed to SenderCredential should be an object reference obtained by using the **Get-Credential** cmdlet. For example, this code returns a credentials object for the user litwareinc\kenmyer and stores that object in a variable named $x:  <br/> $x = Get-Credential "litwareinc\kenmyer"  <br/> You need to supply the user password when running this command.  <br/> |
| _SenderSipAddress_ <br/> |Required  <br/> |String  <br/> |SIP address for the second of the two user accounts to be tested. For example:  <br/> -SenderSipAddress "sip:kenmyer@litwareinc.com"  <br/> The SenderSipAddress parameter must reference the same user account as the SenderCredential parameter.  <br/> |
| _TargetFqdn_ <br/> |Required  <br/> |String  <br/> |Fully qualified domain name (FQDN) of the pool to be tested.  <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _OutLoggerVariable_ <br/> |Optional  <br/> |System.String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods - ToHTML and ToXML - that can then be used to save that output to either an HTML or an XML file.  <br/> To store output in a logger variable named $TestOutput use the following syntax:  <br/> -OutLoggerVariable TestOutput  <br/> Note: Do not use prepend a $ character when specifying the variable name.  <br/> To save the information stored in the logger variable to an HTML file, use a command similar to this:  <br/> $TestOutput.ToHTML() \> C:\Logs\TestOutput.html  <br/> To save the information stored in the logger variable to an XML file, use a command similar to this:  <br/> $TestOutput.ToXML() \> C:\Logs\TestOutput.xml  <br/> |
| _OutVerboseVariable_ <br/> |Optional  <br/> |String  <br/> |When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:  <br/> -OutVerboseVariable TestOutput  <br/> Do not use prepend a $ character when specifying the variable name.  <br/> |
| _RegistrarPort_ <br/> |Optional  <br/> |Int32  <br/> |SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Test-CsMcxP2PIM** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Test-CsMcxP2PIM** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object. 
  

