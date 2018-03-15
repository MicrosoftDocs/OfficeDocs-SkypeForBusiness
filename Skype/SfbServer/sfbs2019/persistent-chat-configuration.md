---
title: "Persistent Chat Configuration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.PersistentChatConfig
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3f2891e6-bad3-4a23-a345-b7de4cae3bd9
description: "In this articleTasks that you can performTo configure Persistent Chat options globallyTo configure Persistent Chat options for a specific Persistent Chat Server pool"
---

# Persistent Chat Configuration
[]
 **In this article**
  
[Tasks that you can perform](#sectionSection0)
  
[To configure Persistent Chat options globally](#sectionSection1)
  
[To configure Persistent Chat options for a specific Persistent Chat Server pool](#sectionSection2)
  
Your Persistent Chat Server deployment can host many concurrent Persistent Chat rooms. Chat rooms can be organized into a set of categories on the server. Each chat room belongs to one category, and inherits some settings from that category. This organization creates a useful structure for identifying conversations, based on their business purpose, and facilitates delegated administration and simplified management.
  
> [!NOTE]
> Although many of the management features of chat rooms are available in computers running Persistent Chat (Lync client) for the user, Persistent Chat Administrators (in the **cspersistentchatadministrator** role) must use the Lync Server Control Panel or Windows PowerShell cmdlets to create or manage categories. 
  
Persistent Chat Administrators use Lync Server Control Panel or Windows PowerShell cmdlets to create and manage categories, and to design access for chat rooms for the users in their organization.
  
Persistent Chat room managers, who have the ability to manage one or more chat rooms, can use the Lync client to launch a room management Web application to create and manage rooms (or customers can create custom solutions and workflows to be invoked). Persistent Chat
  
Persistent Chat administrators can also use Lync Server Control Panel or Windows PowerShell cmdlets to create and manage rooms.
  
Chat room managers can make changes to all chat room properties, except for changing the category of the room. They cannot be restricted from performing the following actions:
  
- Disabling a chat room
    
- Changing a chat room name
    
- Changing a chat room description
    
- Changing a chat room type (Auditorium versus Normal)
    
- Changing the privacy of a room (open versus closed versus secret)
    
- Adding or removing members
    
- Adding or removing chat room managers
    
- Adding or removing an add-in
    
- Changing settings such as invitations (according to what's permitted by the category)
    
## Tasks that you can perform
<a name="sectionSection0"> </a>

You can perform the following tasks on the **Persistent Chat Configuration** page: 
  
- [Configure Persistent Chat Server options globally or for Persistent Chat Server pool in Lync Server 2013](configure-persistent-chat-server-options-globally-or-for-persistent-chat-server.md)
    
For details about the different procedures that you can perform by using the Lync Server 2013 Control Panel, see [Operations in Lync Server 2013](operations.md).
  
## To configure Persistent Chat options globally
<a name="sectionSection1"> </a>

1. From a user account that is assigned to the CsPersistentChatAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. From the **Start** menu, select the Lync Server Control Panel or open a browser window, and then enter the Admin URL. For details about the different methods that you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
    > [!IMPORTANT]
    > You can also use Windows PowerShell cmdlets. For details, see [Configuring Persistent Chat Server by using Windows PowerShell cmdlets](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md) in the Deployment documentation. 
  
3. In the left navigation bar, click **Persistent Chat**, and then click **Persistent Chat Configuration**.
    
4. On the **Persistent Chat Configuration** page, click **New,** and then click **Site configuration**.
    
    > [!IMPORTANT]
    > Choose this option if you want the configuration to be applied to all Persistent Chat Server pools deployed in the site. Click **Pool Configuration** if you want the configuration to be applied to a specific Persistent Chat Server pool. 
  
5. In **Select a Site**, select the site to be configured for the Persistent Chat Server site configuration.
    
6. In **New Persistent Chat Configuration**, do the following:
    
  - In **Name**, specify a name for the new configuration settings. By default, the site name already exists.
    
  - In **Default chat history**, define the number of chat messages that will be processed for each room upon first request. By default, the number is 30. This is the global default, and administrators can disable chat history per category.
    
    > [!IMPORTANT]
    > Persistent Chat Server will cache these messages in memory, so if you increase this number, more messages will be cached. You can always access historical content by search. The default number simply determines the maximum number of messages that you initially see when connecting to a chat room. 
  
  - In **Maximum file size (KB)**, select the maximum file size of each chat history. By default, the number is 20 MB (20,000 KB). This is the maximum size for a file that can be uploaded to any chat room in the system (for which file uploads are enabled by its corresponding **Category** setting). 
    
    > [!IMPORTANT]
    > This setting is enforced on the server because custom applications or previous Group Chat clients using Office Communications Server 2007 R2 Group Chat Server or Lync Server 2010, Group Chat can post files to a room. The Lync 2013 client does not have file upload/download capability, so if you have a pure Lync 2013 deployment or Lync 2013 client, it is not possible to post files in a Persistent Chat Server chat room. 
  
  - In **Participant update limit**, select the limit for participant updates. Persistent Chat Server sends roster information (who is connected to a chat room) to all participants until the number of connected users reaches this number. By default, the number is 75. This limit indicates the maximum number of participants in a given room beyond which Persistent Chat Server stops sending roster updates to connected clients about who is present in the room.
    
  - (Optional.) In **Room management URL**, select the room management URL. This is the URL for a web-based custom room management. If you don't need to customize room management, and you simply use the default setting, leave this option blank. After the URL is set, it is applied as both the internal and external room management URL.
    
    If you want to customize your room creation experience and include your specific business workflow, you can build a custom room management solution by using the Persistent Chat Server Software Development Kit (SDK), host it somewhere, and put the URL here. This URL is sent down to the client, so that when a user tries to view or create a room, he or she is directed to your custom room management solution.
    
7. Click **Commit**.
    
## To configure Persistent Chat options for a specific Persistent Chat Server pool
<a name="sectionSection2"> </a>

1. From a user account that is assigned to the CsPersistentChatAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. From the **Start** menu, select the Lync Server Control Panel, or open a browser window, and then enter the Admin URL. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
    > [!IMPORTANT]
    > You can also use Windows PowerShell cmdlets. For details, see [Configuring Persistent Chat Server by using Windows PowerShell cmdlets](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md) in the Deployment documentation. 
  
3. In the left navigation bar, click **Persistent Chat**, and then click **Persistent Chat Configuration**.
    
4. On the **Persistent Chat Configuration** page, click **New**, and then click **Pool configuration**.
    
5. In **Select a Service**, select the service associated with the Persistent Chat Server pool to be configured.
    
6. In **New Persistent Chat Configuration**, do the following:
    
  - In **Name**, specify a name for the new configuration settings. By default, the site pool name already exists.
    
  - In **Default chat history**, define the number of chat messages that will be processed for each room upon first request. By default, the number is 30. This is the global default, and administrators can disable chat history per category.
    
    > [!IMPORTANT]
    > Persistent Chat Server will cache these messages in memory, so if you increase this number, more messages will be cached. You can always access historical content by search. The default number simply determines the maximum number of messages that you initially see when connecting to a chat room. 
  
  - In **Maximum file size (KB)**, select the maximum file size of each chat history. By default, the number is 20 MB (20,000 KB). This is the maximum size for a file that can be uploaded to any chat room in the system (for which file uploads are enabled by its corresponding **Category** setting). 
    
    > [!IMPORTANT]
    > This setting is enforced on the server because custom applications or previous Group Chat clients (Office Communications Server 2007 R2 Group Chat Server or Lync Server 2010, Group Chat) can post files to a room. The Lync 2013 client does not have file upload/download capability, so if you have a pure Lync 2013 deployment or Lync 2013 client, it is not possible to post files in a Persistent Chat Server chat room. 
  
  - In **Participant update limit**, select the limit for participant updates. Persistent Chat Server sends roster information (who is connected to a chat room) to all participants until the number of connected users reaches this number. By default, the number is 75. This limit indicates the maximum number of participants in a given room beyond which Persistent Chat Server stops sending roster updates to connected clients about who is present in the room.
    
  - (Optional) In **Room management URL**, select the room management URL. This is the URL for a web-based room management deployment. If you don't need to customize room management, and you simply use the default setting, leave this option blank.
    
    If you want to customize your room creation experience and include your specific business workflow, you can build a custom room management solution by using the Persistent Chat Server Software Development Kit (SDK), host it somewhere, and put the URL here. This URL is sent down to the client, so that when a user tries to view/create a room, he or she is directed to your custom room management solution.
    
7. Click **Commit**.
    
### 

For details about Persistent Chat Server features and capabilities, see [Overview of Persistent Chat Server in Lync Server 2013](overview-of-persistent-chat-server.md) in the Planning documentation. For details about working with Persistent Chat Server configurations, see [Configuring Persistent Chat Server in Lync Server 2013](configuring-persistent-chat-server.md) in the Deployment documentation and [Managing Lync Server 2013, Persistent Chat Server](managing-lync-server-2013-persistent-chat-server.md) in the Operations documentation. 
  

