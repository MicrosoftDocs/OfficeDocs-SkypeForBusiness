---
title: "Create a site policy for Persistent Chat in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1327ff5c-b859-4010-a240-e0b2b084b5bd
description: "For each site you have deployed, you can create a site-specific Persistent Chat policy."
---

# Create a site policy for Persistent Chat in Lync Server 2013
[]
For each site you have deployed, you can create a site-specific Persistent Chat policy.
  
The configuration in the site policy overrides the global policy, but only for the specific site covered by the site policy.
  
> [!NOTE]
> To configure and use Persistent Chat Server, you must first use Topology Builder to add Persistent Chat Server support to the topology, and then publish the topology. For details, see [Adding Persistent Chat Server to your deployment in Lync Server 2013](adding-persistent-chat-server-to-your-deployment.md) in the Deployment documentation. > To configure Persistent Chat Server configuration settings, see [Configure Persistent Chat Server options globally or for Persistent Chat Server pool in Lync Server 2013](configure-persistent-chat-server-options-globally-or-for-persistent-chat-server.md) in the Deployment documentation. 
  
## To create a Persistent Chat policy for a site

1. From a user account that is assigned to the CsPersistentChatAdministrator, CsAdministrator, or CsUserAdministrator role, log on to any computer in your internal deployment.
    
2. From the **Start** menu, select the Lync Server Control Panel or open a browser window, and then enter the Admin URL. For details about the different methods that you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Persistent Chat**, and then click **Persistent Chat Policy**.
    
    > [!IMPORTANT]
    > You can also use Windows PowerShell cmdlets. For details, see [Configuring Persistent Chat Server by using Windows PowerShell cmdlets](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md) in the Deployment documentation. 
  
4. Click **New**, and then click **Site policy**.
    
5. In **Select a Site**, click the site to which the policy is to be applied.
    
6. In **New Persistent Chat Policy**, do the following:
    
  - In **Name**, specify a name for the new site policy (for example, Redmond).
    
  - In **Description**, provide details about what the site policy is (for example, chat room policy for Redmond).
    
  - To control Persistent Chat for all sites not specifically controlled through a site policy, select or clear the **Enable Persistent Chat** check box. 
    
7. Click **Commit**.
    

