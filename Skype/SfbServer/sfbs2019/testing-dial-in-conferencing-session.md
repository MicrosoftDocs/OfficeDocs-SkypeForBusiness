---
title: "Testing dial-in conferencing session in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6c505be5-5af7-450c-b3ca-10d9122bee5c

description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Testing dial-in conferencing session in Lync Server 2013
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
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsDialInConferencing cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsDialInConferencing"}```|
   
## Description
<a name="sectionSection0"> </a>

The Test-CsDialInConferencing cmdlet verifies whether a user can participate in a dial-in conference. Test-CsDialInConferencing works by trying to log a test user onto the system. If the logon succeeds, the cmdlet will then use the user's credentials and permissions to try all of the available dial-in conferencing access numbers. The success or failure of each dial-in try will be noted, then the test user will be logged off from Lync Server.Test-CsDialInConferencing only verifies that the appropriate connections can be made. The cmdlet does not actually make any phone calls or create any dial-in conferences that other users can join.
  
## Running the test
<a name="sectionSection1"> </a>

The Test-CsDialInConferencing cmdlet can be run using either a preconfigured test account (see Setting Up Test Accounts for Running Lync Server Tests) or the account of any user who is enabled for Lync Server. To run this check using a test account, you just have to specify the FQDN of the Lync Server pool being tested. For example: 
  
```
Test-CsDialInConferencing -TargetFqdn "atl-cs-001.litwareinc.com" 
```

To run this check using an actual user account, you must create a Windows PowerShell credentials object that contains the account name and password. You must then include that credentials object and the account SIP address the calling Test-CsDialInConferencing: 
  
```
$credential = Get-Credential "litwareinc\kenmyer"
Test-CsDialInConferencing -TargetFqdn atl-cs-001.litwareinc.com" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential
```

For more information, see the Help documentation for the [Test-CsDialInConferencing](test-csdialinconferencing.md) cmdlet. 
  
## Determining success or failure
<a name="sectionSection2"> </a>

If the specified user can log on to Lync Server and then make a connection using one of the available dial-in conferencing access numbers, then you'll receive output similar to this, with the Result property marked as **Success:**
  
TargetFqdn : atl-cs-001.litwareinc.com
  
Result : Success
  
Latency : 00:00:06.8630376
  
Error :
  
Diagnosis :
  
If the specified user can't make this connection, then the Result will be shown as Failure, and additional information will be recorded in the Error and Diagnosis properties:
  
TargetFqdn : atl-cs-001.litwareinc.com
  
Result : Failure
  
Latency : 00:00:00
  
Error : The log on was denied. Check that the proper credentials are
  
 being used and the account is active. 
  
 Inner Exception:NegotiateSecurityAssociation failed, error: - 
  
 2146893044 
  
Diagnosis :
  
The previous output indicates that the test user was denied access to Lync Server itself. This typically means that the user credentials passed to Test-CsDialInConferencing were not valid. In turn, you should re-create the Windows PowerShell credentials object. Although you can retrieve the password for the user account, you can verify the SIP address by using a command similar to this:
  
```
Get-CsUser -Identity "sip:kenmyer@litwareinc.com" | Select-Object SipAddress
```

## Reasons why the test might have failed
<a name="sectionSection3"> </a>

Here are some common reasons why Test-CsDialInConferencing might fail:
  
- You specified a user account that is not valid. You can verify that a user account exists by running a command similar to this: 
    
  ```
  Get-CsUser "sip:kenmyer@litwareinc.com"
  ```

- The user account is valid, but the account is currently not enabled for Lync Server. To verify that a user account is enabled for Lync Server, run a command similar to the following: 
    
  ```
  Get-CsUser "sip:kenmyer@litwareinc.com" | Select-Object Enabled
  ```

    If the Enabled property is set to False, that means that the user is currently not enabled for Lync Server.
    
- You might have an incorrect dial-in conferencing access number. You can return your currently-configured list of dial-in conferencing access numbers by using this command: 
    
  ```
  Get-CsDialConferencingAccessNumber
  ```

