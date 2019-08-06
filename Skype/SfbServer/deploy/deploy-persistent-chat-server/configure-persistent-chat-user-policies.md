---
title: "Configure Persistent Chat user policies in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/28/2016
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e5862480-95f8-4d76-a2b5-940cd995e93c
description: "Summary: Read this topic to learn how to create initial user policies for Persistent Chat Server in Skype for Business Server 2015. Persistent Chat user policies determine whether or not users are allowed access to chat rooms."
---

# Configure Persistent Chat user policies in Skype for Business Server 2015
 
**Summary:** Read this topic to learn how to create initial user policies for Persistent Chat Server in Skype for Business Server 2015. Persistent Chat user policies determine whether or not users are allowed access to chat rooms.
  
You can manage Persistent Chat Server user policies at the following levels: global, site, or user. Initially, you configure the global policy to enable Persistent Chat settings for all users in your deployment, and then create additional user and site policies to control whether Persistent Chat is turned on for specific users and sites.
  
This topic contains the following sections:
  
- Configure the global policy
    
- Create a site policy
    
- Create a user policy
    
- Apply a policy to a user or user group
    
> [!NOTE] 
> Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The same functionality is available in Teams. For more information, see [Getting started with your Microsoft Teams upgrade](/microsoftteams/upgrade-start-here). If you need to use Persistent chat, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015.

## Configure the global policy

To configure the global policy:
  
1. From a user account that is assigned to the CsPersistentChatAdministrator, CsAdministrator, or CsUserAdministrator role, log on to any computer in your internal deployment.
    
2. From the **Start** menu, select the Skype for Business Server Control Panel or open a browser window, and then enter the Admin URL.
    
3. In Skype for Business Server Control Panel, click **Persistent Chat**, and then click **Persistent Chat Policy**.
    
4. Click **Global** in the list of policies, click **Edit**, and then click **Show details**.
    
5. In **Edit Persistent Chat Policy - Global**, do the following: 
    
   - In **Name**, specify a new name for the global policy, if you do not want to use the default of Global.
    
   - In **Description**, provide details about what the user policy is (for example, Global policy for  _centralSiteName_).
    
   - To control Persistent Chat for all sites and users not specifically controlled through a site policy or user policy, select or clear the **Enable Persistent Chat** check box.
    
6. Click **Commit**.
    
## Create a site policy

For each site that you have deployed, you can create a site-specific Persistent Chat policy. The configuration in the site policy overrides the global policy, but only for the specific site covered by the site policy. To create a site policy:
  
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
    
## Create a user policy

You can create user-specific policies that override the global policy and any site policies to which the user belongs. To create a user policy:
  
1. From a user account that is assigned to the CsPersistentChatAdministrator, CsAdministrator, or CsUserAdministrator role, log on to any computer in your internal deployment.
    
2. From the **Start** menu, select the Skype for Business Server Control Panel or open a browser window, and then enter the Admin URL.
    
3. In the left navigation bar, click **Persistent Chat**, and then click **Persistent Chat Policy**.
    
4. Click **New**, and then click **User policy**.
    
5. In **New Persistent Chat Policy**, do the following:
    
   - In **Name**, specify a name for the new user policy.
    
   - In **Description**, provide details about what the user policy is (for example, Persistent Chat policy for specific user).
    
   - To control Persistent Chat for all users who are not specifically controlled through a user policy, select or clear the **Enable Persistent Chat** check box.
    
6. Click **Commit**.
    
## Apply a policy to a user account

After you create policies, you can apply them to a user account as follows:
  
1. From a user account that is assigned to the CsPersistentChatAdministrator, CsAdministrator, or CsUserAdministrator role, log on to any computer in your internal deployment.
    
2. From the **Start** menu, select the Skype for Business Server Control Panel or open a browser window, and then enter the Admin URL.
    
3. In the left navigation bar, click **Users**, and then search on the user account that you want to configure.
    
4. In the table that lists the search results, click the user account, click **Edit**, and then click **Show details**.
    
5. In **Edit Skype for Business Server User** under **Persistent Chat policy**, select the Persistent Chat user policy that you want to apply.
    
    > [!NOTE]
    > The **\<Automatic\>** settings apply the default effective policy. These settings are applied automatically by the server.
  
6. Click **Commit**.
    

