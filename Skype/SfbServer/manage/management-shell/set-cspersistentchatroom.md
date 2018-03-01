---
title: "Set-CsPersistentChatRoom"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3774931e-74a9-4189-9dde-3baae2293138
description: "Modifies and existing Persistent Chat chat room. A chat room is a discussion forum that typically revolves around a specific topic. This cmdlet was introduced in Lync Server 2013."
---

# Set-CsPersistentChatRoom
 
Modifies and existing Persistent Chat chat room. A chat room is a discussion forum that typically revolves around a specific topic. This cmdlet was introduced in Lync Server 2013.
  
```
Set-CsPersistentChatRoom -Instance <ChatRoom> <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 disables the Persistent Chat chat room with the Identity atl-cs-001.litwareinc.com\ITChatRoom.
  
```
Set-CsPersistentChatRoom -Identity "atl-cs-001.litwareinc.com\ITChatRoom" -Disabled $True
```

### Example 2

In Example 2, all the Persistent Chat chat rooms on the pool atl-cs-001.litwareinc.com are disabled. This task is performed by first using the **Get-CsPersistentChatRoom** cmdlet and the Identity parameter to return all the chat rooms configured for the pool atl-cs-001.litwareinc.com. These chat rooms are then piped to the **Set-CsPersistentChatRoom** cmdlet, which sets the Disabled property of each room to True ($True).
  
```
Get-CsPersistentChatRoom -PersistentChatPoolFqdn "atl-cs-001.litwareinc.com" | Set-CsPersistentChatRoom -Disabled $True
```

### Example 3

Example 3 disables all the Persistent Chat chat rooms in the organization. To do this, the command first calls the **Get-CsPersistentChatRoom** cmdlet without any parameters in order to return a collection of all the Persistent Chat chat rooms. This collection is then piped to the **Set-CsPersistentChatRoom** cmdlet, which disables each room in the collection.
  
```
Get-CsPersistentChatRoom | Set-CsPersistentChatRoom -Disabled $True
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
Persistent Chat discussions take the form of messages posted in individual chat rooms; chat rooms are discussion forums based on specific topics. By design, messages posted in a chat room remain there forever; at any time, users can return to the room and review all the messages that have been previously posted. 
  
The **Set-CsPersistentChatRoom** cmdlet enables you to modify any (or all) of the chat rooms that have been configured for use in your organization. This includes assigning Managers and Presenters to a room.
  
 **Skype for Business Server Control Panel:** To modify an existing Persistent Chat chat room using the Skype for Business Server Control Panel, click **Persistent Chat**, click **Room**, then double-click the chat room to be modified.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |System.String  <br/> |Unique Identifier for the Persistent Chat chat room being modified. The Identity for a chat room consists of the Persistent Chat pool where the room has been configured plus the name of the room; for example:  <br/>  `-Identity "atl-gc-001.litwareinc.com\RedmondChatRoom"` <br/> |
