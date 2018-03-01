---
title: "Test-CsExStorageConnectivity"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 20fda110-5e09-4453-bb7b-a062abaab87f
description: "Verifies that the Skype for Business Server 2015 Storage Service is working on a Front End Server. This is done by creating a test email message in the specified Exchange mailbox and then optionally deleting that message at the end of the text. Test-CsExStorageConnectivity also verifies that Exchange archiving is working as expected. This cmdlet was introduced in Lync Server 2013."
---

# Test-CsExStorageConnectivity
 
Verifies that the Skype for Business Server 2015 Storage Service is working on a Front End Server. This is done by creating a test email message in the specified Exchange mailbox and then optionally deleting that message at the end of the text. **Test-CsExStorageConnectivity** also verifies that Exchange archiving is working as expected. This cmdlet was introduced in Lync Server 2013.
  
```
Test-CsExStorageConnectivity -SipUri <String> [-Binding <String>] [-DeleteItem <SwitchParameter>] [-Folder <ConversationHistory | Inbox | Dumpster>] [-Force <SwitchParameter>] [-HostNameStorageService <String>] [-UseCache <SwitchParameter>]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 tests to see if the Skype for Business Server 2015 Storage Service can connect to the Exchange mailbox for the user sip:kenmyer@litwareinc.com. In this example, NetNamedPipe is used as the WCF binding.
  
```
Test-CsExStorageConnectivity -SipUri "sip:kenmyer@litwareinc.com" -Binding "NetNamedPipe"
```

### Example 2

Example 2 verifies that the Skype for Business Server 2015 Storage Service can connect to the archiving store on Exchange. (Note that this command will fail if the specified user has not been enabled for Exchange archiving.) In this example, a connection is made to the Dumpster folder: the Recoverable Items purge folder, a folder that stores deleted items and is not visible to end users.
  
```
Test-CsExStorageConnectivity -SipUri "sip:kenmyer@litwareinc.com" -Binding "NetNamedPipe" -Folder Dumpster
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Test-CsExStorageConnectivity** cmdlet is used to verify that server-to-server authentication is working between Skype for Business Server 2015 and Exchange. To verify server-to-server authentication, the cmdlet logs on to Exchange writes an item to the Conversation History folder in the specified mailbox, and then deletes that item.
  
The **Test-CsExStorageConnectivity** cmdlet can also be used to verify that connections can be made to the archiving store on Exchange.
  
If you receive an "Access Denied" error message when running this cmdlet that typically means that you are not a member of the local group RTC Local User Administrators. You can either be added to that group or to the Active Directory group RTCUniversalUserAdmins (which is a member of the RTC Local User Administrators) in order to get the required permissions to run the **Test-CsExStorageConnectivity** cmdlet.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Test-CsExStorageConnectivity** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _SipUri_ <br/> |Required  <br/> |System.String  <br/> |SIP address of the Exchange mailbox where the test item should be created.  <br/> |
| _Binding_ <br/> |Optional  <br/> |System.String  <br/> |Windows Communication Foundation (WCF) binding. A WCF binding determines the transport, encoding, and protocol details required for clients and services to communicate with each other. valid values are:  <br/> NetNamedPipe  <br/> NetTCP  <br/> |
| _DeleteItem_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, the test item will be deleted from the Exchange mailbox at the end of the text.  <br/> |
| _Folder_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Lyss.Cmdlets.ExchFolder  <br/> |Specifies the Exchange archiving folder that the cmdlet should connect to. Allowed values are:  <br/> ConversationHistory  <br/> Inbox  <br/> Dumpster  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _HostNameStorageService_ <br/> |Optional  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the server where the Skype for Business Server 2015 Storage Service is running. This parameter is required if the Binding is set to NetTCP.  <br/> |
| _UseCache_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When presents, instructs the cmdlet to used cached auto discovery results when attempting to connect to Exchange.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The Test-CsExStorageConnectivity cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **Test-CsExStorageConnectivity** cmdlet returns instances of the Microsoft.Rtc.Management.ResourceData object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Test-CsExStorageNotification](test-csexstoragenotification.md)

