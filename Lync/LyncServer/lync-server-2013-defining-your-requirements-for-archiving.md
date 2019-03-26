---
title: 'Lync Server 2013: Defining your requirements for Archiving'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Defining your organization's requirements for Archiving
ms:assetid: ce0fc0f6-7704-4b80-bf19-a1fa9818fc7a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205276(v=OCS.15)
ms:contentKeyID: 48185462
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Defining your requirements for Archiving in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-09_

If your organization must follow compliance regulations, you can deploy Archiving to enable archiving support for Lync Server 2013 instant messaging (IM) and conferencing (meetings). For details about the type of content that can be archived, see [Overview of Archiving in Lync Server 2013](lync-server-2013-overview-of-archiving.md) in the Planning documentation.

To implement Archiving, you need to first decide how to meet your organization’s requirements for Archiving. This requires determining the following:

  - **When to deploy Archiving**. You can deploy Archiving as part of your initial Lync Server 2013 deployment, or you can add it to an existing deployment. You deploy Archiving by using Topology Builder to add it to your topology, and then publishing the topology.

  - **Whether to archive internal or external communications**. You can enable archiving for internal communications (communications between internal users), external communications (communications that include at least one user outside your internal network), or both. You can specify these options for your entire organization, or you can specify them for specific sites and pools. By default, neither option is enabled.
    
    <div>
    

    > [!NOTE]  
    > If you use Microsoft Exchange integration to store archived data, your Exchange settings control whether Lync communications are archived. If your deployment includes multiple forests, you must synchronize the settings between Lync Server and Exchange. Controlling archiving for internal or external communications is only available for Lync Policy. For Exchange-integrated archiving, both of them will be archived or not archived.

    
    </div>

  - **Why enable Archiving**. You can enable and disable Archiving for your entire deployment at a global level, and you can enable and disable Archiving for specific sites and users. At each of these levels, you specify whether to enable archiving of IM sessions (peer-to-peer), conferences (meetings, which are multiparty sessions), or both. By default, Archiving is disabled.

  - **How critical Archiving is to users in your organization**. If archiving is mission-critical in your organization, you can specify that Lync Server 2013 run in critical mode, which blocks IM and conferencing sessions if archiving fails. For example:
    
      - If the Archiving service is temporarily unable to send a message to the database queue or insert a message into the database), both IM and conferencing functionality are blocked in the deployment until archiving support is restored.
    
      - If a conferencing user uploads a file, but the file cannot be copied to the archiving file store, conferencing functionality is blocked in the deployment until the problem is resolved, but IM functionality is not blocked.
    
    You can configure this option at the global level, site level, and pool level. By default, critical mode is not enabled.

  - **Whether to use Microsoft Exchange integration**. This option integrates Archiving storage with your Exchange 2013 storage, so that your Lync Server archived data and Exchange 2013 archived data are stored together in Exchange. You can use Microsoft Exchange integration for storage of archiving data for users who are homed on Exchange 2013, if their mailboxes have been put on In-Place Hold. If you do not have an Exchange 2013 deployment, or if you prefer not to integrate with it, or if you have any Lync users who are not homed on Exchange 2013, you can deploy separate Archiving databases by using SQL Server to store archived data from Lync communications. You can configure the Microsoft Exchange integration option at the global level, site level, and pool level. By default, Microsoft Exchange integration is not enabled.

  - **How archived data is to be managed**. The archiving database is not intended for long-term retention and Lync Server 2013 does not provide an e-discovery (search) solution for archived data, so data needs to be moved to other storage. Lync Server does provide a session export tool that you can use to export archived data, and which creates searchable transcripts of the archived data. For the global policy, and for each site and user policy that you create, you can enable data purging and specify one of the following options:
    
      - Purge both exported archiving data and stored archiving data after a specific number of days. The minimum number of days that you can specify is one day. The maximum number of days that you can specify is 2562 days.
    
      - Purge exported archiving data only. This option purges all records that have been exported and marked as safe to delete by the session export tool.
    
    You can configure this option at the global level, site level, and pool level. By default, purging is not enabled.

You control Archiving by using the following methods:

  - **Archiving policies**. You use one or more Archiving policies to enable and disable archiving of internal and external communications. By default, no archiving is enabled. You enable or disable Archiving for internal communications, external communications, or both in your deployment by using the default global policy. You cannot delete the global policy. You can specify one or more optional site policies to enable or disable Archiving for internal and external communications for specific sites. You can also specify one or more user policies to enable or disable Archiving for specific users and user groups. User-level policies override site policies. Site-level policies override the global-level policies. User-level policies are implemented only for the specific users who are configured to use the policy. Group instant messages and conferences are archived only if a policy for at least one of the participants is configured to enable archiving.
    
    <div>
    

    > [!NOTE]  
    > If you use Microsoft Exchange integration, Exchange 2013 policies override Lync Server Archiving policies for all users homed on the Exchange 2013 servers.

    
    </div>

  - **Archiving configurations**. You use one or more Archiving configurations to specify most of the Archiving options that are described previously in this topic, except for enabling archiving of internal and external communications (configured using Archiving policies, as described in the previous bullet). Archiving configurations include the default global configuration and optional site and pool configurations. You cannot delete the global configuration. Pool-level configurations override site-level configurations. Site-level configurations override the global-level configuration.

As part of your requirements analysis, you need to determine how to configure the global Archiving configuration and global Archiving policy. You also need to determine your requirements for any site-level Archiving configurations, pool-level Archiving configurations, site-level Archiving policies, and user-level Archiving policies.

If you deploy Archiving for one Front End pool or Standard Edition server, you should then enable it for all other Front End pools and Standard Edition servers in your deployment. You need to do this because users whose communications are required to be archived can be invited to a group IM conversation or meetings hosted on a different pool. If archiving is not enabled on the pool where the conversation or meeting is hosted, all conference data may not be archived. Archiving will still work for archiving enabled users and all IM messages, but conferencing content and events may not be archived.

<div>


> [!NOTE]  
> To enable delegation of administrative tasks while maintaining your organization's security standards, Lync Server 2013&nbsp;uses role-based access control (RBAC). With RBAC, administrative privilege is granted by assigning users to predefined administrative roles. To configure Lync Archiving policies and Archiving configurations, the user must be assigned to the CsArchivingAdministrator role (unless the configuration is done directly on the server where Archiving is deployed, instead of remotely from another computer). For details about RBAC, see <A href="lync-server-2013-planning-for-role-based-access-control.md">Planning for role-based access control in Lync Server 2013</A> in the Planning documentation. For a list of the user rights, permissions, and roles required for archiving deployment, see <A href="lync-server-2013-deployment-checklist-for-archiving.md">Deployment checklist for Archiving in Lync Server 2013</A>, which is available in both the Planning documentation and the Deployment documentation.<BR>If you use Microsoft Exchange integration, configuration of Exchange policies requires appropriate administrator rights and permissions. For details, see the Exchange 2013 documentation.



</div>

</div>

<span> </span>

</div>

</div>

</div>

