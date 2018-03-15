---
title: "Configuring Archiving options for a site in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 59b48fd9-d5fc-40b4-abae-e9cf89ee5573
description: "You can specify Archiving options to be applied to specific sites by creating and configuring options in an Archiving configuration for each of those sites. A site configuration overrides the global configuration, but only for the site specified in the site configuration. Pool configurations override site configurations"
---

# Configuring Archiving options for a site in Lync Server 2013
[]
You can specify Archiving options to be applied to specific sites by creating and configuring options in an Archiving configuration for each of those sites. A site configuration overrides the global configuration, but only for the site specified in the site configuration. Pool configurations override site configurations 
  
For details about how Archiving configurations work, including the hierarchy for global, site, and pool configurations, see [How Archiving works in Lync Server 2013](how-archiving-works.md) in the Planning documentation, Deployment documentation, or Operations documentation. 
  
> [!NOTE]
> You should specify all appropriate options in the Archiving configurations before enabling Archiving. 
  
> [!IMPORTANT]
> To enable archiving, you must specify archiving policies to control the archiving of internal and external communications at the global level and, if appropriate, at site and user levels. If you configure user-level policies, you must also assign the user policies to specific users. For details about creating and configuring archiving policies, see [Managing the Archiving of internal and external communications in Lync Server 2013](managing-the-archiving-of-internal-and-external-communications.md) in the Operations documentation. 
  
### To configure archiving options at the site level

1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server 2013 Control Panel. For details about the different methods you can use to start Lync Server 2013 Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
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
    

