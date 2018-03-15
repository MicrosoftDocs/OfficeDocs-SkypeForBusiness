---
title: "Test-CsExStorageNotification"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d8fe3b22-7a76-4d70-9bc1-b54b37f68449
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Test-CsExStorageNotification
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Verifies that the Lync Server Storage Service running on a Front End server can subscribe to the Microsoft Exchange Server 2013 mailbox notification service. This is done by having the cmdlet subscribe to the service, create an item, verify that notification of the new item is received, and then, optionally, delete that item unsubscribe from the service. This cmdlet was introduced in Lync Server 2013.
  
```
Test-CsExStorageNotification -SipUri <String> [-Binding <String>] [-DeleteItem <SwitchParameter>] [-Force <SwitchParameter>] [-HostNameStorageService <String>]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 tests to see if the Lync Server Storage Service can connect to the Exchange Server mailbox notification service for the user sip:kenmyer@litwareinc.com. In this example, NetNamedPipe is used as the WCF binding.
  
```
Test-CsExStorageNotification -SipUri "sip:kenmyer@litwareinc.com" -Binding "NetNamedPipe"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Test-CsExStorageNotification** cmdlet is used to verify that the Microsoft Exchange Server 2013 notification service is able to notify Lync Server 2013 any time updates are made to a user's Contact List. This cmdlet is valid only if you are using the unified contact store. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsExStorageNotification"}
  
 **Lync Server Control Panel:** The functions carried out by the **Test-CsExStorageNotification** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _SipUri_ <br/> |Required  <br/> |System.String  <br/> |SIP address of the Exchange Server mailbox where the test item should be created.  <br/> |
| _Binding_ <br/> |Optional  <br/> |System.String  <br/> |Windows Communication Foundation (WCF) binding. A WCF binding determines the transport, encoding, and protocol details required for clients and services to communicate with each other. valid values are:  <br/> \* NetNamedPipe  <br/> \* NetTCP  <br/> |
| _DeleteItem_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, the test item will be deleted from the Exchange mailbox at the end of the text.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _HostNameStorageService_ <br/> |Optional  <br/> |System.String  <br/> |Fully qualified domain name of the server where the Lync Server Storage Service is running. This parameter is required if the Binding is set to NetTCP.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Test-CsExStorageNotification** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

The **Test-CsExStorageNotification** cmdlet returns instances of the Microsoft.Rtc.Management.ResourceData object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Test-CsExStorageConnectivity](test-csexstorageconnectivity.md)

