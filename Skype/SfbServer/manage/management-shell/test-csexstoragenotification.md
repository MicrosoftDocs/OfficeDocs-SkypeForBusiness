---
title: "Test-CsExStorageNotification"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: d8fe3b22-7a76-4d70-9bc1-b54b37f68449
description: "Verifies that the Skype for Business Server 2015 Storage Service running on a Front End server can subscribe to the Exchange mailbox notification service. This is done by having the cmdlet subscribe to the service, create an item, verify that notification of the new item is received, and then, optionally, delete that item unsubscribe from the service. This cmdlet was introduced in Lync Server 2013."
---

# Test-CsExStorageNotification
 
Verifies that the Skype for Business Server 2015 Storage Service running on a Front End server can subscribe to the Exchange mailbox notification service. This is done by having the cmdlet subscribe to the service, create an item, verify that notification of the new item is received, and then, optionally, delete that item unsubscribe from the service. This cmdlet was introduced in Lync Server 2013.
  
```
Test-CsExStorageNotification -SipUri <String> [-Binding <String>] [-DeleteItem <SwitchParameter>] [-Force <SwitchParameter>] [-HostNameStorageService <String>]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 tests to see if the Skype for Business Server 2015 Storage Service can connect to the Exchange Server mailbox notification service for the user sip:kenmyer@litwareinc.com. In this example, NetNamedPipe is used as the WCF binding.
  
```
Test-CsExStorageNotification -SipUri "sip:kenmyer@litwareinc.com" -Binding "NetNamedPipe"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Test-CsExStorageNotification** cmdlet is used to verify that the Exchange notification service is able to notify Skype for Business Server 2015 any time updates are made to a user's Contact List. This cmdlet is valid only if you are using the unified contact store.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Test-CsExStorageNotification** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _SipUri_ <br/> |Required  <br/> |System.String  <br/> |SIP address of the Exchange Server mailbox where the test item should be created.  <br/> |
| _Binding_ <br/> |Optional  <br/> |System.String  <br/> |Windows Communication Foundation (WCF) binding. A WCF binding determines the transport, encoding, and protocol details required for clients and services to communicate with each other. valid values are:  <br/> \* NetNamedPipe  <br/> \* NetTCP  <br/> |
| _DeleteItem_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, the test item will be deleted from the Exchange mailbox at the end of the text.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _HostNameStorageService_ <br/> |Optional  <br/> |System.String  <br/> |Fully qualified domain name of the server where the Skype for Business Server 2015 Storage Service is running. This parameter is required if the Binding is set to NetTCP.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
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

