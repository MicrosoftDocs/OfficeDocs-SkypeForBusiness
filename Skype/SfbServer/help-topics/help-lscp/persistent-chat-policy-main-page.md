---
title: "Persistent Chat Policy Main Page"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/27/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.PersistentChatPolicyMain
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 0dc18d5c-82d6-4d39-afb1-efdb3ae6d2c7
description: "You can use the Persistent Chat Policy page of the Persistent Chat group to manage policies at a global, pool, site, or user level, including configuring the default global policy and creating one or more additional user and site policies for your deployment. If a user is enabled for Persistent Chat Server by policy, then the Persistent Chat Server environment appears in their client."
---

# Persistent Chat Policy Main Page
 
You can use the **Persistent Chat Policy** page of the **Persistent Chat** group to manage policies at a global, pool, site, or user level, including configuring the default global policy and creating one or more additional user and site policies for your deployment. If a user is enabled for Persistent Chat Server by policy, then the Persistent Chat Server environment appears in their client.
  
> [!NOTE]
> In the topology, Persistent Chat Server site policies apply globally, per user's pool, or per user's site, or per user. 
  
The global policy is created automatically when you deploy Persistent Chat Server, and it can be configured, but not deleted. Because the global policy applies to all users, it doesn't have to be set per user.
  
You can create and configure multiple site and user policies which, together with the global policy, enable users for Persistent Chat Server. Pool and site Persistent Chat Server policies override the global Persistent Chat Server policy, but only for users of that site. User policies override both global, pool, and site policies for the users to whom the user policy is assigned.
  
> [!NOTE]
> To configure and use Persistent Chat Server, you must first use Topology Builder to add Persistent Chat Server support to the topology, and then publish the topology. For details, see [Add Persistent Chat Server to your Skype for Business Server 2015 topology](../../deploy/deploy-persistent-chat-server/add-persistent-chat-server.md). 
  
## Tasks that you can perform

You can perform the following tasks on the **Persistent Chat Policy** page: enable and manage Persistent Chat Server policy.
  
## To configure the Global Policy for Persistent Chat

1. From a user account that is assigned to the CsPersistentChatAdministrator, CsAdministrator, or CsUserAdministrator role, log on to any computer in your internal deployment.
    
2. From the **Start** menu, select the Skype for Business Server Control Panel or open a browser window, and then enter the Admin URL.
    
3. In Skype for Business Server Control Panel, click **Persistent Chat**, and then click **Persistent Chat Policy**.
    
4. Click **Global** in the list of policies, click **Edit**, and then click **Show details**.
    
5. In **Edit Persistent Chat Policy - Global**, do the following:
    
   - In **Name**, specify a new name for the global policy, if you do not want to use the default of Global.
    
   - In **Description**, provide details about what the user policy is (for example, Global policy for  _centralSiteName_).
    
   - To control Persistent Chat for all sites and users not specifically controlled through a site policy or user policy, select or clear the **Enable Persistent Chat** check box.
    
6. Click **Commit**.
    
## To create a Persistent Chat policy for a site

For each site you have deployed, you can create a site-specific Persistent Chat policy.
  
The configuration in the site policy overrides the global policy, but only for the specific site covered by the site policy.
  
1. From a user account that is assigned to the CsPersistentChatAdministrator, CsAdministrator, or CsUserAdministrator role, log on to any computer in your internal deployment.
    
2. From the **Start** menu, select the Skype for Business Server Control Panel or open a browser window, and then enter the Admin URL.
    
3. In the left navigation bar, click **Persistent Chat**, and then click **Persistent Chat Policy**.
    
4. Click **New**, and then click **Site policy**.
    
5. In **Select a Site**, click the site to which the policy is to be applied.
    
6. In **New Persistent Chat Policy**, do the following:
    
   - In **Name**, specify a name for the new site policy (for example, Redmond).
    
   - In **Description**, provide details about what the site policy is (for example, chat room policy for Redmond).
    
   - To control Persistent Chat for all sites not specifically controlled through a site policy, select or clear the **Enable Persistent Chat** check box.
    
7. Click **Commit**.
    
## To create a user policy for Persistent Chat

In the Skype for Business Server Control Panel, you define user policies that can be assigned to users in **Users**.
  
The user policy overrides the global policy and site policies, but only for the specific users who are assigned the user policy.
  
1. From a user account that is assigned to the CsPersistentChatAdministrator, CsAdministrator, or CsUserAdministrator role, log on to any computer in your internal deployment.
    
2. From the **Start** menu, select the Skype for Business Server Control Panel or open a browser window, and then enter the Admin URL.
    
3. In the left navigation bar, click **Persistent Chat**, and then click **Persistent Chat Policy**.
    
4. Click **New**, and then click **User policy**.
    
5. In **New Persistent Chat Policy**, do the following:
    
   - In **Name**, specify a name for the new user policy.
    
   - In **Description**, provide details about what the user policy is (for example, Persistent Chat policy for specific user).
    
   - To control Persistent Chat for all users who are not specifically controlled through a user policy, select or clear the **Enable Persistent Chat** check box.
    
6. Click **Commit**.
    
## To apply a Persistent Chat user policy to a user account

If a user has been enabled for Skype for Business, you can apply appropriate policies to specific users to enable or disable them for Persistent Chat Server.
  
Use the procedure in this topic to apply a previously created Persistent Chat user policy to one or more user accounts or user groups.
  
1. From a user account that is assigned to the CsPersistentChatAdministrator, CsAdministrator, or CsUserAdministrator role, log on to any computer in your internal deployment.
    
2. From the **Start** menu, select the Skype for Business Server Control Panel or open a browser window, and then enter the Admin URL.
    
3. In the left navigation bar, click **Users**, and then search on the user account that you want to configure.
    
4. In the table that lists the search results, click the user account, click **Edit**, and then click **Show details**.
    
5. In **Edit Lync Server User** under **Persistent Chat policy**, select the Persistent Chat user policy that you want to apply.
    
    > [!NOTE]
    > The **\<Automatic\>** settings apply the default effective policy. These settings are applied automatically by the server.
  
6. Click **Commit**.
    

