---
title: "Configure Persistent Chat Server options globally or for Persistent Chat Server pool in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1e8d5245-cd58-4aad-9a1c-35b24189bc40
description: "In Lync Server 2013 Control Panel, you can use the Persistent Chat Configuration section of the Persistent Chat page to configure Persistent Chat settings globally where it applies to all Persistent Chat Server pools, or for a specific Persistent Chat Server pool."
---

# Configure Persistent Chat Server options globally or for Persistent Chat Server pool in Lync Server 2013
[]
In Lync Server 2013 Control Panel, you can use the **Persistent Chat Configuration** section of the **Persistent Chat** page to configure Persistent Chat settings globally where it applies to all Persistent Chat Server pools, or for a specific Persistent Chat Server pool. 
  
> [!NOTE]
> To configure and use Persistent Chat Server, you must first use Topology Builder to add Persistent Chat Server support to the topology, and then publish the topology. For details, see [Adding Persistent Chat Server to your deployment in Lync Server 2013](adding-persistent-chat-server-to-your-deployment.md) in the Deployment documentation. 
  
## To configure Persistent Chat options globally

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
    
  - In **Room management URL**, select the room management URL. This is the URL for a web-based room management deployment. If you don't need to customize room management, and you simply use the default setting, leave this option blank.
    
    If you want to customize your room creation experience and include your specific business workflow, you can build a custom room management solution by using the Persistent Chat Server Software Development Kit (SDK), host it somewhere, and put the URL here. This URL is sent down to the client so that when a user tries to view/create a room, he or she is directed to your custom room management solution.
    
7. Click **Commit**.
    

