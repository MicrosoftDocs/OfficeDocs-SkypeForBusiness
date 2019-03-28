---
title: 'Lync Server 2013: How Archiving works'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: How Archiving works
ms:assetid: 536a52a9-cfb7-4392-9620-ffc5b319b31b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204900(v=OCS.15)
ms:contentKeyID: 48184174
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# How Archiving works in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-04_

Lync Server 2013 Archiving provides options to help you meet your compliance needs. To implement and maintain it in a way that most effectively meets your organization’s requirements, you should understand:

  - What information can be archived.

  - How to enable and disable Archiving in your deployment.

  - The archiving options that you can configure to control how Archiving is implemented.

<div>

## What Information Can Be Archived?

The following types of content can be archived:

  - Peer-to-peer instant messages

  - Conferences (meetings), which are multiparty instant messages

  - Conference content, including uploaded content (for example, handouts) and event-related content (for example, joining, leaving, uploading sharing, and changes in visibility)

  - Whiteboards and polls shared during a conference

The following types of content are not archived:

  - Peer-to-peer file transfers

  - Audio/video for peer-to-peer instant messages and conferences

  - Desktop and application sharing for peer-to-peer instant messages and conferences

Lync Server also does not archive Persistent Chat conversations. To archive Persistent Chat conversations, you must enable and configure the compliance service, which is a component that can be deployed with Microsoft Lync Server 2013, Persistent Chat Server. For details, see [Planning for Persistent Chat Server in Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md) in the Planning documentation.

</div>

<div>

## How Do I Start Using Archiving?

Archiving is automatically installed on each Front End Server when you deploy the server, but Archiving is not enabled until you configure it. How you configure it is determined by how you deploy Archiving:

  - **Archiving using Microsoft Exchange integration.** If you have users who are homed on Exchange 2013 and their mailboxes have been put on In-Place Hold, you can select the option to integrate Lync Server 2013 storage with Exchange storage. If you choose the Microsoft Exchange integration option, you use Exchange 2013 policies and configurations to control the archiving of Lync Server 2013 data for those users.

  - **Archiving using Lync Server Archiving databases.** If you have users who are not homed on Exchange 2013 or who have not had their mailboxes put on In-Place Hold, or if you don’t want to use Microsoft Exchange integration for any or all users in your deployment, you can deploy Lync Server Archiving databases using SQL Server to store Archiving data for those users. In this case, Lync Server 2013 Archiving policies and configurations determine whether Archiving is enabled and how it is implemented. To use Lync Server 2013, you must add the appropriate SQL Server databases to your topology and publish the topology.

<div>

## Archiving Setup When Using Microsoft Exchange Integration

If your users are homed on Exchange 2013 and their mailboxes have been put on In-Place Hold, you can choose the **Microsoft Exchange integration** option (as described later in this section) to archive Lync Server 2013 for those users, and then you control archiving for those users by specifying Exchange In-Place Hold policies and settings, as well as Lync Server configurations to control the following:

  - Whether to archive IM, conferencing, or both.

  - Whether to implement critical mode for your Lync Server deployment.

  - Selection of the Microsoft Exchange integration option to use Exchange 2013 for storage of archived data.

These Lync Server 2013 Archiving configuration options are described later in this section. For information about how to configure Exchange In-Place Hold policies and settings to support archiving, see the Exchange 2013 product documentation.

</div>

<div>

## Archiving Setup When Using Lync Server Archiving Database Storage

If you want to use Lync Server Archiving databases (using SQL Server databases) to archive data for any users in your deployment, you can configure Lync Server Archiving policies to control whether Archiving is enabled for those users. In each Archiving policy, you can enable or disable Archiving for either or both of the following:

  - Internal communications

  - External communications

By default, archiving is not enabled for internal communications or external communications in any Lync Server Archiving policy. You enable and disable communications using Lync Server 2013 Control Panel or using cmdlets in the Lync Server 2013 Management Shell.

