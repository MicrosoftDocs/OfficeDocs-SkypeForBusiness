---
title: "Apply a Persistent Chat policy to a user or user group in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 809ef4e0-8d42-4feb-b7c0-3995f39867a7
description: "If a user has been enabled for Lync Server 2013, you can apply appropriate policies to specific users to enable or disable them for Persistent Chat Server."
---

# Apply a Persistent Chat policy to a user or user group in Lync Server 2013
[]
If a user has been enabled for Lync Server 2013, you can apply appropriate policies to specific users to enable or disable them for Persistent Chat Server.
  
> [!NOTE]
> To configure and use Persistent Chat Server, you must first use Topology Builder to add Persistent Chat Server support to the topology, and then publish the topology. For details, see [Adding Persistent Chat Server to your deployment in Lync Server 2013](adding-persistent-chat-server-to-your-deployment.md) in the Deployment documentation. > To configure Persistent Chat Server configuration settings, see [Configure Persistent Chat Server options globally or for Persistent Chat Server pool in Lync Server 2013](configure-persistent-chat-server-options-globally-or-for-persistent-chat-server.md) in the Deployment documentation. 
  
Use the procedure in this topic to apply a previously created Persistent Chat user policy to one or more user accounts or user groups.
  
## To apply a Persistent Chat user policy to a user account

1. From a user account that is assigned to the CsPersistentChatAdministrator, CsAdministrator, or CsUserAdministrator role, log on to any computer in your internal deployment.
    
2. From the **Start** menu, select the Lync Server Control Panel or open a browser window, and then enter the Admin URL. For details about the different methods that you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Users**, and then search on the user account that you want to configure.
    
4. In the table that lists the search results, click the user account, click **Edit**, and then click **Show details**.
    
5. In **Edit Lync Server User** under **Persistent Chat policy**, select the Persistent Chat user policy that you want to apply.
    
    > [!NOTE]
    > The **\<Automatic\>** settings apply the default effective policy. These settings are applied automatically by the server. 
  
6. Click **Commit**.
    

