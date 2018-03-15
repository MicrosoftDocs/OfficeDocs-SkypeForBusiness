---
title: "Configure add-ins for rooms in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4eeaf19e-8369-4f6f-af65-a283cf7daa1c
description: "In Lync Server 2013 Control Panel, you can use the Add-in section of the Persistent Chat page to associate URLs with Persistent Chat rooms. These URLs appear in the Lync 2013 client in the chat room in the conversation extensibility pane. An administrator must add Add-ins to the list of registered add-ins, and chat room managers/Creators have to associate rooms with one of the registered add-ins before users can see this upgrade in their Lync 2013 client."
---

# Configure add-ins for rooms in Lync Server 2013
[]
In Lync Server 2013 Control Panel, you can use the **Add-in** section of the **Persistent Chat** page to associate URLs with Persistent Chat rooms. These URLs appear in the Lync 2013 client in the chat room in the conversation extensibility pane. An administrator must add Add-ins to the list of registered add-ins, and chat room managers/Creators have to associate rooms with one of the registered add-ins before users can see this upgrade in their Lync 2013 client. 
  
Add-ins are used to extend the in-room experience. A typical add-in might include a URL pointing to a Silverlight application that intercepts when a stock ticker is posted to a chat room, and shows the stock history in the extensibility pane. Other examples include embedding a OneNote 2013 URL in the chat room as an add-in to include some shared context, such as "Top of mind" or "Topic of the day."
  
## To configure Add-ins for chat rooms

1. From a user account that is assigned to the CsPersistentChatAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. From the **Start** menu, select the Lync Server Control Panel or open a browser window, and then enter the Admin URL. For details about the different methods that you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
    > [!IMPORTANT]
    > You can also use Windows PowerShell cmdlets. For details, see [Configuring Persistent Chat Server by using Windows PowerShell cmdlets](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md) in the Deployment documentation. 
  
3. In the left navigation bar, click **Persistent Chat**, and then click **Add-in**.
    
    For multiple Persistent Chat Server pool deployments, select the appropriate pool from the drop-down list.
    
4. On the **Add-in** page, click **New**.
    
5. In **Select a Service**, select the service corresponding to the Persistent Chat Server pool where you need to create the Add-in. Add-ins cannot be moved from one pool to another or shared between different pools.
    
6. In **New Add-in**, do the following:
    
  - In **Name**, specify a name for the new add-in.
    
  - In **URL**, specify the URL to be associated with the add-in. URLs are limited to http and https protocols.
    
7. Click **Commit**.
    
## See also

#### 

[Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md)
#### 

[Configuring Persistent Chat Server by using Windows PowerShell cmdlets](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md)

