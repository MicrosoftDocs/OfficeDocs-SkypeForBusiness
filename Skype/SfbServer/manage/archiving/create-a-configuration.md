---
title: "Create an archiving configuration in Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: dc574afa-0b7d-404f-99b3-c812430b7c70
description: "Summary: Learn how to create an archiving configuration for Skype for Business Server."
---

# Create an archiving configuration in Skype for Business Server

**Summary:** Learn how to create an archiving configuration for Skype for Business Server.
  
## Configure archiving options by using the Control Panel

To configure archiving options for a specific site or pool: 
  
1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment. 
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Configuration**.
    
4. On the **Archiving Configuration** page, click **New**, and then do one of the following: 
    
   - To create a site archiving configuration, click **Site Configuration**, and then in **Select a site**, select the site to be configured for archiving.
    
   - To create a pool archiving configuration, click **Pool Configuration**, and then in **Select a pool**, select the pool to be configured for archiving.
    
5. In **New Archiving Setting**, in the **Archiving setting** drop-down list box, do one of the following:
    
   - To enable archiving only for instant messaging (IM) sessions, click **Archive IM sessions**.
    
   - To enable archiving for both IM sessions and web conferences, click **Archive IM and web conferencing sessions**.
    
   - To disable archiving for this configuration, click **Disable archiving**.
    
6. Also in **New Archiving Setting**, do the following:
    
   - To block activity when archiving is not available, select the **Block instant messaging (IM) or web conferencing sessions if archiving fails** check box.
    
   - To use Microsoft Exchange Server to store archiving data, click the **Microsoft Exchange integration** check box.
    
   - To enable data purging, select the **Enable purging of archiving data** check box, and then do one of the following:
    
     - To specify purging after a specific number of days, click **Purge exported archiving data and stored archiving data after maximum duration (days)**, and then specify the number of days.
    
     - To limit purging to archiving data that has been exported, click **Purge exported archiving data only**.
    
7. Click **Commit**.
    
## Configure archiving options by using Windows PowerShell

You can also configure archiving options for a specific site or pool by using the **New-CsArchivingConfiguration** cmdlet.
  
The following command creates a new collection of archiving configuration settings for the Redmond site:
  
```
New-CsArchivingConfiguration -Identity "site:Redmond"
```

Because no parameters (other than the mandatory Identity parameter) were specified in the preceding command, the new collection of configuration settings will use the default values for all its properties. 
  
To create settings that use different property values, simply include the appropriate parameter and parameter value. The following example creates a collection of archiving configuration settings that, by default, allow archiving of instant messaging sessions only:
  
```
New-CsArchivingConfiguration -Identity "site:Redmond" -EnableArchiving "ImOnly"
```

Multiple property values can be modified by including multiple parameters. For example, this command configures the new settings to archive instant messaging sessions and to block instant messaging of the archiving service is not available:
  
```
New-CsArchivingConfiguration -Identity "site:Redmond" -EnableArchiving "ImOnly" -BlockOnArchiveFailure $True
```

For more information, see the help topic for the [New-CsArchivingConfiguration](https://docs.microsoft.com/powershell/module/skype/new-csarchivingconfiguration?view=skype-ps) cmdlet.
