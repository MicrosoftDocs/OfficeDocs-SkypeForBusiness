---
title: "Configure Persistent Chat Server options in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/28/2016
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 19ced8de-8867-4152-b38a-891f3bc2a5ea
description: "Summary: Learn how to configure Persistent Chat Server options at the global, site, or pool level in Skype for Business Server 2015."
---

# Configure Persistent Chat Server options in Skype for Business Server 2015
 
**Summary:** Learn how to configure Persistent Chat Server options at the global, site, or pool level in Skype for Business Server 2015.
  
You can specify several options for Persistent Chat Server that can be applied globally, to all pools within a site, or to a specific pool within a site. Persistent Chat server options include the following: 
  
- Default Chat History. The number of chat messages that are available for each chat room upon first request. The global default is 30 chat messages. 
    
- Maximum File Size. The maximum size of a file that can be uploaded to or downloaded from a room. The global default is 20MB.
    
- Participant Update Limit. The maximum number of participants in a given chat room for which Persistent Chat will send roster updates. The global default is 75.
    
- Room Management URL. The URL used for custom chat room management. The setting allows the use of a custom room management solution. 
   
> [!NOTE] 
> Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The same functionality is available in Teams. For more information, see [Journey from Skype for Business to Microsoft Teams](/microsoftteams/journey-skypeforbusiness-teams). If you need to use Persistent chat, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015.
 
## Configure Persistent Chat Server global options

To configure Persistent Chat Server global options:
  
1. From a user account that is assigned to the CsPersistentChatAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. From the **Start** menu, select the Skype for Business Server Control Panel or open a browser window, and then enter the Admin URL.
    
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
    
   - In **Participant update limit**, select the limit for participant updates. Persistent Chat Server sends roster information (who is connected to a chat room) to all participants until the number of connected users reaches this number. By default, the number is 75. This limit indicates the maximum number of participants in a given room beyond which Persistent Chat Server stops sending roster updates to connected clients about who is present in the room.
    
   - (Optional.) In **Room management URL**, select the room management URL. This is the URL for a web-based custom room management. If you don't need to customize room management, and you simply use the default setting, leave this option blank. After the URL is set, it is applied as both the internal and external room management URL.
    
     If you want to customize your room creation experience and include your specific business workflow, you can build a custom room management solution by using the Persistent Chat Server Software Development Kit (SDK), host it somewhere, and put the URL here. This URL is sent down to the client, so that when a user tries to view or create a room, he or she is directed to your custom room management solution.
    
7. Click **Commit**.
    
## Configure options for a specific Persistent Chat Server pool

To configure options for a specific Persistent Chat Server pool.
  
1. From a user account that is assigned to the CsPersistentChatAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. From the **Start** menu, select the Skype for Business Server Control Panel, or open a browser window, and then enter the Admin URL.
    
3. In the left navigation bar, click **Persistent Chat**, and then click **Persistent Chat Configuration**.
    
4. On the **Persistent Chat Configuration** page, click **New**, and then click **Pool configuration**.
    
5. In **Select a Service**, select the service associated with the Persistent Chat Server pool to be configured.
    
6. In **New Persistent Chat Configuration**, do the following:
    
   - In **Name**, specify a name for the new configuration settings. By default, the site pool name already exists.
    
   - In **Default chat history**, define the number of chat messages that will be processed for each room upon first request. By default, the number is 30. This is the global default, and administrators can disable chat history per category.
    
     > [!IMPORTANT]
     > Persistent Chat Server will cache these messages in memory, so if you increase this number, more messages will be cached. You can always access historical content by search. The default number simply determines the maximum number of messages that you initially see when connecting to a chat room. 
  
   - In **Maximum file size (KB)**, select the maximum file size of each chat history. By default, the number is 20 MB (20,000 KB). This is the maximum size for a file that can be uploaded to any chat room in the system (for which file uploads are enabled by its corresponding **Category** setting).
    
   - In **Participant update limit**, select the limit for participant updates. Persistent Chat Server sends roster information (who is connected to a chat room) to all participants until the number of connected users reaches this number. By default, the number is 75. This limit indicates the maximum number of participants in a given room beyond which Persistent Chat Server stops sending roster updates to connected clients about who is present in the room.
    
   - In **Room management URL**, select the room management URL. This is the URL for a web-based room management deployment. If you don't need to customize room management, and you simply use the default setting, leave this option blank.
    
     If you want to customize your room creation experience and include your specific business workflow, you can build a custom room management solution by using the Persistent Chat Server Software Development Kit (SDK), host it somewhere, and put the URL here. This URL is sent down to the client so that when a user tries to view/create a room, he or she is directed to your custom room management solution.
    
7. Click **Commit**.
    

