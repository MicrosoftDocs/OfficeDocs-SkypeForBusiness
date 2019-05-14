---
title: 'Lync Server 2013: Defining your requirements for monitoring'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Defining your organizations's requirements for monitoring
ms:assetid: d587ff04-9af6-4ac1-ad42-076e7a40ac75
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205284(v=OCS.15)
ms:contentKeyID: 48185491
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Defining your requirements for monitoring in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-05_

Streamlining the deployment and installation of monitoring in Microsoft Lync Server 2013 has also streamlined the processes involved in defining your organization's requirements for monitoring. Nevertheless, there are still several key issues that should be addressed before you begin to install and configure Lync Server 2013:

**What type of data do you want to monitor?** Lync Server 2013 enables you to monitor two different types of data: call detailing recording (CDR) data and Quality of Experience (QoE) data. Call detail recording provides a way for you to track the usage of Lync Server features such as Voice over IP (VoIP) phone calls; instant messaging (IM); file transfers; audio/video (A/V) conferencing; and application sharing sessions. This information helps you know which Lync Server features are being used (and which ones are not) and also provides information as to when these features are being used. Quality of Experience data allows you to maintain a record of the quality of audio and video calls made in your organization, including such things as the number of network packets lost, background noise, and the amount of "jitter" (differences in packet delay).

If you choose to enable monitoring in Lync Server 2013 you can enable both CDR monitoring and QoE monitoring, or you can choose to enable one type of monitoring while leaving the other type disabled. For example, suppose your users only use instant messaging and file transfers, and do not make audio or video calls. In that case, there might be little reason to enable QoE monitoring. Likewise, Lync Server makes it easy to enable and disable monitoring after monitoring has been deployed. For example, you might choose to deploy monitoring but initially leave QoE monitoring disabled. If your users begin to experience problems with audio or video calls you could then enable QoE monitoring and use that data to help you troubleshoot and resolve those problems.

There is no particular advantage (or disadvantage) to installing monitoring at the same time you install Lync Server vs. installing monitoring after Lync Server has been installed. The one point to keep in mind is that, before you install monitoring, you must select a computer to host the backend monitoring store, and a supported version of SQL Server must be installing and configured on that computer before that computer can be used for monitoring. If you have already installed SQL Server on a computer and that computer is ready for use then you can install monitoring at the same time you install Lync Server. If you do not have a backend computer ready then you can proceed to install Lync Server by itself, then install monitoring whenever the backend computer is ready for use.

**When do you want to install monitoring?** Monitoring can be installed and configured at the same time you install and configured Lync Server 2013; the Lync Server Deployment Wizard will provide you with the opportunity to associate your Front End pools with a monitoring database during setup. Alternatively, you can install monitoring after Lync Server itself has been installed; this can be done by using Topology Builder to associate your Front End pools and servers with a monitoring database, and then publishing the revised topology.

**How many backend monitoring databases do you need?** A single monitoring database can support tens of thousands of users (for Microsoft Lync Server 2010, it was estimated that a collocated database for both monitoring and archiving could support 240,000 users). In addition, a single monitoring database can be used by multiple Front End pools; if you have three Front End pools in your organization then you could associate all three of those pools with the same backend store.

This simply means that, for many organizations, database capacity will not be the deciding factor when determining the number of backend monitoring databases that will be required. Instead, a more important consideration could be network speed. Suppose you have three Front End pools, but one of those pools is located across a slow network connection. In that case, you might want to use two monitoring databases: one database to service the two pools with the good network connection, and a separate database to service the pool with the slower network connection.

When planning your monitoring infrastructure you should also take into account that Lync Server 2013 supports the use of mirror databases. "Database mirroring" provides a way for you to simultaneously maintain two copies of a database, with each database residing on a different server. Any time data is written to a primary database that same data is also written to the mirror database. If the primary database should fail or otherwise become unavailable, you can "fail over" to the mirror database by using a simple Lync Server PowerShell command. For example:

    Invoke-CsDatabaseFailover -PoolFqdn atl-cs-001.litwareinc.com -DatabaseType "Monitoring" -NewPrincipal "Mirror"

This is important for planning purposes simply because mirroring will require you to double your required number of databases: in addition to each primary database you will need a second database to act as the mirror.

**Do your Lync Server sites need their own custom monitoring configurations?** When you install Lync Server 2013 you also install global collections of CDR and QoE configuration settings; these global collections give you the ability to apply the same CDR and QoE settings to your entire organization. In many cases, this will be sufficient: often-times you will want, say, to have CDR monitoring enabled for all of your users.

However, there might also be times when you want to apply different settings to different sites. For example, perhaps you want to use both CDR and QoE monitoring in your Redmond site, but only use CDR monitoring in your Dublin site. Likewise, you might want to retain monitoring data for 60 days in the Redmond site but only need to maintain this type of data for 30 days in the Dublin site. Lync Server 2013 allows you to create separate collections of CDR and QoE configuration settings at the site scope; that enables you to manage each site differently. (This includes both enabling and disabling monitoring as well as configuring management settings such as how long data is to be retained.)

Note that you can make this decision before you deploy monitoring or after you deploy monitoring. For example, you can deploy monitoring and then manage the entire organization by using the global settings. If you later change your mind, you can create a separate collection of settings for, say, the Redmond site, and then use those settings to manage monitoring for Redmond. (Settings applied at the site scope always take precedence over settings applied at the global scope.) If you change your mind again, you can simply delete the configuration settings applied to the Redmond site. When a collection of site settings is removed then the global collection of settings will automatically be applied to that site.

</div>

<span> </span>

</div>

</div>

</div>

