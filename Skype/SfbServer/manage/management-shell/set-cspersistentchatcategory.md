---
title: "Set-CsPersistentChatCategory"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 61f44b61-c1bb-46a8-af12-8d1c543fcda5
description: "Modifies an existing Persistent Chat category. A Persistent Chat category represents a collection of Persistent Chat chat rooms. Each chat room must be associated with a category. This cmdlet was introduced in Lync Server 2013."
---

# Set-CsPersistentChatCategory
[]
Modifies an existing Persistent Chat category. A Persistent Chat category represents a collection of Persistent Chat chat rooms. Each chat room must be associated with a category. This cmdlet was introduced in Lync Server 2013.
  
```
Set-CsPersistentChatCategory -Instance <Category> <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

In Example 1, file uploads are disabled for the Persistent Chat category atl-cs-001.litwareinc.com\helpdesk.
  
```
Set-CsPersistentChatCategory -Identity "atl-cs-001.litwareinc.com\helpdesk" -FileUpload $False
```

### Example 2

Example 2 disables file uploads for all the Persistent Chat categories currently in use in the organization. To carry out this task, the command first calls the **Get-CsPersistentChatCategory** cmdlet without any parameters in order to return a collection of all the Persistent Chat categories. The categories in this collection are then piped to the **Set-CsPersistentChatCategory** cmdlet to disable file uploads for each category.
  
```
Get-CsPersistentChatCategory | Set-CsPersistentChatCategory -FileUpload $False
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
Persistent Chat categories provide a way for administrators to organize, and manage, Persistent Chat chat rooms. Categories provide a way for administrators to group related chat rooms; for example, all chat rooms used by the finance department can be grouped in the same category. Likewise, categories provide a way for administrators to manage permissions to these rooms, dictating which users are allowed access to the rooms, which users are denied access to the rooms, and which users are allowed to create new chat rooms within the category.
  
Note that all chat rooms must belong to a category; you cannot create a chat room without assigning that room to a category. That means that you must create at least one category before you can add any chat rooms to your Persistent Chat implementation.
  
 **Skype for Business Server Control Panel:** To modify an existing Persistent Chat category using the Skype for Business Server Control Panel, click **Persistent Chat**, click **Category**, then double-click the category to be modified.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |System.String  <br/> |Unique identifier for the chat room category. The Identity consists of the Persistent Chat pool were the category is located followed by the category Name; for example:  <br/>  `-Identity "atl-gc-001.litwareinc.com\ITChat"` <br/> |
| _Instance_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Chat.Cmdlets.Category  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _AllowedMembers_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Lists the users who are allowed to access chat rooms within the category. To add a new user to the Members list, use syntax similar to this:  <br/>  `-Members @{Add="sip:kenmyer@litwareinc.com"}` <br/> Multiple users can be added by separating the user SIP addresses with commas:  <br/>  `-Members @{Add="sip:kenmyer@litwareinc.com", "sip:pilar@litwareinc.com"}` <br/> To remove a user from the Members list use the Remove method:  <br/>  `-Members @{Remove="sip:kenmyer@litwareinc.com"}` <br/> To remove all the users from the Members list, set the value of the Members property to null:  <br/>  `-AllowedMembers $Null` <br/> In addition to working with individual users you can also work with entire OUs. For example, this command enables all the users in the IT OU to access chat rooms:  <br/>  `-Members @{Add="OU=IT,DC=litwareinc,DC=com"}` <br/> To add all the users in a distribution list, use the Active Directory distinguished name of that distribution list:  <br/>  `-Members @{Add="CN=ChatSupportGroup,OU=IT,DC=litwareinc,DC=com"}` <br/> |
| _AsObject_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, Active Directory display names are used when adding users to or removing users from the AllowedMembers, DeniedMembers, and Creators lists. When not specified, SIP addresses are used when managing these lists.  <br/> |
| _ChatHistory_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set the False ($False), the chat history feature will be disabled for the new category. Typically, chat history is only disabled for chat rooms that are used for announcements that are posted once and then never need to be referred to again.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Creators_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Lists the users who are allowed to create chat rooms within the category. To add a new user to the Creators list, use syntax similar to this:  <br/>  `-Creators @{Add="sip:kenmyer@litwareinc.com"}` <br/> Multiple users can be added by separating the user SIP addresses with commas:  <br/>  `-Creators @{Add="sip:kenmyer@litwareinc.com", "sip:pilar@litwareinc.com"}` <br/> To remove a user from the Creators list use the Remove method:  <br/>  `-Creators @{Remove="sip:kenmyer@litwareinc.com"}` <br/> To remove all the users from the Creators list, set the value of the Creators property to null:  <br/>  `-Creators $Null` <br/> In addition to working with individual users you can also work with entire OUs. For example, this command enables all the users in the IT OU to create chat rooms:  <br/>  `-Creators @{Add="OU=IT,DC=litwareinc,DC=com"}` <br/> To add all the users in a distribution list, use the Active Directory distinguished name of that distribution list:  <br/>  `-Creators @{Add="CN=ChatSupportGroup.OU=IT,DC=litwareinc,DC=com"}` <br/> |
| _DeniedMembers_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Lists the users who are not allowed to access chat rooms within the category. To add a new user to the DeniedMembers list, use syntax similar to this:  <br/>  `-DeniedMembers @{Add="sip:kenmyer@litwareinc.com"}` <br/> Multiple users can be added by separating the user SIP addresses with commas:  <br/>  `-DeniedMembers @{Add="sip:kenmyer@litwareinc.com", "sip:pilar@litwareinc.com"}` <br/> To remove a user from the DeniedMembers list use the Remove method:  <br/>  `-DeniedMembers @{Remove="sip:kenmyer@litwareinc.com"}` <br/> To remove all the users from the DeniedMembers list, set the value of the DeniedMembers property to null:  <br/>  `-DeniedMembers $Null` <br/> In addition to working with individual users you can also work with entire OUs. For example, this command denies chat room access to all the users in the IT OUs:  <br/>  `-DeniedMembers @{Add="OU=IT,DC=litwareinc,DC=com"}` <br/> To deny access to all the users in a distribution list, use the Active Directory distinguished name of that distribution list:  <br/>  `-DeniedMembers @{Add="CN=ChatSupportGroup.OU=IT,DC=litwareinc,DC=com"}` <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Additional text accompanying the Persistent Chat category. For example, the Description might explain the purpose of the category and what type of rooms you can expect to find within the category.  <br/> |
| _FileUpload_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True ($True), allows file uploads to the chat rooms in the category.  <br/> |
| _Invitations_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to False ($False), Invitations will be enabled for the category. Among other things, this means that users on the AllowedMembers list will automatically receive an invitation to join a new chat room at the time that new room is created.  <br/> |
| _Name_ <br/> |Optional  <br/> |System.String  <br/> |Name given to the Persistent Chat category. Names must be unique per Persistent Chat pool.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsPersistentChatCategory** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.PersistentChat.Cmdlets.CategoryObject object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsPersistentChatCategory** cmdlet modifies existing instances of the Microsoft.Rtc.Management.PersistentChat.Cmdlets.CategoryObject object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsPersistentChatCategory](get-cspersistentchatcategory.md)
  
[New-CsPersistentChatCategory](new-cspersistentchatcategory.md)
  
[Remove-CsPersistentChatCategory](remove-cspersistentchatcategory.md)

