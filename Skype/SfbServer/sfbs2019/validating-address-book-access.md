---
title: "Validating address book access in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 630682c6-9262-46c5-9af1-6193db70374b

description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Validating address book access in Lync Server 2013
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
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsAddressBookService cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsAddressBookService"}```|
   
## Description
<a name="sectionSection0"> </a>

The Test-CsAddressBookService cmdlet provides a way for you to verify that a user can connect to the Address Book Download Web service. When you run the cmdlet, Test-CsAddressBookService connects to the Address Book Download Web service on the specified pool and requests the location of the Address Book files. If the Address Book Download Web service supplies that location, the test is considered successful. If the request is denied, then the test is considered a failure. 
  
## Running the test
<a name="sectionSection1"> </a>

The Test-CsAddressBookService cmdlet can be run using either a preconfigured test account (see Setting Up Test Accounts for Running Lync Server Tests) or the account of any user who has been enabled for Lync Server. To run this check using a test account, all you need to do is specify the fully qualified domain name (FQDN) of the Lync Server pool being tested. For example: 
  
```
Test-CsAddressBookService -TargetFqdn "atl-cs-001.litwareinc.com"
```

To run this check using an actual user account, you must first create a Windows PowerShell credentials object that contains the account name and password. You must then include that credentials object and the SIP address assigned to the account when calling Test-CsAddressBookService: 
  
```
$credential = Get-Credential "litwareinc\kenmyer"
Test-CsAddressBookService -TargetFqdn "atl-cs-001.litwareinc.com"-UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential
```

For more information, see the Help documentation for the [Test-CsAddressBookService](test-csaddressbookservice.md) cmdlet. 
  
## Determining success or failure
<a name="sectionSection2"> </a>

If the specified user is able to connect to the Address Book Service you will get back output similar to this, with the Result property marked as **Success**:
  
TargetUri : https://lync-se.fabrikam.com:443/abs/handler
  
TargetFqdn : atl-cs-001.litwareinc.com
  
Result : Success
  
Latency : 00:00:06.2260399
  
Error :
  
Diagnosis :
  
If the specified user is not able to make this connection, the Result will be shown as Failure, and additional information will be recorded in the Error and Diagnosis properties:
  
TargetUri : 
  
TargetFqdn : atl-cs-001.litwareinc.com
  
Result : Failure
  
Latency : 00:00:00
  
Diagnosis : ErrorCode=4005,Source=atl-cs-001.litwareinc.com, 
  
 Reason=Destination URI either not enabled for SIP or does not 
  
 exist. 
  
 Microsoft.Rtc.Signaling.DiagnosticHeader 
  
For example, the preceding output states that the test failed because the specified user (that is, the "Destination URI") either does not exist or has not been enabled for Lync Server. You can verify whether or not a user account is valid, and verify that you supplied the correct SIP address, by running a command like this one:
  
Get-CsUser -Identity "sip:kenmyer@litwareinc.com" | Select-Object SipAddress, Enabled
  
If Test-CsAddressBookService fails then you might want to rerun the test, this time including the Verbose parameter:
  
Test-CsAddressBookService -TargetFqdn "atl-cs-001.litwareinc.com" -Verbose
  
When the Verbose parameter is included Test-CsAddressBookService will return a step-by-step account of each action it attempted when checking the ability of the specified user to log on to Lync Server. For example, this sample output shows that Test-CsAddressBookService, at least in this example, was able to download the Address Book file:
  
Sending Http GET Request.
  
 File Path = https://atl-cs-001.litwareinc.com:443/abs/handler/f-1299.lsabs 
  
Attempt Number = 1
  
TimeOut (msec) = 60000
  
Successfully Downloaded the ABS file https://atl-cs-001.litwareinc.com:443/abs/handler/f-1299.lsabs
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

Here are some common reasons why Test-CsAddressBookService might fail: 
  
- You specified an invalid user account. You can verify that a user account exists by running a command similar to this: 
    
  ```
  Get-CsUser "sip:kenmyer@litwareinc.com"
  ```

- The user account is valid, but the account is not currently enabled for Lync Server. To verify that a user account has been enabled for Lync Server, run a command similar to the following: 
    
  ```
  Get-CsUser "sip:kenmyer@litwareinc.com" | Select-Object Enabled
  
  ```

    If the Enabled property is set to False that means that the user is not currently enabled for Lync Server.
    
## See also
<a name="sectionSection3"> </a>

#### 

[Test-CsAddressBookService](test-csaddressbookservice.md)

