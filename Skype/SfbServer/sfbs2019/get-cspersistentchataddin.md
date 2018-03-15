---
title: "Get-CsPersistentChatAddin"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0d6b3283-c73d-4b83-b0f8-8f03aa4bba14
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsPersistentChatAddin
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Returns information about all the Persistent Chat add-ins configured for use in the organization. A Persistent Chat add-in is a customized web page that can be embedded within a Persistent Chat client. This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsPersistentChatAddin [-PersistentChatPoolFqdn <String>] <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

Example 1 returns information about all the Persistent Chat add-ins configured for use in the organization.
  
```
Get-CsPersistentChatAddin
```

### Example 2

In Example 2, information is returned for a specific Persistent Chat add-in: the add-in with the Identity atl-cs-001.litwareinc.com\ITPersistentChatAddin.
  
```
Get-CsPersistentChatAddin -Identity "atl-cs-001.litwareinc.com\ITPersistentChatAddin"
```

### Example 3

Example 3 returns information for all the Persistent Chat add-ins configured for use on the pool atl-cs-001.litwareinc.com.
  
```
Get-CsPersistentChatAddin -PersistentChatPoolFqdn "atl-cs-001.litwareinc.com"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
Add-ins serve as extensions to a Persistent Chat chat room. Add-ins are external applications (that is, items not built into Persistent Chat itself) that are associated with a particular chat room. For example, a help desk chat room might include a URL that links to a Web page or to a Silverlight application that shows the status of the day's help requests. The Lync Server Windows PowerShell command-line interface cmdlets do not provide the ability to create these add-ins. Instead, the **CsPersistentChatAddin** cmdlets are used to associate (or disassociate) an add-in from a chat room. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsPersistentChatAddin"}
  
 **Lync Server Control Panel:** To view Persistent Chat add-in information in Lync Server Control Panel, click **Persistent Chat** and then click **Add-in**.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |System.String  <br/> |Unique identifier for the Persistent Chat add-in to be returned. The Identity is composed of the fully qualified domain name of the Persistent Chat pool where the add-in is located, a "\" character, and the add-in name. For example:  <br/> -Identity "atl-gc-001.litwareincom\ITPersistentChatAddin"  <br/> If this parameter is not specified then the **Get-CsPersistentChatAddin** cmdlet returns information about all your Persistent Chat add-ins.  <br/> |
| _PersistentChatPoolFqdn_ <br/> |Optional  <br/> |System.String  <br/> |Fully qualified domain name for the Persistent Chat pool. If this parameter is used then only Persistent Chat add-ins found on the specified pool will be returned. If this parameter is not used then the **Get-CsPersistentChatAddin** cmdlet will return add-ins from all your Persistent Chat pools. For example:  <br/> -PoolFqdn "atl-cs-001.litwareinc.com"  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsPersistentChatAddin** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsPersistentChatAddin** cmdlet returns instances of the Microsoft.Rtc.Management.PersistentChat.Cmdlets.AddinObject object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[New-CsPersistentChatAddin](new-cspersistentchataddin.md)
  
[Remove-CsPersistentChatAddin](remove-cspersistentchataddin.md)
  
[Set-CsPersistentChatAddin](set-cspersistentchataddin.md)

