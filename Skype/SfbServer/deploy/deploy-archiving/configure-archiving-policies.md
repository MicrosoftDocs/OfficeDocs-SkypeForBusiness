---
title: "Configure archiving policies for Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e8e48087-d4f0-4fe1-9e7e-f2b3e07f815f
description: "Summary: Read this topic to learn how to configure initial archiving policies for Skype for Business Server users."
---

# Configure archiving policies for Skype for Business Server
 
**Summary:** Read this topic to learn how to configure initial archiving policies for Skype for Business Server users.
  
In Skype for Business Server, you use policies to enable and disable archiving for internal communications and external communications for users who are homed on Skype for Business Server. This includes the following:
  
- A global policy that is created by default when you deploy Skype for Business Server
    
- Optional site-level policies that specify how archiving is implemented for a specific site
    
- Optional user-level policies that specify how archiving is implemented for specific users
    
You initially set up archiving policies when you deploy archiving, but you can change, add, and delete policies after deployment. In Skype for Business Server Control Panel, you can use the **Archiving Policy** page of the **Archiving and Monitoring** group to manage policies at the global, site, and user levels.
  
> [!NOTE]
> To control the implementation of archiving, you must specify options, such as whether to archive IM or conferencing, the use of critical mode, and purging options. By default no options are enabled in the global archiving configuration or any site or pool archiving configuration. You should specify all appropriate options before enabling archiving for internal or external communications. For details, see [Configure archiving options for Skype for Business Server](configure-archiving-options.md). 
  
> [!NOTE]
> If you enable Microsoft Exchange integration for your deployment, Exchange In-Place Hold policies control whether archiving is enabled for the users who are homed on Exchange and have their mailboxes put on In-Place Hold. 
  
For details about how archiving policies work, including the hierarchy for global, site, and user policies, see [Plan for archiving in Skype for Business Server](../../plan-your-deployment/archiving/archiving.md). For details about how to manage policies after deployment, see [Manage archiving policies in Skype for Business Server](../../manage/archiving/policies.md).
  
## Global policy

When you deploy your Front End Servers, Skype for Business Server creates a global policy for archiving. By default, archiving is disabled in the global policy. The global policy controls whether archiving is enabled for internal and external communications for your entire deployment, unless you set up site or user policies, which override the global policy, or if you use Microsoft Exchange integration for some or all of your users. If you use Microsoft Exchange integration, the global policy does not apply to any users who are homed on Exchange and have the mailboxes put on In-Place Hold.
  
### Configure the global policy for archiving for Skype for Business Server archiving databases

1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Policy**.
    
4. On the **Archiving Policy** page, click **Global**, click **Edit**, and then click **Show details**.
    
5. In **Edit Archiving Policy - Global**, do the following:
    
   - In **Name**, if you do not want to use the default name of Global, specify a new name for the global policy. 
    
   - In **Description**, provide information about what the policy is (for example, Global policy for  *divisionName*  .
    
   - To control archiving of internal communications for all sites and users not specifically controlled through a site policy or user policy, select or clear the **Archive internal communications** check box.
    
   - To control archiving of external communications for all sites and users not specifically controlled through a site policy or user policy, select or clear the **Archive external communications** check box.
    
6. Click **Commit**.
    
## Site policies

You can enable or disable archiving for specific sites by creating an archiving policy for each of those sites. A site policy overrides the global policy, but user policies override site policies. Archiving policies only apply if you do not use Microsoft Exchange integration or, if you do use Microsoft Exchange integration, but have some users who are not homed on Exchange and have their mailboxes put on In-Place Hold.
  
### Create an archiving policy for a site

1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Policy**.
    
    For details about how archiving policies work, including the hierarchy for global, site, and user policies, see [Plan for archiving in Skype for Business Server](../../plan-your-deployment/archiving/archiving.md).
    
4. Click **New**, and then click **Site policy**.
    
5. In **Select a site**, click the site to which the policy is to be applied.
    
6. In **New Archiving Policy**, do the following:
    
   - In **Name**, specify the name for the site policy. 
    
   - In **Description**, provide information about what the site policy is (for example, site policy for Redmond).
    
   - To control archiving of internal communications for the specified site, select or clear the **Archive internal communications** check box.
    
   - To control archiving of external communications for the specified site, select or clear the **Archive external communications** check box.
    
7. Click **Commit**.
    
## User policies

You can enable or disable archiving for specific users by creating and configuring an archiving policy for users, and then applying the policy to specific users or user groups. User policies override any global policy or site policies. Archiving policies only apply if you do not use Microsoft Exchange integration or, if you do use Microsoft Exchange integration, but have some users who are not homed on Exchange and have their mailboxes put on In-Place Hold.
  
### Configure an archiving policy for users homed on Skype for Business Server

1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Policy**.
    
4. Click **New**, and then click **User policy**.
    
5. In **New Archiving Policy**, do the following:
    
   - In **Name**, specify the name for the user policy. 
    
   - In **Description**, provide information about what the user policy is (for example, user policy for legal department).
    
   - To control archiving of internal communications for the user policy, select or clear the **Archive internal communications** check box.
    
   - To control archiving of external communications for the user policy, select or clear the **Archive external communications** check box.
    
6. Click **Commit**.
    
A user policy applies only to users to whom you assign the policy.
### Apply a Skype for Business Server archiving policy to a user

1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, click **Users**, and then search for the user account that you want to configure.
    
4. In the table that lists the search results, click the user account, click **Edit**, and then click **Show details**.
    
5. In **Edit Skype for Business Server user** under **Archiving policy**, select the archiving user policy that you want to apply.
    
    > [!NOTE]
    > The **\<Automatic\>** settings apply the default server installation settings. These settings are applied automatically by the server.
  
6. Click **Commit**.
    

