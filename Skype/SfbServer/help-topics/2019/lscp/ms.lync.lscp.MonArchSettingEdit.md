---
title: "Archiving Configuration Create New or Edit Existing"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.MonArchSettingEdit
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 49096960-c442-4846-be8f-03c167acea41
ROBOTS: NOINDEX, NOFOLLOW
description: "You use Archiving configurations to control archiving options for your deployment. Archiving configurations include the global configuration, and, optionally, one or more site and pool configurations:"
---

# Archiving Configuration: Create New or Edit Existing
 
You use Archiving configurations to control archiving options for your deployment. Archiving configurations include the global configuration, and, optionally, one or more site and pool configurations:
  
- **Global configuration** The global configuration is created by default. You can edit the global configuration, but you cannot delete this Archiving configuration. If you try to delete it, all options are reset to the defaults.
    
- **Site configuration (optional)** You can specify one or more site Archiving configurations, each of which you can configure to control archiving options for a specific site. A site configuration overrides the global configuration, but only for the sites specified in the Archiving site configurations. You can edit or delete site configurations.
    
- **Pool configuration (optional)** You can specify one or more pool Archiving configurations, to control archiving options for a specific pool. A pool configuration overrides the global configuration and site configuration, but only for the pools specified in Archiving pool configurations. You can edit or delete pool configurations.
    
> [!NOTE]
> Archiving configurations apply to users homed on Skype for Business Server, and, if you enable the Microsoft Exchange integration option to use Exchange to store archiving data in Microsoft Exchange, to users homed on Exchange. However, some options are implemented slightly differently for users homed on Exchange, as described in the next section. 
  
To configure the settings for a new or existing Archiving configuration, specify the following options:
- **Name** Each Archiving configuration requires a name. The name is determined by the type of configuration you are adding or editing:
    
  - **Global configuration** The default name is Global. For example, Contoso North American Organization.
    
  - **Site configuration** The list contains the available sites in your deployment. Click a single site to select it. For example, Redmond Data Center.
    
  - **Pool configuration** Specify an appropriate name, which can be the name of a specific Front End pool or Standard Edition Server in your deployment. For example, Marketing Division.
    
- **Description** This is optional. Use it to provide additional details, such as the scope or use of the configuration. For example, Coordinate with Legal Departments of Other Sites.
    
- **Archiving setting** Options include the following:
    
  - **Archive IM sessions**
    
  - **Archive IM and web conferencing sessions**
    
  - **Disable archiving**
    
- **Block instant messaging (IM) or web conferencing sessions if archiving fails** Failures include the following:
    
  - **IM** A failure could be a full database or problem with the storage service. In this case, IM is blocked for users who are enabled for Archiving.
    
  - **Conferencing** A failure could be an unavailable file share or a problem with the storage service. In this case, all active conferences hosted in the pool at the time of failure are switched to restricted mode and new conferences cannot be activated.
    
    Both IM and conferencing automatically recover after the failures are corrected.
    
- **Microsoft Exchange integration** Select this option if you have users who are homed on Exchange. With this option, Exchange is used to store data for those users, if their mailboxes have been placed on In-Place Hold. If all your users are homed on Exchange, you do not need to set up separate SQL Server databases for storage of archiving data.
    
- **Enable purging of archiving data** Select this option to enable purging and specify purging options, which include the following:
    
  - Purging after a specific number of days that you specify.
    
  - Purging after the archiving data has been exported (which includes data that has been uploaded to Exchange, if you enable Microsoft Exchange integration).
    
    > [!NOTE]
    > If you enable Microsoft Exchange integration, purging for users homed on Exchange and with their mailboxes placed on In-Place Hold is controlled by Exchange. The only exception is for conferencing files, which are stored on the Lync Server file share. These files are purged from the file share only after the files have been exported (uploaded to Exchange), if you select the option to purge data after the archiving data has been exported, or after the specified maximum number of days, if you specify a maximum number of days for retention. 
  
For details about the Archiving feature and capabilities, including Exchange integration, see [Plan for archiving in Skype for Business Server](../../../plan-your-deployment/archiving/archiving.md), [Deploy archiving for Skype for Business Server](../../../deploy/deploy-archiving/deploy-archiving.md), and [Manage archiving in Skype for Business Server](../../../manage/archiving/archiving.md).

