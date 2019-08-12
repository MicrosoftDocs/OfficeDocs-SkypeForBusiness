---
title: "Archiving Server General Settings Expander"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.ArchivingGeneralSettingsExpander
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 0b820af7-8d00-42e2-979c-dbae17159a08
ROBOTS: NOINDEX, NOFOLLOW
description: "In Topology Builder, you can edit the properties for an individual server running Archiving either by right-clicking the server running Archiving in the console tree and clicking Action in the toolbar, or by clicking a task in the Actions pane, and then clicking Edit Properties and changing any of the following options:"
---

# Archiving Server General Settings Expander
 
In Topology Builder, you can edit the properties for an individual server running Archiving either by right-clicking the server running Archiving in the console tree and clicking **Action** in the toolbar, or by clicking a task in the Actions pane, and then clicking **Edit Properties** and changing any of the following options:
  
- **FQDN**, to change the fully qualified domain name (FQDN) of the server that you want to deploy as an Server running Archiving.
    
- **SQL store**, to change the instance of SQL Server to be used for the archiving SQL Server database. If you change the SQL Server database of a server running Archiving, you must restart the server running Archiving to make sure that the change takes effect.
    
- **File share**, to change the folder to be used for the archiving file store. If you change the file share of a Server running Archiving, you must restart the Server running Archiving to make sure that the change takes effect. Additionally, you must move previous conference files to the new file store folder to avoid loss of archived conference files.
    
> [!NOTE]
> To change the pools associated with a server running Archiving, select the **Edit Properties** option for the individual Front End pool node or Survivable Branch Appliance node that is currently associated with the server running Archiving.
  
> [!NOTE]
> The Archiving node contains a server running Archiving if you have previously added a server running Archiving to the topology in Topology Builder. You can edit properties for any server running Archiving in the list. However, instant messaging or web conferencing (messaging) cannot be archived until you also set up the service for the server running Archiving. 
  

