---
title: 'Lync Server 2013: Creating an Archiving configuration to manage Archiving for specific sites or pools'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Creating an Archiving configuration to manage Archiving for specific sites or pools
ms:assetid: c5c864a6-96c7-4bbb-ab7c-61eb1744246c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205251(v=OCS.15)
ms:contentKeyID: 48185361
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Creating an Archiving configuration in Lync Server 2013 to manage Archiving for specific sites or pools

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

In Lync Server 2013 Control Panel, you use Archiving configurations to control how archiving is implemented in your deployment. This includes the following Archiving configurations:

  - A global configuration that is created by default when you deploy Lync Server 2013.

  - Optional site-level and pool-level configurations that you can create and use to specify how archiving is implemented for specific sites or pools.

You initially set up Archiving configurations when you deploy Archiving, but you can change, add, and delete configurations after deployment. For details about how Archiving configurations are implemented, including which options you can specify and the hierarchy of Archiving configurations, see [How Archiving works in Lync Server 2013](lync-server-2013-how-archiving-works.md) in the Planning documentation, Deployment documentation, or Operations documentation.

<div>


> [!NOTE]  
> To use archiving, you must configure Archiving policies to specify whether to enable archiving for internal communications, for external communications, or for both for users homed on Lync Server 2013. By default, archiving is not enabled for either internal or external communications. Before enabling Archiving in any policies, you should specify the appropriate Archiving configurations for your deployment and, optionally, for specific sites and pools, as described in this section. For details about enabling Archiving, see <A href="lync-server-2013-configuring-and-assigning-archiving-policies.md">Configuring and assigning Archiving policies in Lync Server 2013</A> in the Deployment documentation.<BR>If you decide after you deploy Archiving that you want to use Microsoft Exchange integration to store archiving data and files on Exchange 2013 servers and all your users are homed on your Exchange 2013 servers, you should remove the SQL Server database configuration from your topology. You must use Topology Builder to do this. For details, see <A href="lync-server-2013-changing-archiving-database-options.md">Changing Archiving database options in Lync Server 2013</A> in the Operations documentation.



</div>

<div>

## To create an archiving configuration for a site or pool

1.  From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Configuration**.

4.  On the **Archiving Configuration** page, click **New**, and then do one of the following:
    
      - To create a site archiving configuration, click **Site Configuration** and then, in **Select a site**, select the site to be configured for archiving.
    
      - To create a pool archiving configuration, click **Pool Configuration** and then, in **Select a pool**, select the pool to be configured for archiving.

5.  In **New Archiving Setting**, in the **Archiving setting** drop-down list box, do one of the following:
    
      - To enable archiving only for instant messaging (IM) sessions, click **Archive IM sessions**.
    
      - To enable archiving for both IM sessions and web conferences, click **Archive IM and web conferencing sessions**.
    
      - To disable archiving for the policy, click **Disable archiving**.

6.  Also in **New Archiving Setting**, do the following:
    
      - To block activity when archiving is not available, select the **Block instant messaging (IM) or web conferencing sessions if archiving fails** check box.
    
      - To use Microsoft Exchange Server to store archiving data, click the **Microsoft Exchange integration** check box.
    
      - To enable data purging, select the **Enable purging of archiving data** check box, and then do one of the following:
        
          - To specify purging after a specific number of days, click **Purge exported archiving data and stored archiving data after maximum duration (days)**, and then specify the number of days.
        
          - To limit purging to archiving data that has been exported, click **Purge exported archiving data only**.

7.  Click **Commit**.

</div>

<div>

## Creating Archiving Configuration Settings by Using Windows PowerShell Cmdlets

Archiving configuration settings can be created by using Windows PowerShell and the New-CsArchivingConfiguration cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To create a new collection of archiving configuration settings for a site

  - The following command creates a new collection of archiving configuration settings for the Redmond site:
    
        New-CsArchivingConfiguration -Identity "site:Redmond"

</div>

<div>

## To create a new collection of archiving configuration settings that only allow IM archiving

  - Because no parameters (other than the mandatory Identity parameter) were specified in the preceding command, the new collection of configuration settings will use the default values for all its properties. To create settings that use different property values, simply include the appropriate parameter and parameter value. For example, to create a collection of archiving configuration settings that, by default, allow archiving of instant messaging sessions, only use a command like this:
    
        New-CsArchivingConfiguration -Identity "site:Redmond" -EnableArchiving "ImOnly"

</div>

<div>

## To specify multiple property values when creating archiving configuration settings

  - Multiple property values can be modified by including multiple parameters. For example, this command configures the new settings to archive instant messaging sessions and to block instant messaging of the archiving service is not available:
    
        New-CsArchivingConfiguration -Identity "site:Redmond" -EnableArchiving "ImOnly" -BlockOnArchiveFailure $True

</div>

For more information, see the help topic for the [New-CsArchivingConfiguration](https://docs.microsoft.com/powershell/module/skype/New-CsArchivingConfiguration) cmdlet.

</div>

<div>

## See Also


[How Archiving works in Lync Server 2013](lync-server-2013-how-archiving-works.md)  


[Managing Archiving configuration options in Lync Server 2013 for your organization, sites, and pools](lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

