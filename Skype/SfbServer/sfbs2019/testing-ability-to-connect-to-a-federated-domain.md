---
title: "Testing ability to connect to a federated domain from Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d8ccfade-ef54-47a4-9f87-36213a635ce5

description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Testing ability to connect to a federated domain from Lync Server 2013
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
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsFederatedPartner cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsFederatedPartner"}```|
   
## Description
<a name="sectionSection0"> </a>

Test-CsFederatedPartner verifies your ability to connect to the domain of a federated partner. To verify the connectivity to a domain, that domain must be listed in the collection of allowed (federated) domains. You can retrieve a list of the domains on your allowed domains list by using this command:
  
```
Get-CsAllowedDomain
```

For more information, see the Help documentation for the [Test-CsFederatedPartner](test-csfederatedpartner.md) cmdlet. 
  
## Running the test
<a name="sectionSection1"> </a>

The Test-FederatedPartner cmdlet requires two pieces of information: the FQDN of your Edge Server and the FQDN of the federated partner. For example, this command tests the ability to connect to the domain contoso.com: 
  
```
Test-CsFederatedPartner -TargetFqdn "atl-edge-001.litwareinc.com" -Domain "contoso.com"
```

This command enables you to test the connections to all the domains currently on your allowed domains list: 
  
```
Get-CsAllowedDomain | ForEach-Object {Test-CsFederatedPartner -TargetFqdn "atl-edge-001.litwareinc.com" -Domain $_.Identity}
```

For more information, see the Help documentation for the [Test-CsFederatedPartner](test-csfederatedpartner.md) cmdlet. 
  
## Determining success or failure
<a name="sectionSection2"> </a>

If the specified domain can be contacted, you'll receive output similar to this with the Result property marked as **Success:**
  
TargetFqdn : atl-cs-001.litwareinc.com
  
Result : Success
  
Latency : 00:00:00
  
Error : 
  
Diagnosis :
  
If the specified domain cannot be contacted, then the Result will be shown as Failure, and additional information will be recorded in the Error and Diagnosis properties:
  
TargetFqdn : atl-cs-001.litwareinc.com
  
Result : Failure
  
Latency : 00:00:00
  
Error : 504, Server time-out
  
Diagnosis : ErrorCode=2, Source=atl-cs-001.litwareinc.com,Reason=See
  
 response code and reason phrase. 
  
 Microsoft.Rtc.Signaling.DiagnosticHeader 
  
For example, the previous output states that the test failed because of a server time-out error. This typically indicates either network connectivity problems or problems contacting the Edge Server. 
  
If Test-CsFederatedPartner fails, then you might want to rerun the test, this time including the Verbose parameter: 
  
```
Test-CsFederatedPartner -TargetFqdn "atl-edge-001.litwareinc.com" -Domain "contoso.com" -Verbose
```

## Reasons why the test might have failed
<a name="sectionSection3"> </a>

Here are some common reasons why Test-CsFederatedPartner might fail:
  
- The Edge Server might not be available. You can the FQDNs of your Edge Servers by using this command: 
    
  ```
  Get-CsService -EdgeServer | Select-Object PoolFqdn
  ```

    You can then ping each Edge Server to verify that it can be accessed over the network. For example: 
    
  ```
  ping atl-edge-001.litwareinc.com
  ```

- The specified domain might not be listed on the allowed domains list. To verify the domains that were added to the allowed domains list, use this command: 
    
  ```
  Get-CsAllowedDomain
  ```

    If you'd like to see a list of domains that users were blocked from communicating with, then use this command: 
    
  ```
  Get-CsBlockedDomain
  ```