| _Instance_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Chat.Cmdlets.ChatRoom  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _Addin_ <br/> |Optional  <br/> |System.String  <br/> |Name of the Persistent Chat add-in, if any, associated with the chat room. A Persistent Chat add-in is a customized web page that can be embedded within a Persistent Chat client. Add-ins can be created by using the **New-CsPersistentChatAddin** cmdlet. <br/> |
| _AsObject_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, Active Directory display names are used when adding users to or removing users from the Managers or Presenters lists. When not specified, SIP addresses are used when managing these lists.  <br/> |
| _Category_ <br/> |Optional  <br/> |System.String  <br/> |Category under which the room is located; for example:  <br/>  `-Category "IT"` <br/> Note that the specified category must already exist or the command will fail. Categories, which are a collection of chat rooms, can be created by using the **New-CsPersistentChatCategory** cmdlet. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables administrators to provide additional information about the new chat room.  <br/> |
| _Disabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True ($True), the new chat room will be disabled and unavailable for use when it is first created. If this parameter is not used then the new chat room will be enabled and available for immediate use.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _Invitations_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Chat.Cmdlets.ChatRoomInvitations  <br/> |Specifies whether or not invitations for the chat room will be inherited from the category. Among other things, this means that users on the Members list will automatically receive an invitation to join a new chat room at the time that new room is created. If set to False, invitations will not be used for the room. If set to Inherit, the room will use the Invitations setting specified for its Category.  <br/> |
| _Managers_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |List of users allowed to define the membership of the chat room as well as configure other settings for the room.  <br/> To add a new user to the Managers list, use syntax similar to this:  <br/>  `-Managers @{Add="sip:kenmyer@litwareinc.com"}` <br/> Multiple users can be added by separating the user SIP addresses with commas:  <br/>  `-Managers @{Add="sip:kenmyer@litwareinc.com", "sip:pilar@litwareinc.com"}` <br/> To remove a user from the Managers list use the Remove method:  <br/>  `-Managers @{Remove="sip:kenmyer@litwareinc.com"}` <br/> To remove all the users from the Managers list, set the value of the Managers property to null:  <br/>  `-Managers $Null` <br/> In addition to working with individual users you can also work with entire OUs. For example, this command adds all the users in the IT OU to the managers list:  <br/>  `-Managers @{Add="OU=IT,DC=litwareinc,DC=com"}` <br/> To make all the users in a distribution list chat room managers, use the Active Directory distinguished name of that distribution list:  <br/>  `-Managers @{Add="CN=ChatSupportGroup,OU=IT,DC=litwareinc,DC=com"}` <br/> |
| _Members_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |List of users who are allowed to access the chat room. If the Members property is null then the chat room inherits the membership list from its Persistent Chat category.  <br/> To add a new user to the Members list, use syntax similar to this:  <br/>  `-Members @{Add="sip:kenmyer@litwareinc.com"}` <br/> Multiple users can be added by separating the user SIP addresses with commas:  <br/>  `-Members @{Add="sip:kenmyer@litwareinc.com", "sip:pilar@litwareinc.com"}` <br/> To remove a user from the Members list use the Remove method:  <br/>  `-Members @{Remove="sip:kenmyer@litwareinc.com"}` <br/> To remove all the users from the Members list, set the value of the Members property to null:  <br/>  `-Members $Null` <br/> In addition to working with individual users you can also work with entire OUs. For example, this command adds all the users in the IT OU to the Members list:  <br/>  `-Members @{Add="OU=IT,DC=litwareinc,DC=com"}` <br/> To make all the users in a distribution list chat room members, use the Active Directory distinguished name of that distribution list:  <br/>  `-Members @{Add="CN=ChatSupportGroup,OU=IT,DC=litwareinc,DC=com"}` <br/> |
| _Name_ <br/> |Optional  <br/> |System.String  <br/> |Name of the Persistent Chat chat room. Names must be unique per Persistent Chat pool.  <br/> |
| _Presenters_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |List of users who are allowed to post messages in an auditorium chat room.  <br/> To add a new user to the Presenters list, use syntax similar to this:  <br/>  `-Presenters @{Add="sip:kenmyer@litwareinc.com"}` <br/> Multiple users can be added by separating the user SIP addresses with commas:  <br/>  `-Presenters @{Add="sip:kenmyer@litwareinc.com", "sip:pilar@litwareinc.com"}` <br/> To remove a user from the Presenters list use the Remove method:  <br/>  `-Presenters @{Remove="sip:kenmyer@litwareinc.com"}` <br/> To remove all the users from the Presenters list, set the value of the Presenters property to null:  <br/>  `-Presenters $Null` <br/> In addition to working with individual users you can also work with entire OUs. For example, this command adds all the users in the IT OU to the Presenters list:  <br/>  `-Presenters @{Add="OU=IT,DC=litwareinc,DC=com"}` <br/> To make all the users in a distribution list chat room presenters, use the Active Directory distinguished name of that distribution list:  <br/>  `-Presenters @{Add="CN=ChatSupportGroup,OU=IT,DC=litwareinc,DC=com"}` <br/> |
| _Privacy_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Chat.Cmdlets.ChatRoomPrivacy  <br/> |Privacy settings for the chat room. Allowed values are:  <br/> \* Open (any user can locate the chat room by doing a directory search, and anyone can participate in chat room activities)  <br/> \* Secret (only chat room members can locate the room by doing a directory search, and only members can participate in chat room activities)  <br/> \* Closed (any user can locate the chat room by doing a directory search, but only members can participate in chat room activities)  <br/> |
| _Type_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Chat.Cmdlets.ChatRoomType  <br/> |Specifies whether the chat room is configured as a Normal chat room (where all members can post messages) or an Auditorium (where only presenters can post messages). For example:  <br/>  `-Type "Auditorium"` <br/> The default value is Normal.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsPersistentChatRoom** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.PersistentChat.Cmdlets.ChatRoomObject object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Set-CsPersistentChatRoom** cmdlet modifies existing instances of the Microsoft.Rtc.Management.PersistentChat.Cmdlets.ChatRoomObject object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Clear-CsPersistentChatRoom](clear-cspersistentchatroom.md)
  
[Get-CsPersistentChatRoom](get-cspersistentchatroom.md)
  
[New-CsPersistentChatRoom](new-cspersistentchatroom.md)
  
[Remove-CsPersistentChatRoom](remove-cspersistentchatroom.md)

