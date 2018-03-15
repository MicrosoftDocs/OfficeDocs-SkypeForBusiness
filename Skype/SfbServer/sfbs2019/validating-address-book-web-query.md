---
title: "Validating address book web query in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e6ae0a5a-e131-4cfe-9a33-6e611831072d

description: "In this articleDescriptionRunning the testDetermining success or failureReasons Why the Test Might Have Failed"
---

# Validating address book web query in Lync Server 2013
[]
 **In this article**
  
[Description](#sectionSection0)
  
[Running the test](#sectionSection1)
  
[Determining success or failure](#sectionSection2)
  
[Reasons Why the Test Might Have Failed](#sectionSection3)
  
****

|||
|:-----|:-----|
|Verification schedule  <br/> |Daily  <br/> |
|Testing tool  <br/> |Windows PowerShell  <br/> |
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsAddressBookWebQuery cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsAddressBookWebQuery"}```|
   
## Description
<a name="sectionSection0"> </a>

The Test-CsAddressBookWebQuery cmdlet enables administrators to verify that users can use the Address Book Web Query service to search for a specific contact. When you run the cmdlet, Test-CsAddressBookWebQuery will first connect to the Web Ticket service to be authenticated. If authentication is successful, the cmdlet will then connect to the Address Book Web Query service and search for the specified contact. If that contact is found, the cmdlet will attempt to return that information to the local computer. The test will be marked a success only if all those steps can be completed.
  
For more information, see the Help documentation for the [Test-CsAddressBookWebQuery](test-csaddressbookwebquery.md) cmdlet. 
  
## Running the test
<a name="sectionSection1"> </a>

The Test-CsAddressBookWebQuery cmdlet can be run using either a preconfigured test account (see Setting Up Test Accounts for Running Lync Server Tests) or the account of any user who is enabled for Lync Server. To run this check using a test account, you just have to specify the FQDN of the Lync Server pool and the SIP address of the user acting as the target of the search. For example: 
  
```
Test-CsAddressBookWebQuery -TargetFqdn "atl-cs-001.litwareinc.com" -TargetSipAddress "sip:davidlongmire@litwareinc.com"
```

To run this check using an actual user account, you must create a Windows PowerShell credentials object that contains a valid user name and password. You must then include that credentials object and the SIP address assigned to the account when the code calls Test-CsAddressBookWebQuery: 
  
```
$credential = Get-Credential "litwareinc\kenmyer"
Test-CsAddressBookWebQuery -TargetFqdn "atl-cs-001.litwareinc.com" -TargetSipAddress "sip:davidlongmire@litwareinc.com" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential
```

For more information, see the Help documentation for the [Test-CsAddressBookWebQuery](https://technet.microsoft.com/en-us/library/gg398773%28v=ocs.14%29.aspx) cmdlet. 
  
## Determining success or failure
<a name="sectionSection2"> </a>

If the specified user can connect to the Address Book Service and retrieve the targeted user address, you'll return output similar to this with the Result property marked as Success:
  
TargetUri : https://atl-cs-001.litwareinc.com:443/groupexpansion/service.svc
  
TargetFqdn : atl-cs-001.litwareinc.com
  
Result : Success
  
Latency : 00:00:06.2611356
  
Error :
  
Diagnosis :
  
If the specified user can't connect or if the target user address cannot be retrieved, then the Result will be shown as Failure, and additional information will be recorded in the Error and Diagnosis properties:
  
TargetUri : https://atl-cs-001.litwareinc.com:443/groupexpansion/service.svc
  
TargetFqdn : atl-cs-001.litwareinc.com
  
Result : Failure
  
Latency : 00:00:00
  
Error : Address Book Web service request has failed with response code
  
 NoEntryFound. 
  
Diagnosis :
  
The previous output states that the test failed because the target user couldn't be found. You can determine whether or not a valid SIP address was passed to Test-CsAddressBookWebQuery by running a command similar to the following:
  
```
Get-CsUser | Where-Object {$_.SipAddress -eq "sip:davidlongmire@litwareinc.com"
```

If Test-CsAddressBookWebQuery fails, then you might want to rerun the test, this time including the Verbose parameter:
  
```
Test-CsAddressBookWebQuery -TargetFqdn "atl-cs-001.litwareinc.com" -TargetSipAddress "sip:davidlongmire@litwareinc.com" -Verbose
```

When the Verbose parameter is included, Test-CsAddressBookWebQuery will return a step-by-step account of each action it tried while checking the ability of the specified user to log on to Lync Server. For example, this output indicates that Test-CsAddressBookWebQuery was able to connect to the Address Book Service, but was not able to locate the target SIP address:
  
'QueryAddressBookWebService' activity started.
  
Calling Address Book Web Query Service. ABWS URL =
  
https://atl-cs-001.litwareinc.com:443/groupexpansion/service.svc
  
Address book query exception : Address Book Web service request has failed with response code NoEntryFound.
  
## Reasons Why the Test Might Have Failed
<a name="sectionSection3"> </a>

Here are some common reasons why Test-CsAddressBookWebQuery might fail:
  
- You specified an invalid user account. You can verify that a user account exists by running a command similar to this:
    
  ```
  Get-CsUser "sip:kenmyer@litwareinc.com"
  ```

- The user account is valid, but the account is not currently enabled for Lync Server. To verify that a user account has been enabled for Lync Server, run a command similar to the following:
    
  ```
  Get-CsUser "sip:kenmyer@litwareinc.com" | Select-Object Enabled
  ```

    If the Enabled property is set to False that means that the user is not currently enabled for Lync Server.
    
- The target user might not be in the Address Book.
    
- The Address Book might not have fully updated and replicated. You can force an update of all the Address Book Servers in your organization by running the following command: 
    
  ```
  Update-CsAddressBook
  
  ```

