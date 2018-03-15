---
title: "Testing Exchange to Lync notifications in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ed2d6325-3cf5-4450-9951-03092bcb0a7c

description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Testing Exchange to Lync notifications in Lync Server 2013
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
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the **Test-CsExStorageNotification** cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsExStorageNotification"}```|
   
## Description
<a name="sectionSection0"> </a>

The **Test-CsExStorageNotification** cmdlet is used to verify that the Microsoft Exchange Server 2013 notification service can notify Lync Server 2013 any time updates are made to a user's Contact List. This cmdlet is valid only if you are using the unified contact store. 
  
## Running the test
<a name="sectionSection1"> </a>

The command shown in Example 1 tests to see whether the Lync Server Storage Service can connect to the Microsoft Exchange Server mailbox notification service for the user sip:kenmyer@litwareinc.com. In this example, NetNamedPipe is used as the WCF binding.
  
```
Test-CsExStorageNotification -SipUri "sip:kenmyer@litwareinc.com" -Binding "NetNamedPipe"
```

## Determining success or failure
<a name="sectionSection2"> </a>

If Exchange integration is configured correctly , you'll receive output similar to this, with the Result property marked as **Success**:
  
Target Fqdn : atl-cs-001.litwareinc.com
  
Result : Success
  
Latency : 00:00:00
  
Error Message :
  
Diagnosis :
  
If the specified user can't receive notifications, the Result will be shown as Failure, and additional information will be recorded in the Error and Diagnosis properties:
  
Target Fqdn : atl-cs-001.litwareinc.com
  
Result : Failure
  
Latency : 00:00:00
  
Error Message : 10060, A connection attempt failed because the connected party
  
 did not properly respond after a period of time, or 
  
 established connection failed because connected host has 
  
 failed to respond 10.188.116.96:5061 
  
 Inner Exception:A connection attempt failed because the 
  
 connected party did not properly respond after a period of 
  
 time, or established connection failed because connected host 
  
 has failed to respond 10.188.116.96:5061 
  
Diagnosis :
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

Here are some common reasons why **Test-CsExStorageNotification** might fail: 
  
- An incorrect parameter value was supplied. If used, the optional parameters must be configured correctly or the test will fail. Rerun the command without the optional parameters and see whether that succeeds. 
    
- This command will fail if the Microsoft Exchange Server is misconfigured or not yet deployed. 
    
## See also
<a name="sectionSection3"> </a>

#### 

[Test-CsExStorageConnectivity](test-csexstorageconnectivity.md)

