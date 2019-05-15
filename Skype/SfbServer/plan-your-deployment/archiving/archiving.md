---
title: "Plan for archiving in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e9f0dcf7-66b4-4196-9e8c-b14721b1fb84
description: "Summary: Read this topic to learn how to plan for archiving in Skype for Business Server."
---

# Plan for archiving in Skype for Business Server
 
**Summary:** Read this topic to learn how to plan for archiving in Skype for Business Server.
  
Corporations and other organizations are subject to an increasing number of industry and government regulations that require the retention of specific types of communications. If your organization has such requirements, you can use archiving in Skype for Business Server to archive instant messaging (IM) and conferencing (meeting) communications to help support some of your compliance requirements.
  
## Archiving components

Skype for Business Server uses the following archiving components:
  
- **Archiving agents**. Archiving agents (also known as unified data collection agents) are installed and activated automatically on every Enterprise Edition Front End pool and Standard Edition Server. Although archiving agents are activated automatically, no messages are actually captured until archiving is enabled and appropriately configured. By default, archiving is disabled.
    
- **Archiving data storage**. Data storage for Skype for Business Server can be implemented as Skype for Business Server SQL Server databases, or, if you have an Exchange deployment, integrated with Exchange storage. 
    
Archiving also requires file storage, but archiving uses the same file storage as the Front End Servers or Standard Edition Server.

  
## Determine your organizations requirements for archiving

To implement archiving, you need to decide how to meet your organization's requirements for archiving by determining the following:
  
- **Which storage option to use**. You can implement storage in one of two ways or use a combination of both:
    
  - **Exchange storage.** If you have an Exchange deployment, you can integrate Skype for Business Server and Exchange archiving so that your Skype for Business Server and Exchange archived data are stored together in Exchange. If you enable the Microsoft Exchange integration option, user mailboxes homed on the Exchange Server use Exchange storage for archived data, but only if the mailboxes have been put on In-Place Hold. By default, Microsoft Exchange integration is not enabled.
    
  - **Skype for Business Server storage.** If you have users who are not homed on Exchange or who have not had their mailboxes put on In-Place Hold, or if you don't want to use Microsoft Exchange integration for any or all users in your deployment, you can deploy Skype for Business Server Archiving databases using SQL Server.
    
- **When to deploy archiving**. You can deploy archiving as part of your initial Skype for Business Server deployment, or you can add it to an existing deployment. To use Skype for Business Server archiving storage (SQL Server databases), you use Topology Builder to add the databases to your topology, and then publish the topology again. If all your users are homed on Exchange and have their mailboxes put on In-Place Hold, you do not have to update your topology, but only need to enable Microsoft Exchange integration to store archived data in Exchange. 
    
- **Which sites and users in the organization require archiving**. You can configure archiving settings for your entire organization and, optionally, for specific sites, pools, users, and user groups.
    
- **What content should be archived**. Whether you specify archiving at the global level or for specific sites and users, at each of these levels, you specify whether to enable the following types of content: 
    
  - Peer-to-peer instant messages
    
  - Conferences (meetings), which are multiparty instant messages
    
  - Conference content, including uploaded content (for example, handouts) and event-related content (for example, joining, leaving, uploading sharing, and changes in visibility)
    
  - Whiteboards and polls shared during a conference
    
- **What content cannot be archived**. The following types of content cannot be archived: 
    
  - Peer-to-peer file transfers
    
  - Audio/video for peer-to-peer instant messages and conferences
    
  - Desktop and application sharing for peer-to-peer instant messages and conferences
    
    Skype for Business Server also does not archive Persistent Chat conversations. To archive Persistent Chat conversations, you must enable and configure the Compliance service, which is a component that can be deployed with Persistent Chat Server. For details, see [Plan for Persistent Chat Server in Skype for Business Server 2015](../../plan-your-deployment/persistent-chat-server/persistent-chat-server.md).

    > [!NOTE] 
    > Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The same functionality is available in Teams. For more information, see [Journey from Skype for Business to Microsoft Teams](/microsoftteams/journey-skypeforbusiness-teams). If you need to use Persistent chat, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015. 
    
- **How long archived materials should be retained**. The Archiving database is not intended for long-term retention, and Skype for Business Server does not provide an e-discovery (search) solution for archived data, so data needs to be moved to other storage. Skype for Business Server provides a session export tool that you can use to export archived data, and which creates searchable transcripts of the archived data. 
    
     For the global policy, and for each site and user policy that you create, you can specify when to purge archived and exported data. For more information about purging data, see [Manage purging of archived data in Skype for Business Server](../../manage/archiving/purging-of-archived-data.md). For more information about using the session export tool, see [Export archived data in Skype for Business Server](../../manage/archiving/export-archived-data.md).
    
