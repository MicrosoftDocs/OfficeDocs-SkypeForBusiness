---
title: "Manage chat rooms in Persistent Chat Server in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 1/31/2018
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 7b2e1302-280c-4efe-9ec8-787687b414da
description: "Summary: Learn how to manage Persistent Chat Server chat rooms in Skype for Business Server 2015."
---

# Manage chat rooms in Persistent Chat Server in Skype for Business Server 2015
 
**Summary:** Learn how to manage Persistent Chat Server chat rooms in Skype for Business Server 2015.
  
Creating and managing chat rooms is much easier with the correct use of categories. A category defines who can create or join the chat rooms. Before you attempt to manage chat rooms, be sure to read [Persistent chat categories, chat rooms, and user roles in Skype for Business Server 2015](../../plan-your-deployment/persistent-chat-server/categories-chat-rooms-and-user-roles.md) and [Manage categories in Persistent Chat Server in Skype for Business Server 2015](categories.md).
  
> [!NOTE]
> Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The same functionality is available in Teams. For more information, see [Getting started with your Microsoft Teams upgrade](/microsoftteams/upgrade-start-here). If you need to use Persistent chat, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015. 

You can configure and manage chat rooms by using the Windows PowerShell command-line interface, or by using the Skype for Business client if you are a member of the chat room. This topic describes how to manage chat rooms by using the Windows PowerShell command-line interface. If you want to manage chat rooms by using the Skype for Business client, see the client help. 
  
Chat rooms can be one of two types: Normal and Auditorium. A Normal chat room allows all members to post and read messages. An Auditorium is a type of chat room where only Presenters can post, but everyone can read.
  
Who can access and manage chat rooms depends on user roles as follows:
  
- Users must be Members of a chat room to be able to post and read messages.
    
- Presenters are allowed to post to Auditorium rooms.
    
- Administrators can delete earlier content (for example, content that was posted before a certain date) from any chat room to keep the database from growing too large. Administrators can also remove or replace messages that are considered inappropriate for a particular chat room.
    
- End users, including message authors, cannot delete content from any chat room.
    
- Chat room Managers can make changes to all chat room properties, including disabling rooms. Managers cannot, however, delete a room, or change the category of a room. 
    
- Only Administrators can delete a chat room after it has been created.
    
You can configure and manage chat rooms by using the following Windows PowerShell cmdlets:
  

|**Cmdlet**|**Description**|
|:-----|:-----|
|New-CsPersistentChatRoom  <br/> |Create a new chat room  <br/> |
|Set-CsPersistentChatRoom  <br/> |Configure settings for an existing room; assign users and user groups to the room  <br/> |
|Get-CsPersistentChatRoom  <br/> |Retrieve information about rooms  <br/> |
|Clear-CsPersistentChatRoom  <br/> |Clear a room or messages from a room  <br/> |
|Remove-CsPersistentChatRoom  <br/> |Remove a room  <br/> |
|Remove-CsPersistentChatMessage  <br/> |Remove messages from a room  <br/> |
   
You use the **New-CsPersistentChatRoom** cmdlet to create chat rooms and the **Set-CsPersistentChatRoom** cmdlet to configure an existing chat room, including adding users to the chat room. You can configure the following parameters for chat rooms:
  
- Disabled. Lets you disable or enable a chat room. 
    
- Invitations. Lets you enable or disable chat room invitations, which are used to notify users when they have been added as chat room members. The default setting for invitations in inherit, which caused the chat room to adopt the invitation setting configured on the category it belongs to. Configuring the invitations setting to false at the chat room level allows the category setting to be overridden. 
    
- Privacy. Lets you specify whether a chat room is Open, Closed, or Secret. Open rooms can be searched and accessed by anyone. Closed rooms can be searched by anyone, but can be accessed only by members. Secret rooms can be searched and accessed only by members of the room. By default, each new room is initially configured as Closed.
    
- Type. Lets you specify whether a chat room is a Normal room, which accepts messages posted by any member, or an Auditorium room, which accepts messages posted only by a Presenter.
    
- Addin. Lets you associate a previously configured add-in with a chat room, which allows URL content to be viewed by members while participating.
    
In addition to the above parameters, the **Set-CsPersistentChatRoom** cmdlet lets you assign users to the chat room as follows:
  
- Members. Configures membership for the chat room. You can add or remove either the individual or multiple members using a single cmdlet by specifying the SIP address of the users. To allow users to be added in bulk, Active Directory organizational units or distribution groups can also be specified.
    
- Managers. Lets you assign managers to the chat room. Managers have the permissions to define membership of a chat room along with other settings.
    
- Presenters. Lets you assign presenters to an Auditorium chat room. 
    
  For details about syntax, including all parameters, see [Skype for Business Server 2015 Management Shell](../management-shell.md).
  
## Create a new room

You can create a new room by using the **New-CsPersistentChatRoom** cmdlet. For example, the following command creates a new chat room named ITChatRoom on the pool atl-cs-001.contoso.com. In this example, the chat room is added to the IT category:
  
