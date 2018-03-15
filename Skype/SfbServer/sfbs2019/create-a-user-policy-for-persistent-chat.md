---
title: "Create a user policy for Persistent Chat in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: aa3774af-d442-4206-8a68-2fbb9102e9d6
description: "In the Lync Server Control Panel, you define user policies that can be assigned to users in Users."
---

# Create a user policy for Persistent Chat in Lync Server 2013
[]
In the Lync Server Control Panel, you define user policies that can be assigned to users in **Users**.
  
The user policy overrides the global policy and site policies, but only for the specific users who are assigned the user policy.
  
> [!NOTE]
> To configure and use Persistent Chat Server, you must first use Topology Builder to add Persistent Chat Server support to the topology, and then publish the topology. For details, see [Adding Persistent Chat Server to your deployment in Lync Server 2013](adding-persistent-chat-server-to-your-deployment.md) in the Deployment documentation. > To configure Persistent Chat Server configuration settings, see [Configure Persistent Chat Server options globally or for Persistent Chat Server pool in Lync Server 2013](configure-persistent-chat-server-options-globally-or-for-persistent-chat-server.md) in the Deployment documentation. 
  
## To create a user policy for Persistent Chat

1. From a user account that is assigned to the CsPersistentChatAdministrator, CsAdministrator, or CsUserAdministrator role, log on to any computer in your internal deployment.
    
2. From the **Start** menu, select the Lync Server Control Panel or open a browser window, and then enter the Admin URL. For details about the different methods that you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
    > [!IMPORTANT]
    > You can also use Windows PowerShell cmdlets. See [Configuring Persistent Chat Server by using Windows PowerShell cmdlets](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md) in the Deployment documentation. 
  
3. In the left navigation bar, click **Persistent Chat**, and then click **Persistent Chat Policy**.
    
4. Click **New**, and then click **User policy**.
    
5. In **New Persistent Chat Policy**, do the following:
    
  - In **Name**, specify a name for the new user policy.
    
  - In **Description**, provide details about what the user policy is (for example, Persistent Chat policy for specific user).
    
  - To control Persistent Chat for all users who are not specifically controlled through a user policy, select or clear the **Enable Persistent Chat** check box. 
    
6. Click **Commit**.
    

