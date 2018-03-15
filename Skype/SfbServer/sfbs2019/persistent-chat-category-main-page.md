---
title: "Persistent Chat Category Main Page"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.PersistentChatCategoryMain
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b71c6e6f-681c-4230-954d-3e95ab64ca00
description: "In Lync Server 2013 Control Panel, you can use the Category section of the Persistent Chat page to configure categories. A Persistent Chat room category is a logical structure for organizing chat rooms. A category defines a default set of access control lists (ACLs) for controlling the users and user groups who may create or join the chat rooms. You can use categories enforce ethical walls between different subdivisions within their organizations."
---

# Persistent Chat Category Main Page
[]
In Lync Server 2013 Control Panel, you can use the **Category** section of the **Persistent Chat** page to configure categories. A Persistent Chat room category is a logical structure for organizing chat rooms. A category defines a default set of access control lists (ACLs) for controlling the users and user groups who may create or join the chat rooms. You can use categories enforce ethical walls between different subdivisions within their organizations. 
  
Chat room categories may contain chat rooms, but not other categories. Each category describes its contents with metadata, such as  _Name_ and  _Description_. In addition, the category has properties which can be set to control the behavior of the chat rooms belonging to it, such as if the chat rooms allow  _Invitations_ or  _File Uploads_, or contain  _Chat History_.
  
To create a new category, see [Configure categories in Lync Server 2013](configure-categories.md) in the Deployment documentation. If you are a Persistent Chat Administrator, you can create categories by using the Lync Server Control Panel or Windows PowerShell cmdlets. 
  
## Tasks that you can perform

You can perform the following tasks on the **Category** page: 
  
- [Creating or editing a new category in Lync Server 2013](creating-or-editing-a-new-category.md)
    
- [Moving a chat room from one category to another in Lync Server 2013](moving-a-chat-room-from-one-category-to-another.md)
    
- [Deleting a chat room or category in Lync Server 2013](deleting-a-chat-room-or-category.md)
    
For details about the different procedures that you can perform by using the Lync Server 2013 Control Panel, see [Operations in Lync Server 2013](operations.md).
  
## To configure categories for Persistent Chat rooms

1. From a user account that is assigned to the CsPersistentChatAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. From the **Start** menu, select the Lync Server Control Panel or open a browser window, and then enter the Admin URL. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
    > [!IMPORTANT]
    > You can also use Windows PowerShell cmdlets. For details, see [Configuring Persistent Chat Server by using Windows PowerShell cmdlets](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md) in the Deployment documentation. 
  
3. In the left navigation bar, click **Persistent Chat**, and then click **Category**.
    
    For multiple Persistent Chat Server pool deployments, select the appropriate pool from the drop-down list.
    
4. On the **Category** page, click **New** or **Edit**.
    
5. In **Select a Service**, select the service corresponding to the Persistent Chat Server pool on which the category needs to be created. The service is the Persistent Chat Server pool that the Persistent Chat (client) uses to identify which pool the category belongs to. A category can belong to only one Persistent Chat Server pool, and cannot be moved to another one, or shared with another pool.
    
6. In **New Category**, do the following:
    
1. In **Name**, specify a name for the new room category.
    
2. In **Description**, provide a detailed description for the room category (for example, a room category for Contoso).
    
3. To control whether invitations can be enabled for chat rooms that belong to this category, select or clear the **Enable invitations** check box. If selected, rooms in this category may have invitations on or off; if cleared, the rooms in this category are not allowed to have invitations. If a room has invitations on, when a new member is added to a room, he or she gets a notification of the new room in their Persistent Chat client. 
    
4. To control file uploads in chat rooms belonging to this category, select or clear the **Enable file upload** check box. If selected, the rooms of this category can enable or disable file uploads; if cleared, the rooms of this category are not allowed to have file uploads. 
    
    > [!IMPORTANT]
    > This setting is enforced on the server because custom applications or previous Group Chat clients that use Office Communications Server 2007 R2 Group Chat Server or Lync Server 2010, Group Chat can post files to a room. The Lync 2013 client does not have file upload/download capability, so if you have a pure Lync 2013 deployment or Lync 2013 client, it is not possible to post files in a Persistent Chat Server chat room. 
  
5. To control chat history, select or clear the **Enable chat history** check box. If selected, room chats become persistent; otherwise, chat messages are not persisted. If compliance is enabled, room chats will be saved in compliance, but users will not be able to access older messages. This option can be used for rooms designated for real-time, ad hoc collaborations that don't need chat history to be persisted. 
    
7. In **Edit Category**, do the following:
    
  - In **Membership**, in the **Allowed members** section, add or remove users and other Active Directory Domain Services principals (users, distribution groups, organizational units, and so on) that are permitted to be added as members of chat rooms belonging to the category. Principals permitted by a category can search for the rooms in the category (unless the room is hidden, in which case only members of the room can search for it in the directory). 
    
  - In **Membership**, in the **Denied members** section, add or remove users and other Active Directory principals associated with members being denied from the room. 
    
  - In **Membership**, in the **Creators** section, add or remove users and other Active Directory principals associated with creators for the category. A creator is a user who has permissions to create chat rooms and assign chat room managers and members. 
    
8. Click **Commit**.
    
### 

For details about Persistent Chat Server features and capabilities, see [Overview of Persistent Chat Server in Lync Server 2013](overview-of-persistent-chat-server.md) in the Planning documentation. For details about working with Persistent Chat Server configurations, see [Configuring Persistent Chat Server in Lync Server 2013](configuring-persistent-chat-server.md) in the Deployment documentation and [Managing Lync Server 2013, Persistent Chat Server](managing-lync-server-2013-persistent-chat-server.md) in the Operations documentation. 
  

