---
title: 'Lync Server 2013: Managing Archiving configuration options for your organization, sites, and pools'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Managing Archiving configuration options for your organization, sites, and pools
ms:assetid: 377a6f80-5f2b-4bc1-b507-e930a461fb1d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204802(v=OCS.15)
ms:contentKeyID: 48183830
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Managing Archiving configuration options in Lync Server 2013 for your organization, sites, and pools

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

In Lync Server 2013 Control Panel, you use Archiving configurations to specify how archiving is implemented. This includes the following Archiving configurations:

  - A global configuration that is created by default when you deploy Lync Server 2013.

  - Optional site-level and pool-level configurations that you can create and use to specify how archiving is implemented for specific sites or pools.

You initially set up Archiving configurations when you deploy Archiving, but you can change, add, and delete configurations after deployment. In Lync Server 2013 Control Panel, you can use the **Archiving Configuration** page of the **Archiving and Monitoring** group to manage configurations at the global level, site level, and pool level. For details about how Archiving configurations are implemented, including which options you can specify, and the hierarchy of Archiving configurations, see [How Archiving works in Lync Server 2013](lync-server-2013-how-archiving-works.md) in the Planning documentation, Deployment documentation, or Operations documentation.

<div>


> [!NOTE]  
> To use archiving, you must configure Archiving policies to specify whether to enable archiving for internal communications, for external communications, or for both for all users homed on Lync Server 2013. By default, archiving is not enabled for either internal or external communications. If you use Microsoft Exchange integration, you must enable and configure Exchange 2013 to support archiving for all users homed on Exchange 2013 who have had their mailboxes put on In-Place Hold.<BR>Prior to enabling Archiving, you should specify the appropriate Archiving configurations for your deployment and, optionally, for specific sites and pools, as described in this section. For details about enabling Archiving, see <A href="lync-server-2013-configuring-and-assigning-archiving-policies.md">Configuring and assigning Archiving policies in Lync Server 2013</A> in the Deployment documentation.



</div>

**To view archiving configuration information by using Windows PowerShell cmdlets**

  - You can view Archiving configuration information by using Windows PowerShell and the **Get-CsArchivingConfiguration** cmdlet. You can run this cmdlet from either the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).
    
    In the Lync Server Management Shell, use the following command to view information about all of your archiving configuration settings:
    
        Get-CsArchivingConfiguration

<div>

## In This Section

  - [Creating an Archiving configuration in Lync Server 2013 to manage Archiving for specific sites or pools](lync-server-2013-creating-an-archiving-configuration-to-manage-archiving-for-specific-sites-or-pools.md)

  - [Enabling or disabling Archiving of IM or conferencing sessions in Lync Server 2013](lync-server-2013-enabling-or-disabling-archiving-of-im-or-conferencing-sessions.md)

  - [Enabling or disabling the purging of archived data in Lync Server 2013](lync-server-2013-enabling-or-disabling-the-purging-of-archived-data.md)

  - [Enabling or disabling critical mode in Lync Server 2013 to block or allow IM and web conferencing sessions if Archiving fails](lync-server-2013-enabling-or-disabling-critical-mode-to-block-or-allow-im-and-web-conferencing-sessions-if-archiving-fails.md)

  - [Enable or disable sending an Archiving disclaimer to federated partners in Lync Server 2013](lync-server-2013-enable-or-disable-sending-an-archiving-disclaimer-to-federated-partners.md)

  - [Enabling or disabling integration of Lync Server 2013 with Exchange storage](lync-server-2013-enabling-or-disabling-integration-with-exchange-storage.md)

  - [Deleting an Archiving configuration in Lync Server 2013](lync-server-2013-deleting-an-archiving-configuration.md)

</div>

<div>

## See Also


[Managing Lync Server 2013 Archiving](lync-server-2013-managing-archiving.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

