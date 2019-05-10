---
title: "Manage categories in Persistent Chat Server in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: b0c834b9-b5c8-41d5-865b-c8b180e76d13
description: "Summary: Learn how to manage Persistent Chat Server categories in Skype for Business Server 2015."
---

# Manage categories in Persistent Chat Server in Skype for Business Server 2015
 
**Summary:** Learn how to manage Persistent Chat Server categories in Skype for Business Server 2015.
  
A category is a logical structure for organizing chat rooms. A category defines a default set of access control lists (ACLs) for controlling the users and user groups who can create or join the chat rooms. Chat room categories contain chat rooms, but not other categories. Each category describes its contents with metadata, such as Name and Description. The category has properties that can be set to control the behavior of the chat rooms belonging to it; for example, whether the chat rooms allow Invitations or File Uploads, or contain Chat History. 
  
Creating and managing chat rooms is much easier with the correct use of categories. As a Persistent Chat Server administrator, you can define AllowedMembers and Creators for each category, and also define the default chat room settings and behaviors that will be applied to all chat rooms created in the category. For example, if you set the category's AllowedMembers to contoso.com, you can add any group or user at Contoso as a member to chat rooms in that category. If you set the Allowed Members on a category to Sales, only groups and users in this distribution list can be added as members to chat rooms in that category. The Creators property enables you to control who can create chat rooms in that category. After the chat room is created, anyone from the AllowedMembers group can be designated as a Manager for ongoing management operations on the rooms (for example, membership changes and approval).
  
Defining AllowedMembers and Creators for a category has the following benefits:
  
- All chat rooms in this category are bound by the restrictions set at the category level. You can use this to segregate chat rooms based on business need and access policies.
    
- A user who is in the Creators list can create new chat rooms in that category. If you want to implement a system where a restricted number of personnel in the organization can create chat rooms this control can be used to meet that requirements. 
    
Users, Organization Units (OUs), and user groups that are identified as Creators of the category are the only individuals and groups that are allowed to create rooms in the category. After the category is created, you can choose users, OUs, and user groups from the category's AllowedMembers list as chat room managers and members to manage and participate in the room. 
  
Before you configure categories, be sure to read [Persistent chat categories, chat rooms, and user roles in Skype for Business Server 2015](../../plan-your-deployment/persistent-chat-server/categories-chat-rooms-and-user-roles.md).
  
You can configure and manage categories by using the Control Panel or by using Windows PowerShell cmdlets.

> [!NOTE]
> Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The same functionality is available in Teams. For more information, see [Journey from Skype for Business to Microsoft Teams](/microsoftteams/journey-skypeforbusiness-teams). If you need to use Persistent chat, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015. 
  
## Configure categories by using the Control Panel

1. From a user account that is assigned to the CsPersistentChatAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. From the **Start** menu, select the Skype for Business Server Control Panel or open a browser window, and then enter the Admin URL.
    
3. In the left navigation bar, click **Persistent Chat**, and then click **Category**.
    
    For multiple Persistent Chat Server pool deployments, select the appropriate pool from the drop-down list.
    
4. On the **Category** page, click **New** or **Edit**.
    
5. In **Select a Service**, select the service corresponding to the Persistent Chat Server pool on which the category needs to be created. The service is the Persistent Chat Server pool that the Persistent Chat client uses to identify which pool the category belongs to. A category can belong to only one Persistent Chat Server pool, and cannot be moved to, or shared with, another pool.
    
6. In **New Category**, do the following:
    
   - In **Name**, specify a name for the new room category.
    
   - In **Description**, provide a detailed description for the room category (for example, a room category for Contoso).
    
   - To control whether invitations can be enabled for chat rooms that belong to this category, select or clear the **Enable invitations** check box. If selected, rooms in this category may have invitations on or off; if cleared, the rooms in this category are not allowed to have invitations. If a room has invitations on, when a new member is added to a room, he or she gets a notification of the new room in their Persistent Chat client.
    
   - To control file uploads in chat rooms belonging to this category, select or clear the **Enable file upload** check box. If selected, the rooms of this category can enable or disable file uploads; if cleared, the rooms of this category are not allowed to have file uploads.
    
   - To control chat history, select or clear the **Enable chat history** check box. If selected, room chats become persistent; otherwise, chat messages are not persisted. If compliance is enabled, room chats will be saved in compliance, but users will not be able to access older messages. This option can be used for rooms designated for real-time, ad hoc collaborations that don't need chat history to be persisted.
    
