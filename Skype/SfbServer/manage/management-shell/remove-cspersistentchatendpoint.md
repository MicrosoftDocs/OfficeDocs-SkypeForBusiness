---
title: "Remove-CsPersistentChatEndpoint"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 0211850c-b4e7-4bb2-9a82-bfbfbd7de7b7
description: "Removes an existing Persistent Chat endpoint. A Persistent Chat endpoint is an Active Directory contact object provides a friendly URL for a Skype for Business Server 2015 Persistent Chat pool. This cmdlet was introduced in Lync Server 2013."
---

# Remove-CsPersistentChatEndpoint
 
Removes an existing Persistent Chat endpoint. A Persistent Chat endpoint is an Active Directory contact object provides a friendly URL for a Skype for Business Server 2015 Persistent Chat pool. This cmdlet was introduced in Lync Server 2013.
  
```
Remove-CsPersistentChatEndpoint -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 deletes the Persistent Chat endpoint that has the Identity "sip:pce@litwareinc.com". In this example, the SIP address is used for the Identity
  
```
Remove-CsPersistentChatEndpoint -Identity "sip:pce@litwareinc.com"
```

### Example 2

Example 2 deletes all the Persistent Chat endpoints configured for the pool atl-pcpool-001.litwareinc.com. To carry out this task, the command first uses the **Get-CsPersistentChatEndpoint** cmdlet and the PoolFqdn parameter to return all the endpoints for the pool atl-pcpool-001.litwareinc.com. The endpoints in that collection are then piped to, and removed by, the **Remove-CsPersistentChatEndpoint** cmdlet.
  
```
Get-CsPersistentChatEndpoint -PersistentChatPoolFqdn "atl-pcpool-001.litwareinc.com" | Remove-CsPersistentChatEndpoint
```

### Example 3

The command shown in Example 3 deletes all the Persistent Chat endpoints configured for use in the organization. To do this, the command first calls the **Get-CsPersistentChatEndpoint** cmdlet to return a collection of all the Persistent Chat endpoints. This collection is then piped to the **Remove-CsPersistentChatEndpoint** cmdlet, which deletes each endpoint in the collection.
  
```
Get-CsPersistentChatEndpoint | Remove-CsPersistentChatEndpoint
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
However, if you have users running legacy clients (such as Microsoft Lync 2010 these users might find the default Persistent Chat URIs difficult to work with and difficult to use when pointing their legacy client towards the pool. Because of this, administrators can use the [New-CsPersistentChatEndpoint](new-cspersistentchatendpoint.md) cmdlet to create an additional contact object for the pool, a contact object that provides a friendlier, easier-to-use URI. These endpoints can later be removed by using the **Remove-CsPersistentChatEndpoint** cmdlet.
  
 **Skype for Business Server Control Panel **: The functions carried out by the **Remove-CsPersistentChatEndpoint** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Unique identifier for the Persistent Chat endpoint to be removed. Endpoint Identities are typically specified using the endpoint's SIP address or display name; for example:  <br/>  `-Identity "sip:pcEndpoint1@litwareinc.com"` <br/> However, you can also use the full Identity of the endpoint; for example:  <br/>  `-Identity "CN={33e5014b-dcba-46b5-9bf7-48f4d5fca69d}, CN=Application Contacts,CN=RTC Service,CN=Services,CN=Configuration,DC=litwareinc,DC=com"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Remove-CsPersistentChatEndpoint** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSPersistentChatContact class.
  
## Return Types
<a name="ReturnTypes"> </a>

None. The **Remove-CsPersistentChatEndpoint** cmdlet does not return objects or data.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsPersistentChatEndpoint](get-cspersistentchatendpoint.md)
  
[New-CsPersistentChatEndpoint](new-cspersistentchatendpoint.md)

