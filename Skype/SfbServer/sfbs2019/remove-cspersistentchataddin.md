---
title: "Remove-CsPersistentChatAddin"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e218e88a-326e-4405-ba58-4d34b41191b4
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsPersistentChatAddin
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Removes an existing Persistent Chat add-in. A Persistent Chat add-in is a customized web page that can be embedded within a Persistent Chat client. This cmdlet was introduced in Lync Server 2013.
  
```
Remove-CsPersistentChatAddin -Identity <String> <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

Example 1 removes the Persistent Chat add-in ITChatAddin found on the pool atl-cs-001.litwareinc.com.
  
```
Remove-CsPersistentChatAddin -Identity "atl-cs-001.litwareinc.com\ITChatAddin"
```

### Example 2

The command shown in Example 2 removes all the Persistent Chat add-ins currently in use in the organization. To do this, the command first uses the **Get-CsPersistentChatAddin** cmdlet to return a collection of all the Persistent Chat add-ins currently in use. This collection is piped to the **Remove-CsPersistentChatAddin** cmdlet, which then deletes each add-in in the collection. 
  
```
Get-CsPersistentChatAddin | Remove-CsPersistentChatAddin
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
Add-ins serve as extensions to a Persistent Chat chat room. Add-ins are external applications (that is, items not built into Persistent Chat itself) that are associated with a particular chat room. For example, a help desk chat room might include a URL that links to a Web page or to a Silverlight application that shows the status of the day's help requests. The Lync Server Windows PowerShell command-line interface cmdlets do not provide the ability to create these add-ins. Instead, the **CsPersistentChatAddin** cmdlets are used to associate (or disassociate) an add-in from a chat room. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsPersistentChatAddin"}
  
 **Lync Server Control Panel:** To remove a Persistent Chat add-in using the Lync Server Control Panel, click **Persistent Chat** and then click **Add-in**. Select the add-in to be removed, click **Edit**, and then click **Delete**.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |System.String  <br/> |Unique identifier for the Persistent Chat add-in to be removed. The Identity is composed of the fully qualified domain name of the Persistent Chat pool where the add-in is located, a "\" character, and the add-in name. For example:  <br/> -Identity "atl-gc-001.litwareincom\ITPersistentChatAddin"  <br/> |
| _Instance_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Chat.Cmdlets.Addin  <br/> |Allows you to pass a reference to an object to the cmdlet.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command; for example, attempting to remove an add-in that is currently associated with one or more chat rooms.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Remove-CsPersistentChatAddin** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.PersistentChat.Cmdlets.AddinObject object. The cmdlet will also accept a string value representing the Identity of an existing add-in. 
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Remove-CsPersistentChatAddin** cmdlet deletes existing instances of the Microsoft.Rtc.Management.PersistentChat.Cmdlets.AddinObject object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsPersistentChatAddin](get-cspersistentchataddin.md)
  
[New-CsPersistentChatAddin](new-cspersistentchataddin.md)
  
[Set-CsPersistentChatAddin](set-cspersistentchataddin.md)