Lync Server 2013 Archiving policies include the following:

  - **Global Archiving policy**. This is the default Archiving policy and applies to your entire deployment. It is created when you deploy Lync Server 2013 and, by default, disables Archiving for both internal and external communications. You cannot delete this policy. If you choose the delete option, the global policy is reset to the default settings.

  - **Site Archiving policy**. Optionally, you can enable or disable Archiving for one or more specific sites by creating and configuring a site-level Archiving policy for the site. When you create a site-level Archiving policy, by default, archiving is not enabled. You can delete any site-level Archiving policy that you create. A site-level Archiving policy overrides the global policy, but only for the site specified in the policy. For example, if you enable Archiving for internal and external communications in your global policy and create a site policy in which you disable Archiving for external communications, only internal communications would be archived for that site.

  - **User Archiving policy**. Optionally, you can enable or disable Archiving for one or more specific users and group of users by creating, configuring, and applying a user-level Archiving policy for the specified users and user groups. When you create a user-level Archiving policy, by default, archiving is not enabled. You can delete any user-level Archiving policy that you create, and you can change which users and group of users the Archiving policy applies to. A user-level Archiving policy overrides the global policy and any site policies, but only for the users and user groups to whom the policy is applied. For example, if you disable Archiving for internal and external communications in your global policy, create a site-level policy in which you enable Archiving for internal and external communications, and then create a user-level policy in which you disable Archiving for external communications, the communications would be archived for both external and internal communications for all site users except that, for the users to whom you apply the user-level policy, only internal communications would be archived.

For details about how to set up initial Archiving policies when you deploy Archiving, see [Configuring and assigning Archiving policies in Lync Server 2013](lync-server-2013-configuring-and-assigning-archiving-policies.md) in the Deployment documentation. For details about using Archiving policies to enable and disable communications after deployment, see [Managing the Archiving of internal and external communications in Lync Server 2013](lync-server-2013-managing-the-archiving-of-internal-and-external-communications.md) in the Operations documentation.

<div>


> [!NOTE]  
> If you implement both Lync Server 2013 Archiving databases and enable Microsoft Exchange integration, Exchange 2013 policies override Lync Server Archiving policies, but only for users who are homed on Exchange 2013 and have had their mailboxes put on In-Place Hold. Lync Archiving depends on Microsoft Exchange In-Place Hold policy only.



</div>

</div>

<div>

## What Options Do I Have for Configuring Archiving?

In addition to using policies and to enable and disable Archiving, you have other Archiving options that can be configure for your entire deployment and, optionally, for specific sites and pools. You control most Archiving options by using one or more Archiving configurations, which are available in Lync Server 2013 Control Panel, but also have another option that is only available for configuration using Lync Server 2013 Management Shell.

<div>

## Archiving Configuration Options Available in Lync Server 2013 Control Panel

Each archiving configuration provides the following options:

The global-level configuration is created automatically when you deploy archiving and can be configured, but not deleted. If you select the option to delete the global configuration, the settings are reset to the default values. You can create multiple site and pool configurations that, together with the global configuration, control archiving settings. For the global configuration and each site and pool configuration, you have the following options:

  - Disable archiving, enable archiving only for instant messaging (IM), or enable archiving of both IM and conferencing.

  - Configure critical mode to block IM and conferencing sessions in the event of a Lync Server failure. Failures include the following:
    
      - **IM**. A problem with the Lync Server storage service. In this case, IM is blocked for users who are enabled for Archiving.
    
      - **Conferencing**. A failure could be an unavailable file share or a problem with the storage service. In this case, all active conferences hosted in the pool at the time of failure are switched to restricted mode and new conferences cannot be activated.
    
    Both IM and conferencing automatically recover after the failures are corrected.

  - Specify the use of Microsoft Exchange Server 2013 integration to use Exchange 2013 for storage of archived data, instead of setting up separate SQL Server databases for storage of Lync Server 2013 archiving data.

  - Configure purging options for archived data. This includes specifying when to purge archived data, which can be either of the following:
    
      - After a specific number of days that you specify
    
      - After the archiving data has been exported (which includes data that has been uploaded to Exchange, if you enable Microsoft Exchange integration).
    
    <div>
    

    > [!NOTE]  
    > If you enable Microsoft Exchange integration, purging for users homed on Exchange 2013 and with their mailboxes put on In-Place Hold is controlled by Exchange. The only qualification is for conferencing files, which are stored on the Lync Server file share. These files are purged from the file share only after the files have been exported (uploaded to Exchange), if you select the option to purge data after the archiving data has been exported, or after the specified maximum number of days, if you specify a maximum number of days for retention.

    
    </div>

