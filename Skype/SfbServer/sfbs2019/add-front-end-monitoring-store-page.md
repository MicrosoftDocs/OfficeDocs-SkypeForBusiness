---
title: "Add Front End Monitoring Store Page"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
f1_keywords:
- ms.lync.tb.AddFrontEndMonitoringStorePage
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 48e8587d-a9d2-4fc5-acc5-2bf0abf133c6
description: "You Define the Monitoring SQL Server store by configuring the following properties:"
---

# Add Front End Monitoring Store Page
[]
You **Define the Monitoring SQL Server store** by configuring the following properties: 
  
- **Monitoring SQL Server store**: Select a SQL Server fully qualified domain name (and, optionally an instance) from the list.
    
    Click **New** to create a new SQL Server FQDN definition, and optionally an instance name for the Monitoring Server store. 
    
- Select the **Enable SQL Server store mirroring** check box if you want to add database mirroring for the Monitoring Server. 
    
    Select an existing **Monitoring SQL Server store mirror** from the list. 
    
    Click **New** to create a new SQL Server FQDN definition, and optionally an instance name for the mirror store. 
    
- If you selected **Enable SQL Server store mirroring**, optionally select **Use SQL Server mirroring witness to enable automatic failover** to select a SQL Server mirroring witness store from the list. 
    
    Click **New** to create a new SQL Server FQDN definition, and optionally an instance name for the mirroring witness store. 
    
![Define monitoring SQL server store page](media/Add_Front_End_Monitoring_Store_Page.jpg)
  
Click **Back** to go back to the previous pool definition dialog. 
  
Click **Next** after you have finished entering the options for this dialog to proceed with the configuration. 
  
Click **Cancel** to discard all changes and end the wizard. 
  
Click **Help** to access context sensitive help, such as this page. 
  
## See also

#### 

[Associating a monitoring store with a Front End pool in Lync Server 2013](associating-a-monitoring-store-with-a-front-end-pool.md)

