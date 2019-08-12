---
title: 'Lync Server 2013: Create or modify a network site'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Create or modify a network site
ms:assetid: 14e24856-9996-4da4-9f31-300940bdf5aa
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398218(v=OCS.15)
ms:contentKeyID: 48183488
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create or modify a network site in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-24_

Call admission control (CAC), E9-1-1, and media bypass deployments rely on the configuration of *network sites* which are defined within and always associated with a network region. A network site represents a branch office location, a set of buildings, or a campus. Network sites represent collections of subnets with similar bandwidth.

Use the following procedures to create or modify network sites. For example, if you have already created network sites for one Voice feature, you do not need to create new network sites; other Voice features will use those same sites. You may, however, need to modify an existing network site definition to apply feature-specific settings. For example, if you created a network site for E9-1-1, you need to modify the network site during deployment of call admission control to apply a bandwidth policy profile.

<div>


> [!NOTE]  
> Where they exist, you can find specific examples and requirements for network sites as they pertain to an advanced Voice feature in the Deployment documentation for each feature: 
> <UL>
> <LI>
> <P><A href="lync-server-2013-configure-network-sites-for-cac.md">Configure network sites for CAC in Lync Server 2013</A></P></LI></UL>



</div>

For details about working with network sites, see the Lync Server Management Shell documentation for the following cmdlets:

  - [New-CsNetworkSite](https://docs.microsoft.com/powershell/module/skype/New-CsNetworkSite)

  - [Get-CsNetworkSite](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkSite)

  - [Set-CsNetworkSite](https://docs.microsoft.com/powershell/module/skype/Set-CsNetworkSite)

  - [Remove-CsNetworkSite](https://docs.microsoft.com/powershell/module/skype/Remove-CsNetworkSite)

<div>

## Create a Network Site

Create a network region that can be used by call admission control, E9-1-1, or media bypass.

<div>

## To create a network site by using Management Shell

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Run the New-CsNetworkSite cmdlet to create network sites:
    
        New-CsNetworkSite -NetworkSiteID <string>
    
    For example:
    
        New-CsNetworkSite -NetworkSiteID Chicago -Description "Corporate headquarters"-NetworkRegionID NorthAmerica
    
    In this example, you created a network site called “Chicago” that is in the “NorthAmerica” network region.
    
    <div>
    

    > [!NOTE]  
    > The NorthAmerica network region must already exist for this command to run successfully.

    
    </div>

3.  To finish creating network sites for your topology, repeat step 2 with settings for other sites.

</div>

<div>

## To create a network site by using Lync Server Control Panel

1.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

2.  In the left navigation bar, click **Network Configuration**.

3.  Click the **Site** navigation button.

4.  Click **New**.

5.  On the **New Site** page, click **Name** and then type a name for the network site.

6.  Click **Region**, and then click a region in the list.

7.  Optionally, click **Bandwidth policy**, and then click a bandwidth policy in the list.
    
    <div>
    

    > [!NOTE]  
    > Bandwidth policy is required only if you deploy call admission control at the site.

    
    </div>

8.  Optionally, click **Location policy**, and then click a location policy in the list.
    
    <div>
    

    > [!NOTE]  
    > Location policy is required only if you deploy E9-1-1 at the site.

    
    </div>

9.  Optionally, click **Description**, and then type additional information to describe this network site.

10. Click **Commit**.

11. To finish creating network sites for your topology, repeat steps 4 through 10 with settings for other sites.

</div>

</div>

<div>

## Modify a Network Site

Modify a network region that can be used by call admission control, E9-1-1, or media bypass.

<div>

## To modify a network site

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Run the Set-CsNetworkSite cmdlet to modify network sites:
    
        Set-CsNetworkSite -Identity <string>
    
    For example:
    
        Set-CsNetworkSite -Identity Albuquerque -NetworkRegionID NorthAmerica
    
    In this example, the site called “Albuquerque” is moved to the “NorthAmerica” network region. To modify the network site configuration to deploy call admission control, E9-1-1, or media bypass, modify the network site settings by running the Set-CsNetworkSite cmdlet with the BWPolicyProfileID or LocationPolicy parameter, respectively.
    
    <div>
    

    > [!NOTE]  
    > Although the BypassID parameter exists for media bypass, we strongly recommend that you do not override automatically generated bypass IDs. You do not need to specify additional parameters to configure a network site for media bypass.

    
    </div>

3.  To finish modifying network sites for your topology, repeat step 2 with settings for other sites.

</div>

<div>

## To modify a network site by using Lync Server Control Panel

1.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

2.  In the left navigation bar, click **Network Configuration**.

3.  Click the **Site** navigation button.

4.  In the table, click the network site that you want to modify.

5.  Click **Edit**, and then click **Show details…**.

6.  On the **Edit Site** page, change the values for this network site’s settings as appropriate.

7.  Click **Commit**.

8.  To finish modify network sites, repeat steps 4 through 7 with settings for other sites.

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