7. In **Edit Category**, do the following:
    
   - In **Membership**, in the **Allowed members** section, add or remove users and other Active Directory Domain Services principals (users, distribution groups, organizational units, and so on) that are permitted to be added as members of chat rooms belonging to the category. Principals permitted by a category can search for the rooms in the category (unless the room is hidden, in which case only members of the room can search for it in the directory).
    
   - In **Membership**, in the **Denied members** section, add or remove users and other Active Directory principals associated with members being denied from the room.
    
   - In **Membership**, in the **Creators** section, add or remove users and other Active Directory principals associated with creators for the category. A creator is a user who has permissions to create chat rooms and assign chat room managers and members.
    
8. Click **Commit**.
    
## Configure categories by using Windows PowerShell

You can configure categories by using the following Windows PowerShell cmdlets:
  

|**Cmdlet**|**Description**|
|:-----|:-----|
|New-CsPersistentChatCategory  <br/> |Create a new category  <br/> |
|Set-CsPersistentChatCategory  <br/> |Configure settings for an existing category  <br/> |
|Get-CsPersistentChatCategory  <br/> |Retrieve information about categories  <br/> |
|Remove-CsPersistentChatCategory  <br/> |Remove a category  <br/> |
   
You can configure the following parameters for categories:
  
- EnableFileUpload. Allows file uploads to the chat rooms in the category.
    
- EnableInvitations. Enables invitations for the category. Users on the AllowedMembers list will automatically receive an invitation to join a new chat room at the time the new room is created.
    
- ChatHistory. Enables or disables the chat history feature.
    
- Creators. Specifies the users who are allowed to create chat rooms within the category.
    
- AllowedMembers. Specifies the users who are allowed to access chat rooms within the category.
    
- DeniedMembers. Lists the users who are not allowed to access chat rooms within the category.
    
For complete information about cmdlet syntax, including all parameters, see [Skype for Business Server 2015 Management Shell](../management-shell.md).
  
### Create a new category

You can create a new category by using the **New-CsPersistentChatCategory** cmdlet. For example, the following command creates a new category named HelpDesk on the pool atl-cs-001.contoso.com. In this example, file upload is enabled:
  
```
New-CsPersistentChatCategory -Name "HelpDesk" -PersistentChatPoolFqdn "atl-cs-001.contoso.com" -EnableFileUpload 
```

### Configure an existing category

You can configure an existing category by using the **Set-CsPersistentCategory** cmdlet.
  
For example, the following command specifies that user1 is an AllowedMember and a Creator, while user2 is denied access to the rooms in the category:
  
```
Set-CsPersistentChatCategory -Identity testCat -AllowedMembers @{Add="sip:user1@contoso.com", "CN=container,DC=contoso,DC=com"}  -DeniedMembers @{Add="sip:user2@contoso.com"}
Set-CsPersistentChatCategory -Identity testCat -Creators @{Add="sip:user1@contoso.com"}
```

### Get information about categories

You can get information about categories by using the **Get-CsPersistentChatCategory** cmdlet. For example, the following command returns information for all the Persistent Chat categories in the organization:
  
```
Get-CsPersistentChatCategory
```

### Remove a category

You can remove a category by using the **Remove-CsPersistentChatCategory** cmdlet. Before removing a category, you must first either delete all chat rooms under it or move the chat rooms to a new category. For example, the following command removes the category that has the Identity "atl-cs-001.contoso.com\helpdesk":
  
```
Remove-CsPersistentChatCategory -Identity "atl-cs-001.contoso.com\helpdesk"
```