```
New-CsPersistentChatRoom -Name "ITChatRoom" -PersistentChatPoolFqdn "atl-cs-001.contoso.com"-Category "IT"
```

**Note:** PersistentChatPoolFqdn is not needed if one of the following is true: 
  
- There is only one Persistent Chat Server pool.
    
- You provide a pool FQDN to the category.
    
- You provide a pool FQDN to adding the room.
    
## Configure an existing room

You can configure an existing room by using the **Set-CsPersistentChatRoom** cmdlet. For example, the following command assigns user1 as a Member and Presenter, and user2 as a Manager, of the testCat Auditorium room:
  
```
Set-CsPersistentChatRoom -Identity testCat -Members @{Add="sip:user1@contoso.com", "CN=container,DC=contoso,DC=com"}
Set-CsPersistentChatRoom -Identity testCat -Presenters @{Add="sip:user1@contoso.com"}
Set-CsPersistentChatRoom -Identity testCat -Managers @{Add="sip:user2@contoso.com"}
```

 The next example adds all the users from the NorthAmericaUsers OU in active Directory to the NorthAmerica chat room:
  
```
Set-CsPersistentChatRoom -PersistentChatPoolFqdn "atl-cs-001.contoso.com\NorthAmerica" -Members @{Add="OU=NorthAmericaUsers,DC=contoso,DC=com"}
```

The next example adds all the members from the Finance distribution group to the same chat room:
  
```
Set-CsPersistentChatRoom -PersistentChatPoolFqdn "atl-cs-001.contoso.com\NorthAmerica" -Members @{Add="CN=Finance,OU=ExternalUsers,DC=contoso,DC=com"}
```

## Disable or enable a room

If the topic of a Persistent Chat room is no longer relevant, you can make the chat room unavailable to users by disabling it. When a chat room is disabled, all members are immediately disconnected from the room. After a chat room is disabled, users cannot rejoin it or find it in chat room searches.
  
If the chat room's history persists, the content is preserved when the chat room is disabled. However, that content will not appear in searches during the time that the chat room remains in a disabled state. If you later enable the chat room, users can search for messages that were posted before the chat room was disabled. For information about configuring chat room history, see [Manage categories in Persistent Chat Server in Skype for Business Server 2015](categories.md). 
  
If a chat room is disabled, its membership list and other settings are preserved. As an administrator, you can enable a room that has been disabled, and you do not need to manually re-create the settings.
  
You can disable a room by using the **Set-CsPersistentChatRoom** cmdlet and setting the Disabled parameter to True:
  
```
Set-CsPersistentChatRoom -Identity "atl-cs-001.contoso.com\ITChatRoom" -Disabled $True
```

To enable a chat room, set the Disabled parameter to False:
  
```
Set-CsPersistentChatRoom -Identity "atl-cs-001.contoso.com\ITChatRoom" -Disabled $False
```

## Get information about rooms

To get information about the rooms configured for use in your organization, you can use the **Get-CsPersistentChatRoom** cmdlet.
  
The following command returns information about all the chat rooms configured for use in the organization:
  
```
Get-CsPersistentChatRoom
```

## Remove all content from a room

You can remove content from a room by using the **Clear-CsPersistentChatRoom** cmdlet. For example, the following command removes all the content from the Persistent Chat room ITChatRoom that was added to the room on or before March 1, 2015:
  
```
Clear-CsPersistentChatRoom -Identity "atl-cs-001.contoso.com\ITChatRoom" -EndDate "3/1/2015"
```

## Remove a message from a room

You can remove one or more messages in the Persistent Chat database, and optionally replace the message with a default message or with an administrator-provided message, by using the **Remove-CsPersistentChatMessage** cmdlet. For example, the following command removes all the messages from the ITChatRoom chat room that were posted by the user kenmyer@contoso.com:
  
```
Remove-CsPersistentChatMessage -Identity "atl-persistentchat-001.contoso.com\ITChatRoom" -UserUri "sip:kenmyer@contoso.com"
```

The next example replaces any removed messages with the note that the message is no longer available:
  
```
Remove-CsPersistentChatMessage -Identity "atl-persistentchat-001.contoso.com\ITChatRoom" -UserUri "sip:kenmyer@contoso.com" -ReplaceMessage "This message is no longer available."
```

## Remove a room

You can remove a room by using the **Remove-CsPersistentChatRoom** cmdlet.
  
For example, the following command removes the chat room RedmondChatRoom:
  
```
Remove-CsPersistentChatRoom -Identity "atl-gc-001.contoso.com\RedmondChatRoom"
```

## Move a room from one category to another

If a chat room manager has **Creator** privileges in another category, he or she can move the room from one category to another. The room is not deleted and recreated. It is a change of association within the database.
  
Changing a chat room category should be done rarely and with caution. A category determines the allowed membership for the chat room, so when a chat room is moved to another category, all the system access control lists (SACLs) that are no longer supported by the new category are purged. For example, if a user was a member of the room and is no longer an allowed member in the new category, the room membership will be modified and the user will be removed from the room.
  

