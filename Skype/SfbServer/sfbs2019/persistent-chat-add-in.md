---
title: "Persistent Chat Add-in"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.PersistentChatAddin
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 66124a70-67e8-4bda-9da5-8ab13afccf49
description: "In Lync Server 2013 Control Panel, you can use the Add-in section of the Persistent Chat page to associate URLs with Persistent Chat rooms. These URLs appear in the Lync 2013 client in the chat room in the conversation extensibility pane. An administrator must add Add-ins to the list of registered add-ins, and chat room managers/Creators must associate rooms with one of the registered add-ins before users can see this upgrade in their Lync 2013 client."
---

# Persistent Chat Add-in
[]
In Lync Server 2013 Control Panel, you can use the **Add-in** section of the **Persistent Chat** page to associate URLs with Persistent Chat rooms. These URLs appear in the Lync 2013 client in the chat room in the conversation extensibility pane. An administrator must add Add-ins to the list of registered add-ins, and chat room managers/Creators must associate rooms with one of the registered add-ins before users can see this upgrade in their Lync 2013 client. 
  
Add-ins are used to extend the in-room experience. A typical add-in might include a URL pointing to a Silverlight application that intercepts when a stock ticker is posted to a chat room, and shows the stock history in the extensibility pane. Other examples include embedding a OneNote 2013 URL in the chat room as an add-in to include some shared context, such as "Top of mind" or "Topic of the day."
  
To create Add-ins for Persistent Chat rooms, see [Configure add-ins for rooms in Lync Server 2013](configure-add-ins-for-rooms.md) in the Deployment documentation. If you are a Persistent Chat Administrator, you can create add-ins by using the Lync Server Control Panel or Windows PowerShell cmdlets. 
  
## Tasks that you can perform

You can perform the following tasks on the **Add-in** page: 
  
- [Configure add-ins for rooms in Lync Server 2013](configure-add-ins-for-rooms.md)
    
- [Manage add-ins](manage-add-ins.md)
    
For details about the different procedures that you can perform by using the Lync Server 2013 Control Panel, see [Operations in Lync Server 2013](operations.md).
  
## To configure Add-ins for chat rooms

The following lists describe the menus, command, fields, and properties on the page.
  
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
    
### 

For details about Persistent Chat Server features and capabilities, see [Overview of Persistent Chat Server in Lync Server 2013](overview-of-persistent-chat-server.md) in the Planning documentation. For details about working with Persistent Chat Server configurations, see [Configuring Persistent Chat Server in Lync Server 2013](configuring-persistent-chat-server.md) in the Deployment documentation and [Managing Lync Server 2013, Persistent Chat Server](managing-lync-server-2013-persistent-chat-server.md) in the Operations documentation. 
  

