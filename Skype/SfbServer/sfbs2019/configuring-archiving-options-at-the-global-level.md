---
title: "Configuring Archiving options at the global level in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: bfe415f7-2abf-41ee-a1cb-cf48b2d59c0c
description: "When you add Archiving to your topology and publish the topology, Lync Server creates a global configuration for Archiving. By default, no Archiving options are enabled in the global configuration. The global configuration controls which options are enabled for your entire deployment, unless you set up site or pool configurations, which override the global configuration."
---

# Configuring Archiving options at the global level in Lync Server 2013
[]
When you add Archiving to your topology and publish the topology, Lync Server creates a global configuration for Archiving. By default, no Archiving options are enabled in the global configuration. The global configuration controls which options are enabled for your entire deployment, unless you set up site or pool configurations, which override the global configuration.
  
For details about how Archiving configurations work, including the hierarchy for global, site, and pool configurations, see [How Archiving works in Lync Server 2013](how-archiving-works.md) in the Planning documentation, Deployment documentation, or Operations documentation. 
  
> [!NOTE]
> You should specify all appropriate options in the Archiving configurations before enabling Archiving. 
  
### To configure archiving options at the global level

1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server 2013 Control Panel. For details about the different methods that you can use to start Lync Server 2013 Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
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
    

