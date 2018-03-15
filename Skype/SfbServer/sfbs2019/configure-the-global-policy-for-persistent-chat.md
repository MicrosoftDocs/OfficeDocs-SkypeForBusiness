---
title: "Configure the global policy for Persistent Chat in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6176eb5c-19de-4c07-bcc0-2e38f8965966
description: "You can use the default global policy by itself to enable Persistent Chat settings for all users in your deployment. You can also specify additional policies for sites and users to control whether Persistent Chat is enabled or disabled for specific users and sites."
---

# Configure the global policy for Persistent Chat in Lync Server 2013
[]
You can use the default global policy by itself to enable Persistent Chat settings for all users in your deployment. You can also specify additional policies for sites and users to control whether Persistent Chat is enabled or disabled for specific users and sites.
  
You cannot delete the global policy. If you attempt to delete it, the configuration resets to the default values.
  
> [!NOTE]
> To configure and use Persistent Chat Server, you must first use Topology Builder to add Persistent Chat Server support to the topology, and then publish the topology. For details, see [Adding Persistent Chat Server to your deployment in Lync Server 2013](adding-persistent-chat-server-to-your-deployment.md) in the Deployment documentation. > To configure Persistent Chat Server configuration settings, see [Configure Persistent Chat Server options globally or for Persistent Chat Server pool in Lync Server 2013](configure-persistent-chat-server-options-globally-or-for-persistent-chat-server.md) in the Deployment documentation. 
  
## To configure the Global Policy for Persistent Chat

1. From a user account that is assigned to the CsPersistentChatAdministrator, CsAdministrator, or CsUserAdministrator role, log on to any computer in your internal deployment.
    
2. From the **Start** menu, select the Lync Server Control Panel or open a browser window, and then enter the Admin URL. For details about the different methods that you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md) in the Operations documentation. 
    
    > [!IMPORTANT]
    > You can also use Windows PowerShell cmdlets. For details, see [Configuring Persistent Chat Server by using Windows PowerShell cmdlets](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md) in Deployment documentation. 
  
3. In Lync Server Control Panel, click **Persistent Chat**, and then click **Persistent Chat Policy**.
    
4. Click **Global** in the list of policies, click **Edit**, and then click **Show details**.
    
5. In **Edit Persistent Chat Policy - Global**, do the following:
    
  - In **Name**, specify a new name for the global policy, if you do not want to use the default of Global.
    
  - In **Description**, provide details about what the user policy is (for example, Global policy for  _centralSiteName_).
    
  - To control Persistent Chat for all sites and users not specifically controlled through a site policy or user policy, select or clear the **Enable Persistent Chat** check box. 
    
6. Click **Commit**.
    

