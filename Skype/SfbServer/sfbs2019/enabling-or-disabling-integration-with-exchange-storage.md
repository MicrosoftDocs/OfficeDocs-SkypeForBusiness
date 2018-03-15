---
title: "Enabling or disabling integration of Lync Server 2013 with Exchange storage"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c08b9ba5-04f6-452a-b44c-c130f1564a34
description: "In Lync Server 2013 Control Panel, you use Archiving configurations to enable and disable integration with Exchange storage. This includes the following Archiving configurations:"
---

# Enabling or disabling integration of Lync Server 2013 with Exchange storage
[]
In Lync Server 2013 Control Panel, you use Archiving configurations to enable and disable integration with Exchange storage. This includes the following Archiving configurations: 
  
- A global configuration that is created by default when you deploy Lync Server 2013.
    
- Optional site-level and pool-level configurations that you can create and use to specify how archiving is implemented for specific sites or pools.
    
For details about how Archiving configurations are implemented, including which options you can specify and the hierarchy of Archiving configurations, see [How Archiving works in Lync Server 2013](how-archiving-works.md) in the Planning documentation, Deployment documentation, or Operations documentation. 
  
### To enable or disable integration with Microsoft Exchange storage

1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Configuration**.
    
4. Click the name of the appropriate global, site, or pool configuration in the list of archiving configurations, click **Edit**, click **Show details**, and then do the following:
    
  - To enable integration with Exchange 2013 storage, select the **Microsoft Exchange integration** check box. 
    
  - To disable integration with Exchange 2013 storage, clear the **Microsoft Exchange integration** check box. 
    
5. Click **Commit**.
    
## See also

#### 

[How Archiving works in Lync Server 2013](how-archiving-works.md)
#### 

[Managing Archiving configuration options in Lync Server 2013 for your organization, sites, and pools](managing-archiving-configuration-options-for-your-organization-sites-and-pools.md)