- **Whether to archive internal or external communications**. You can enable archiving for internal communications (communications between internal users), external communications (communications that include at least one user outside your internal network), or both. You can specify these options for your entire organization, or you can specify them for specific sites and pools. By default, neither option is enabled.
    
    > [!NOTE]
    > Controlling archiving for internal or external communications is only available for Skype for Business Policy. For Exchange-integrated archiving, both internal and external communications are either archived or not archived. 
  
- **Whether to implement critical mode**. If archiving is a requirement for your organization, configuring critical mode will block IM and conferencing sessions in the event of a Skype for Business Server failure that would prevent archiving. For example: 
    
  - A problem with the Skype for Business Server storage service. In this case, IM is blocked for users who are enabled for archiving.
    
  - An unavailable file share or a problem with the storage service. In this case, all active conferences hosted in the pool at the time of failure are switched to restricted mode and new conferences cannot be activated.
    
    Both IM and conferencing automatically recover after the failures are corrected.
    
## Choose archiving deployment and configuration options

Archiving is automatically installed on each Front End Server when you deploy the server, but archiving is not enabled until you configure it. How you configure archiving is determined by how you deploy it. You can deploy archiving in one of the following ways:
  
- Use Microsoft Exchange storage
    
- Use Skype for Business Server storage
    
> [!NOTE]
> If you implement both Skype for Business Server Archiving databases and enable Microsoft Exchange integration, Exchange policies override Skype for Business Server archiving policies, but only for users who are homed on Exchange and have had their mailboxes put on In-Place Hold. Skype for Business archiving depends on the Microsoft Exchange In-Place Hold policy. 
  
If you deploy archiving for one Front End pool or Standard Edition Server, you should enable it for all other Front End pools and Standard Edition servers in your deployment. If archiving is not enabled on the pool where a conversation or meeting is hosted, all conference data may not be archived. Archiving will still work for IM messages, but conferencing content and events may not be archived.
  
> [!NOTE]
> To enable delegation of administrative tasks while maintaining your organization's security standards, Skype for Business Server uses role-based access control (RBAC). With RBAC, administrative privilege is granted by assigning users to predefined administrative roles. To configure Skype for Business archiving policies and configurations, the user must be assigned to the CsArchivingAdministrator role (unless the configuration is done directly on the server where archiving is deployed, instead of remotely from another computer). For a list of the user rights, permissions, and roles required for archiving deployment, see [Deploy archiving for Skype for Business Server](../../deploy/deploy-archiving/deploy-archiving.md). 
  
> [!NOTE]
> If you use Microsoft Exchange integration, configuration of Exchange policies requires appropriate administrator rights and permissions. For details, see the Exchange documentation. 
  
### Microsoft Exchange storage

 If you choose Microsoft Exchange integration, you use Exchange policies and configurations to control the archiving of Skype for Business Server. You can configure the Microsoft Exchange integration option at the global level, site level, and pool level. If your deployment includes multiple forests, you must synchronize the settings between Skype for Business Server and Exchange. You will need to determine:
  
- Whether to archive IM, conferencing, or both
    
- Whether to implement critical mode, which blocks IM and conferencing sessions in case of a Skype for Business Server failure 
    
- Selection of the Microsoft Exchange integration option to use Exchange for storage of archived data
    
For information about how to configure Exchange In-Place Hold policies and settings to support archiving, see the Exchange product documentation.
  
### Skype for Business Server storage

If you choose Skype for Business Server storage, you use Skype for Business Server archiving policies and configurations to control how archiving is enabled and implemented. Skype for Business Server storage uses SQL Server databases, so you will need to add the appropriate SQL Server databases to your topology, then configure your archiving policies. 
  
### Add storage databases to your topology

When adding SQL Server storage databases to your topology, you can choose to collocate the Archiving databases with any of the following:
  
- Monitoring database
    
- Back-end database of an Enterprise Edition Front End pool
    
> [!NOTE]
> The server hosting the Archiving database can host other databases. However, when you consider collocating the Archiving database with other databases, be aware that if you are archiving the messages of more than a few users, the disk space needed by the Archiving database can grow very large. For this reason, we do not recommend collocating the Archiving database with the back-end database. 
  
If you collocate the Archiving database with the Monitoring database, back-end database, or both of these databases, you can either use a single SQL instance for any or all of the databases, or you can use a separate SQL instance for each database, with the following limitation: Each SQL instance can contain only a single back-end database, single Monitoring database, and single Archiving database.
  
For details about collocation of all server roles and databases, see [Topology Basics for Skype for Business Server](../../plan-your-deployment/topology-basics/topology-basics.md). For details about updating your topology to include storage databases, see [Create and publish new topology in Skype for Business Server](../../deploy/install/create-and-publish-new-topology.md).
  
