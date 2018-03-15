---
title: "Testing Lync Client authentication in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e22114cb-4456-4e5f-93ab-51592c4a8209

description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Testing Lync Client authentication in Lync Server 2013
[]
 **In this article**
  
[Description](#sectionSection0)
  
[Running the test](#sectionSection1)
  
[Determining success or failure](#sectionSection2)
  
[Reasons why the test might have failed](#sectionSection3)
  
****

|||
|:-----|:-----|
|Verification schedule  <br/> |Daily  <br/> |
|Testing tool  <br/> |Windows PowerShell  <br/> |
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsClientAuth cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsClientAuth"}```|
   
## Description
<a name="sectionSection0"> </a>

The Test-CsClientAuth cmdlet enables you to determine whether a user can log on to the Lync Server by using a client certificate, you can run the Test-CsClientAuth cmdlet. After calling Test-CsClientAuth, the cmdlet will contact the certificate provisioning service and download a copy of any client certificates for the specified user. If a client certificate can be found and downloaded, Test-CsClientAuth will then attempt to log on by using that certificate. If logon succeeds, Test-CsClientAuth will log off and report that the test succeeded. If a certificate cannot be found or downloaded, or if the cmdlet is unable to logon using that certificate, then Test-CsClientAuth will report that the test failed.
  
## Running the test
<a name="sectionSection1"> </a>

The Test-CsClientAuth cmdlet is run by using the account of any user who is enabled for Lync Server. To run this check using an actual user account, you must first create a Windows PowerShell credentials object that contains the account name and password. You must then include that credentials object and the SIP address assigned to the account when the system calls Test-CsClientAuth:
  
```
$credential = Get-Credential "litwareinc\kenmyer"
Test-CsClientAuth -TargetFqdn "atl-cs-001.litwareinc.com"-UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential
```

For more information, see the Help documentation for the [Test-CsClientAuth](https://technet.microsoft.com/en-us/library/gg398712%28v=ocs.14%29.aspx) cmdlet. 
  
## Determining success or failure
<a name="sectionSection2"> </a>

If the specified user can log on to Lync Server by using a client certificate, you will receive output similar to this, with the Result property marked as **Success:**
  
TargetFqdn : atl-cs-001.litwareinc.com
  
Result : Success
  
Latency : 00:00:06.8630376
  
Error :
  
Diagnosis :
  
If the specified user can not log on, the Result will be shown as Failure and additional information will be recorded in the Error and Diagnosis properties:
  
TargetFqdn : atl-cs-001.litwareinc.com
  
Result : Failure
  
Latency : 00:00:03.3645259
  
Error : Could not download a CS Certificate for the given user. Check if
  
 provided uri and credentials are correct. 
  
Diagnosis :
  
For example, the previous output states that the test failed because a valid client certificate couldn't be located for the specified user. You can return a list of the client certificates issued to a user by running a command as follows: 
  
```
Get-CsClientCertificate -Identity "sip:kenmyer@litwareinc.com"
```

If Test-CsClientAuth fails, then you might want to rerun the test, this time including the Verbose parameter: 
  
```
$credential = Get-Credential "litwareinc\kenmyer"
Test-CsClientAuth -TargetFqdn "atl-cs-001.litwareinc.com"-UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential -Verbose
```

When the Verbose parameter is included, Test-CsClientAuth will return a step-by-step account of each action it tried when it checked the ability of the specified user to log on to Lync Server. For example: 
  
Trying to download a CS certificate for User : kenmyer@litwareinc.com endpoint : STEpid
  
Web Service url : https://atl-cs-001.litwareinc.com:443/CertProv/CertprovisioningService.svc
  
Could not download a CS certificate from web service.
  
CHECK:
  
 - Web service url is valid and the web services are functional 
  
 - If using PhoneNo\\Pin to authenticate, make sure they match the user uri 
  
 - If using NTLM\Kerberos auth, make sure you provided valid credentials 
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

Here are some common reasons why Test-CsClientAuth might fail:
  
- You specified a user account that was not valid. You can verify that a user account exists by running a command similar to this: 
    
  ```
  Get-CsUser "sip:kenmyer@litwareinc.com"
  ```

- The user account is valid, but the account is currently not enabled for Lync Server. To verify that a user account is enabled for Lync Server, run a command similar to the following: 
    
  ```
  Get-CsUser "sip:kenmyer@litwareinc.com" | Select-Object Enabled
  ```

    If the Enabled property is set to False, that means that the user is currently not enabled for Lync Server.
    
- The test user might not have a valid client certificate. You can return information about the client certificates assigned to a user by using a command similar to this: 
    
  ```
  Get-CsClientCertificate -Identity "sip:kenmyer@litwareinc.com"
  ```

