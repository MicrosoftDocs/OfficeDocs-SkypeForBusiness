---
title: "New-CsPersistentChatEndpoint"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3a3a7acc-3239-4140-8005-ef72ab2f61e1
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsPersistentChatEndpoint
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Creates a new Persistent Chat endpoint. A Persistent Chat endpoint is an Active Directory contact object provides a friendly URL for a Lync Server 2013 Persistent Chat pool. This cmdlet was introduced in Lync Server 2013.
  
```
New-CsPersistentChatEndpoint -PersistentChatPoolFqdn <Fqdn> -SipAddress <String> [-Confirm [<SwitchParameter>]] [-DisplayName <String>] [-PassThru <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 creates a new Persistent Chat endpoint for the pool atl-pcpool-001.litwareinc.com. This new endpoint has the SIP address "sip:pce@litwareinc.com" and the display name of "Persistent Chat Endpoint 1".
  
```
New-CsPersistentChatEndpoint -SipAddress "sip:pce@litwareinc.com" -PersistentChatPoolFqdn "atl-pcpool-001.litwareinc.com" -DisplayName "Persistent Chat Endpoint 1"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
However, if you have users running legacy clients (such as Microsoft Lync 2010 these users might find the default Persistent Chat URIs difficult to work with and difficult to use when pointing their legacy client towards the pool. Because of this, administrators can use the **New-CsPersistentChatEndpoint** cmdlet to create an additional contact object for the pool, a contact object that provides a friendlier, easier-to-use URI. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsPersistentChatEndpoint"}
  
 **Lync Server Control Panel:** The functions carried out by the **New-CsPersistentChatEndpoint** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _PersistentChatPoolFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the Persistent Chat pool that the new endpoint will be associated with. For example:  <br/> -PersistentChatPoolFqdn "atl-pc-001.litwareinc.com"  <br/> |
| _SipAddress_ <br/> |Required  <br/> |System.String  <br/> |Unique identifier that allows the endpoint to communicate with SIP devices such as Lync 2013. The SIP address must use the sip: prefix as well as a valid SIP domain; for example:  <br/> -SipAddress "sip:pcEndpoint1@litwareinc.com"  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DisplayName_ <br/> |Optional  <br/> |System.String  <br/> |Active Directory display name for the new contact object.  <br/> |
| _PassThru_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Enables you to pass a contact object through the pipeline that represents the new Persistent Chat endpoint. By default, the **New-CsPersistentChatEndpoint** cmdlet does not pass objects through the pipeline.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **New-CsPersistentChatEndpoint** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

The **New-CsPersistentChatEndpoint** cmdlet creates new instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSPersistentChatContact class. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsPersistentChatEndpoint](get-cspersistentchatendpoint.md)
  
[Remove-CsPersistentChatEndpoint](remove-cspersistentchatendpoint.md)