### Determine archiving options and user policies

You will need to determine:
  
- Whether to enable or disable archiving for internal and external communications
    
- Whether to archive IM, conferencing, or both
    
- Whether to implement critical mode, which blocks IM and conferencing sessions in case of a Skype for Business Server failure 
    
- Whether to enable policies for specific users and groups
    
Skype for Business Server Archiving options can be specified at the following levels. 
  
- **Global level option**. This is the default archiving configuration and applies to your entire deployment. It is created when you deploy Skype for Business Server and, by default, disables archiving for both internal and external communications. You cannot delete this option. If you choose the delete option, the global option is reset to the default settings.
    
- **Site level options**. You can enable or disable archiving for one or more specific sites by creating and configuring a site-level archiving option for the site. You can delete any site-level archiving option that you create. A site-level archiving option overrides the global option, but only for the site specified in the option. 
    
    For example, if you enable archiving for internal and external communications in your global configuration and create a site configuration in which you disable archiving for external communications, only internal communications would be archived for that site. For another example, if you enable archiving for only IM in your global configuration and create a site configuration in which you enable archiving for both IM and conferencing, conferencing would only be archived for the site, not for the remainder of your organization.
    
- **Pool level options**. You can specify archiving settings for one or more specific pools by creating and configuring a pool-level configuration for the individual pool. A pool-level archiving configuration exists only if you create it. You can modify and delete any pool-level archiving configuration. A pool-level archiving configuration overrides the global configuration and any site archiving configuration you may have created. 
    
    For example, assume you enable archiving for IM only in your global configuration, then create a site-level configuration in which you enable archiving for both IM and conferencing, and then create a pool-level configuration in which you enable archiving only for IM. Communications would be archived for both IM and conferencing for all users of the site except the users homed in the pool specified in the pool-level configuration. For all other users in your organization, archiving would be enabled only for IM.
    
- **User archiving policies**. You can enable or disable archiving for one or more specific users and groups of users by creating, configuring, and applying a user-level archiving policy for the specified users and user groups. You can delete any user-level archiving policy that you create, and you can change which users and group of users the archiving policy applies to. A user-level archiving policy overrides the global policy and any site policies, but only for the users and user groups to whom the policy is applied. 
    
    For example, suppose you disable archiving for internal and external communications in your global configuration, create a site-level policy in which you enable archiving for internal and external communications, and then create a user-level policy in which you disable archiving for external communications. Communications would be archived for both external and internal communications for all site users except for the users to whom you apply the user-level policy--for these users only internal communications would be archived.
    
For details about how to set up initial archiving configurations when you deploy archiving, see [Deploy archiving for Skype for Business Server](../../deploy/deploy-archiving/deploy-archiving.md). For details about managing archiving after deployment, see [Manage archiving in Skype for Business Server](../../manage/archiving/archiving.md). 
  
## Archiving configuration tools

 You control most archiving options by using the Skype for Business Server Control Panel. However, there are a few options available only by using the Skype for Business Server Management Shell. These options include archiving duplicate messages and exporting archived data. For more information about using the Skype for Business Server Control Panel and the Skype for Business Server Management Shell to manage archiving policies, see [Manage archiving in Skype for Business Server](../../manage/archiving/archiving.md).
  
## Access archived data

Access to archived data is dependent on where the data is stored: 
  
- **Microsoft Exchange storage**. If you choose the Exchange integration option, Skype for Business Server deposits the archiving content in the Exchange store for all users who are homed on Exchange, and who have had their mailboxes put on In-Place Hold. Archived data is stored in the user mailboxes Recoverable items folder, which is generally invisible to users, and can only be searched by users with an Exchange **Discovery Management** role. Exchange enables federated search and discovery, along with SharePoint, if it is deployed. For more details about storage, retention, and discovery of data stored in Exchange, see the Exchange and SharePoint documentation.
    
- **Skype for Business Server archiving storage**. If you set up Skype for Business Server Archiving databases, Skype for Business Server deposits archiving content in the Skype for Business Server Archiving databases for any users not homed on Exchange, and who have not had their mailboxes put on In-Place Hold. This data is not searchable, but it can be exported to formats that are searchable using other tools. For details about exporting data stored in Archiving databases, see [Export archived data in Skype for Business Server](../../manage/archiving/export-archived-data.md).
    
## For more information

For more information about archiving, see the following topics:
  
- [Deploy archiving for Skype for Business Server](../../deploy/deploy-archiving/deploy-archiving.md)
    
- [Manage archiving in Skype for Business Server](../../manage/archiving/archiving.md)
    
For more details about how Skype for Business Server and Exchange work together, see [Plan to integrate Skype for Business and Exchange](../../plan-your-deployment/integrate-with-exchange/integrate-with-exchange.md).
  

