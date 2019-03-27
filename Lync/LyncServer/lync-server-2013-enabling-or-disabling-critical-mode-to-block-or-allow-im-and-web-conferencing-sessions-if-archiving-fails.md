---
title: 'Lync Server 2013: Enabling or disabling critical mode to block or allow IM and web conferencing sessions if Archiving fails'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Enabling or disabling critical mode to block or allow IM and web conferencing sessions if Archiving fails
ms:assetid: fafdcd2e-b778-4ed5-a25f-09208aa3b699
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182609(v=OCS.15)
ms:contentKeyID: 48185927
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enabling or disabling critical mode in Lync Server 2013 to block or allow IM and web conferencing sessions if Archiving fails

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

In Lync Server 2013 Control Panel, you use Archiving configurations to enable and disable critical mode. This includes the following Archiving configurations:

  - A global configuration that is created by default when you deploy Lync Server 2013.

  - Optional site-level and pool-level configurations that you can create and use to specify how archiving is implemented for specific sites or pools.

You initially set up Archiving configurations when you deploy Archiving, but you can change, add, and delete configurations after deployment. For details about how Archiving configurations are implemented, including which options you can specify and the hierarchy of Archiving configurations, see [How Archiving works in Lync Server 2013](lync-server-2013-how-archiving-works.md) in the Planning documentation, Deployment documentation, or Operations documentation.

<div>


> [!NOTE]  
> To use archiving, you must configure Archiving policies to specify whether to enable archiving for internal communications, for external communications, or for both for users homed on Lync Server 2013. By default, archiving is not enabled for either internal or external communications. Prior to enabling Archiving in any policies, you should specify the appropriate Archiving configurations for your deployment and, optionally, for specific sites and pools, as described in this section. For details about enabling Archiving, see <A href="lync-server-2013-configuring-and-assigning-archiving-policies.md">Configuring and assigning Archiving policies in Lync Server 2013</A> in the Deployment documentation.<BR>If you decide after you deploy Archiving that you want to use Exchange Server integration to store archiving data and files on Exchange 2013 servers and all your users are homed on your Exchange 2013 servers, you should remove the SQL Server database configuration from your topology. You must use Topology Builder to do this. For details, see <A href="lync-server-2013-changing-archiving-database-options.md">Changing Archiving database options in Lync Server 2013</A> in the Operations documentation.



</div>

<div>

## To enable or disable blocking of IM and web conferencing sessions if archiving fails

1.  From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Configuration**.

4.  Click the name of the appropriate global, site, or pool configuration in the list of archiving configurations, click **Edit**, click **Show details**, and then do the following:

5.  To set how archiving behaves when a failure occurs, select or clear the **Block instant messaging (IM) or web conferencing sessions if archiving fails** check box.

6.  Click **Commit**.

</div>

<div>

## Enabling and Disabling Critical Mode by Using Windows PowerShell Cmdlets

You can enable or disable critical mode using the **Set-CsArchivingConfiguration** cmdlet. You can run this cmdlet from either the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To enable critical mode

  - To enable critical mode, set the value of the BlockOnArchiveFailure property to True ($True). For example:
    
        Set-CsArchivingConfiguration -Identity "site:Redmond" -BlockOnArchiveFailure $True

</div>

<div>

## To disable critical mode

  - To disable critical mode, set the value of the BlockOnArchiveFailure property to False ($False). For example:
    
        Set-CsArchivingConfiguration -Identity "site:Redmond" -BlockOnArchiveFailure $False

</div>

For more information, see the Help topic for the [Set-CsArchivingConfiguration](https://docs.microsoft.com/powershell/module/skype/Set-CsArchivingConfiguration) cmdlet.

</div>

<div>

## See Also


[Changing Archiving database options in Lync Server 2013](lync-server-2013-changing-archiving-database-options.md)  


[How Archiving works in Lync Server 2013](lync-server-2013-how-archiving-works.md)  


[Managing Archiving configuration options in Lync Server 2013 for your organization, sites, and pools](lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