By default, no archiving options are enabled. You can manage Archiving configurations using Lync Server 2013 Control Panel.

You can specify the following Archiving configurations:

  - **Global Archiving configuration**. This is the default Archiving configuration and applies to your entire deployment. It is created when you deploy Lync Server 2013 and, by default, does not enable archiving functionality. You can modify the global configuration, but you cannot delete it. If you choose the delete option for the configuration, the global configuration is reset to the default settings.

  - **Site Archiving configuration**. Optionally, you can configure Archiving for one or more specific sites by creating and configuring a site-level Archiving configuration for an individual site. A site-level Archiving configuration exists only if you create it. You can modify or delete any site-level Archiving configuration. A site-level Archiving configuration overrides the global configuration, but only for the site specified in the site-level configuration. For example, if you enable Archiving for only IM in your global configuration and create a site configuration in which you enable Archiving for both IM and conferencing, conferencing would only be archived for the site, not for the remainder of your organization.

  - **Pool Archiving configuration**. Optionally, you can specify Archiving settings for one or more specific pools by creating and configuring a pool-level configuration for the individual pool. A pool-level Archiving configuration exists only if you create it. You can modify and delete any pool-level Archiving configuration. A pool-level Archiving configuration overrides the global configuration and any site archiving configuration you may have created. For example, if you enable Archiving for only IM in your global configuration, create a site-level configuration in which you enable Archiving for both IM and conferencing for the site, and then create a pool-level configuration in which you enable Archiving only for IM, the communications would be archived for both IM and conferencing for all users of the site except the users homed in the pool specified in the pool-level configuration. For all other users in your organization, Archiving would be enabled only for IM.

For details about how to set up initial Archiving configurations when you deploy Archiving, see [Configuring Archiving options in Lync Server 2013](lync-server-2013-configuring-archiving-options.md) in the Deployment documentation. For details about using Archiving policies to enable and disable communications after deployment, see [Managing Archiving configuration options in Lync Server 2013 for your organization, sites, and pools](lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md) in the Operations documentation.

</div>

<div>

## Archiving Options Available Only in Windows PowerShell

Using Lync Server 2013 Management Shell, you can use cmdlets to implement options that are not available in Lync Server 2013 Control Panel. These options include the following:

  - **Archive duplicate messages**. For details, see [New-CsArchivingConfiguration](https://docs.microsoft.com/powershell/module/skype/New-CsArchivingConfiguration) and [Set-CsArchivingConfiguration](https://docs.microsoft.com/powershell/module/skype/Set-CsArchivingConfiguration) in the Operations documentation.

  - **Export archived data**. For details, see [Export-CsArchivingData](https://docs.microsoft.com/powershell/module/skype/Export-CsArchivingData)

</div>

</div>

</div>

<div>

## How Do I Access Archived Data?

Access to archived data is dependent on where the data is stored:

  - **Microsoft Exchange storage**. If you choose the Exchange integration option, Lync Server deposits the archiving content in the Exchange 2013 store for all users who are homed on Exchange 2013, and who have had their mailboxes put on In-Place Hold. Archived data is stored in user mailboxes Recoverable items folder, which is generally invisible to users, and can only be searched by users with an Exchange **Discovery Management** role. Exchange enables federated search and discovery, along with SharePoint, if it is deployed. For more details about storage, retention, and discovery of data stored in Exchange, see the Exchange 2013 and SharePoint documentation.

  - **Lync Server storage**. If you set up Lync Server 2013 Archiving databases for storage of Lync Server data, Lync Server deposits archiving content in the Lync Server Archiving databases (SQL Server databases) for any users not homed on Exchange 2013, and who have not had their mailboxes put on In-Place Hold. This data is not searchable, but it can be exported to formats that are searchable using other tools. For details about exporting data stored in Archiving databases, see [Exporting archived data from Lync Server 2013](lync-server-2013-exporting-archived-data.md) in the Operations documentation.

For more details about how Lync Server 2013 and Exchange 2013 work together, see [Exchange Server and SharePoint integration support in Lync Server 2013](lync-server-2013-exchange-and-sharepoint-integration-support.md) in the Supportability documentation.

</div>

</div>

<span> </span>

</div>

</div>

</div>

