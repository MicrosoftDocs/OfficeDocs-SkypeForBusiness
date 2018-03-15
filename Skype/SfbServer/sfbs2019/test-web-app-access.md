---
title: "Test Web App access in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 17d67ea3-f74d-4952-ac2b-92c0dacc8014

description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Test Web App access in Lync Server 2013
[]
 **In this article**
  
[Description](#sectionSection0)
  
[Running the test](#sectionSection1)
  
[Determining success or failure](#sectionSection2)
  
[Reasons why the test might have failed](#sectionSection3)
  
****

|||
|:-----|:-----|
|Verification schedule  <br/> |Monthly  <br/> |
|Testing tool  <br/> |Windows PowerShell  <br/> |
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsWebApp cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsWebApp"}```|
   
## Description
<a name="sectionSection0"> </a>

The Test-CsWebApp cmdlet verifies that authenticated users can join Lync Server conferences by using the Lync Web App. When you run the cmdlet, Test-CsWebApp contacts the Web Ticket service to obtain web tickets for the specified users. These tickets effectively act as 'admission tickets" to the Lync Server conference. If the tickets can be retrieved, and if the users can be authenticated, Test-CsWebApp will then contact Lync Server and attempt to establish separate conferences for instant messaging, application sharing, and data collaboration.
  
Note that Test-CsWebApp just verifies the APIs and connections used to create these conferences. The cmdlet is designed to verify that Lync Web App could be used to create and join conferences. However,, it does not actually create and conduct a conference.
  
## Running the test
<a name="sectionSection1"> </a>

The Test-CsWebApp cmdlet can be run using either a pair of preconfigured test accounts or the accounts of any two users who are enabled for Lync Server. To run this check using test accounts, you just have to specify the fully qualified domain name of the Lync Server pool being tested. For example:
  
```
Test-CsWebApp -TargetFqdn "atl-cs-001.litwareinc.com"
```

To run this check using actual user accounts, you must create two Windows PowerShell credentials objects (objects that contain the account name and password) for each account. You must then include those credentials objects and the SIP addresses of the two accounts when you call Test-CsWebApp:
  
```
$cred1 = Get-Credential "litwareinc\kenmyer"
$cred2 = Get-Credential "litwareinc\pilar"
Test-CsWebApp -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $cred1 -User2SipAddress "sip:pilar@litwareinc.com" -User2Credential $cred2
```

For more information, see the help topic for the [Test-CsWebApp](test-cswebapp.md) cmdlet. Note that Test-CsWebApp was deprecated for use on Lync Server 2013. 
  
## Determining success or failure
<a name="sectionSection2"> </a>

If Test-CsWebApp can join the users to their conferences, the cmdlet will return the test result Success: 
  
Target Fqdn :
  
Result : Success
  
Latency : 00:00:00
  
Error Message :
  
Diagnosis :
  
If the users cannot join the necessary conferences then the test result will be marked as Failure. Typically Test-CsWebApp will also report back a detailed error message and diagnosis: 
  
Target Fqdn : atl-cs-001.litwareinc.com
  
Result : Failure
  
Latency : 00:00:00
  
Error Message : No response received for Web-Ticket service
  
Diagnosis : The HTTP request is unauthorized with client
  
 authentication scheme 'Ntlm'. The authentication 
  
 header received from the server was 'Negotiate,NTLM'. 
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

Test-CsWebApp failures typically involve user authentication errors. If Test-CsWebApp fails, you should first verify that the specified users have valid user accounts and are enabled for Lync Server. You can retrieve account information by using a command similar to this:
  
```
Get-CsUser -Identity "sip:kenmyer@litwareinc.com" | Select-Object Enabled
```

If the Enabled property is not equal to True or if the command fails, that means that the user does not have a valid Lync Server account.You should also verify that the passwords that you supplied to the cmdlet are valid.
  

