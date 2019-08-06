---
title: "Configure archiving options for Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 2f534697-ac7f-45b7-8cdc-ba67f052223b
description: "Summary: Read this topic to learn how to configure initial archiving options for Skype for Business Server. You initially set up archiving configurations when you deploy archiving, but you can change, add, and delete configurations after deployment."
---

# Configure archiving options for Skype for Business Server
 
**Summary:** Read this topic to learn how to configure initial archiving options for Skype for Business Server. You initially set up archiving configurations when you deploy archiving, but you can change, add, and delete configurations after deployment.
  
To configure initial archiving configurations, you use Skype for Business Server Control Panel to specify the following:
  
- Global-level configuration that is created by default when you deploy Skype for Business Server
    
- Optional site-level configurations that specify how archiving is implemented for a specific site
    
- Optional pool-level configurations that specify how archiving is implemented for a specific pool
    
You will need to configure options for the following:
  
- Whether to enable or disable archiving
    
- Whether to archive IM sessions
    
- Whether to archive web conferencing sessions
    
- Whether to block activity when archiving is not available
    
- Whether to use Exchange integration
    
- How to set up purging and exporting of data
    
> [!NOTE]
> You should specify all appropriate options before enabling archiving. 
  
For details about how archiving configurations are implemented, including which options you can specify and the hierarchy of archiving configurations, see [Plan for archiving in Skype for Business Server](../../plan-your-deployment/archiving/archiving.md). For details about how to manage configurations after deployment by using the Control Panel or by using Windows PowerShell, see [Manage archiving options in Skype for Business Server](../../manage/archiving/options.md).
  
## Configure global level archiving options

When you add archiving to your topology and publish the topology, Skype for Business Server creates a global configuration for archiving. By default, no archiving options are enabled in the global configuration. The global configuration controls which options are enabled for your entire deployment, unless you set up site or pool configurations, which override the global configuration.
  
To configure archiving options at the global level:
  
1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Configuration**.
    
4. On the **Archiving Configuration** page, click **Global**, click **Edit**, and then click **Show details**.
    
5. In **Edit Archiving Setting - Global**, in the **Archiving setting** drop-down list, select one of the following archiving options:
    
   - **Disable archiving**
    
   - **Archive IM sessions**
    
   - **Archive IM and web conferencing sessions**
    
6. Also on the **Edit Archiving Setting - Global** page, do the following:
    
   - To block activity when archiving is not available, select the **Block instant messaging (IM) or web conferencing sessions if archiving fails** check box.
    
   - To use Microsoft Exchange Server to store archiving data, click the **Microsoft Exchange integration** check box.
    
   - To enable data purging, select the **Enable purging of archiving data** check box, and then do one of the following:
    
   - To specify purging after a specific number of days, click **Purge exported archiving data and stored archiving data after maximum duration (days)**, and then specify the number of days.
    
   - To limit purging to archiving data that has been exported, click **Purge exported archiving data only**.
    
7. Click **Commit**.
    
## Configure site level archiving options

You can specify archiving options for a specific site. A site configuration overrides the global configuration, but only for the site specified in the site configuration. 
  
1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Configuration**.
    
4. On the **Archiving Configuration** page, click **New**, and then click **Site Configuration**.
    
5. In **Select a Site**, select the site to be configured for archiving.
    
6. In **New Archiving Setting**, in the **Archiving setting** drop-down list box, do one of the following:
    
   - To enable archiving only for instant messaging (IM) sessions, click **Archive IM sessions**.
    
   - To enable archiving for both IM sessions and conferences, click **Archive IM and web conferencing sessions**.
    
   - To disable archiving for the policy, click **Disable archiving**.
    
7. Also in **New Archiving Setting**, do the following:
    
   - To block activity when archiving is not available, select the **Block instant messaging (IM) or web conferencing sessions if archiving fails** check box.
    
   - To use Microsoft Exchange Server to store archiving data, click the **Microsoft Exchange integration** check box.
    
   - To enable data purging, select the **Enable purging of archiving data** check box, and then do one of the following:
    
   - To specify purging after a specific number of days, click **Purge exported archiving data and stored archiving data after maximum duration (days)**, and then specify the number of days.
    
   - To limit purging to archiving data that has been exported, click **Purge exported archiving data only**.
    
8. Click **Commit**.
    
## Configure pool level archiving options

You can specify archiving options for a specific pool. A pool configuration overrides the global configuration and site configuration, but only for the pool specified in the pool configuration.
  
1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Configuration**.
    
4. On the **Archiving Configuration** page, click **New**, and then click **Pool Configuration**.
    
5. In **Select a Service**, select the pool to be configured for archiving.
    
6. In **New Archiving Setting**, in the **Archiving setting** drop-down list, select one of the following archiving options:
    
   - **Disable archiving**
    
   - **Archive IM sessions**
    
   - **Archive IM and web conferencing sessions**
    
7. Also in **New Archiving Setting** page, do the following:
    
   - To block activity when archiving is not available, select the **Block instant messaging (IM) or web conferencing sessions if archiving fails** check box.
    
   - To use Microsoft Exchange Server to store archiving data, click the **Microsoft Exchange integration** check box.
    
   - To enable data purging, select the **Enable purging of archiving data** check box, and then do one of the following:
    
   - To specify purging after a specific number of days, click **Purge exported archiving data and stored archiving data after maximum duration (days)**, and then specify the number of days.
    
   - To limit purging to archiving data that has been exported, click **Purge exported archiving data only**.
    
8. Click **Commit**.
    

