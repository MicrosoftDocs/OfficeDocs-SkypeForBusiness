---
title: 'Lync Server 2013: Create or modify a network region'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Create or modify a network region
ms:assetid: bf7a3dc4-71a2-4559-a547-d90305d4f904
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412933(v=OCS.15)
ms:contentKeyID: 48185281
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create or modify a network region in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-19_

*Network regions* are the network hubs or backbones used in the configuration of call admission control, E9-1-1, and media bypass. Use the following procedures to create or modify network regions. For example, if you have already created network regions for one Voice feature, you do not need to create new network regions; other advanced Enterprise Voice features will use those same network regions. You may, however, need to modify an existing network region definition to apply feature-specific settings. For example, if you have created network regions for E9-1-1 (which do not require an associated central site) and you then deploy call admission control, you need to modify the network region definitions to specify a central site. For details, see [Configure network regions for CAC in Lync Server 2013](lync-server-2013-configure-network-regions-for-cac.md).

<div>


> [!NOTE]  
> Any feature-specific requirements for network region definitions are documented in the Deployment topics for the feature.



</div>

For details about working with network regions, see the Lync Server Management Shell documentation for the following cmdlets:

  - [New-CsNetworkRegion](https://docs.microsoft.com/powershell/module/skype/New-CsNetworkRegion)

  - [Get-CsNetworkRegion](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkRegionLink)

  - [Set-CsNetworkRegion](https://docs.microsoft.com/powershell/module/skype/Set-CsNetworkRegion)

  - [Remove-CsNetworkRegion](https://docs.microsoft.com/powershell/module/skype/Remove-CsNetworkRegion)

<div>

## Create a Network Region

Create a network region that can be used by call admission control, E9-1-1, or media bypass.

<div>

## To create a network region using Lync Server Management Shell

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Run the New-CsNetworkRegion cmdlet to create network regions:
    
        New-CsNetworkRegion -Identity <String> -CentralSite <String>
    
    For example:
    
        New-CsNetworkRegion -Identity NorthAmerica -CentralSite CHICAGO -Description "All North America Locations"
    
    In this example, you created a network region called “NorthAmerica” that is associated with a central site with site ID CHICAGO.

3.  To finish creating network regions for your topology, repeat step 2 with settings for each network region.

</div>

<div>

## To create a network region using Lync Server Control Panel

1.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

2.  In the left navigation bar, click **Network Configuration**.

3.  Click **Region**.

4.  Click **New**.

5.  On the **New Region** page, click **Name** and then type a name for the network region.

6.  Click **Central site**, and then click a central site in the list.

7.  Optionally, click **Description**, and then type additional information to describe this network site.

8.  Click **Commit**.

9.  To finish creating network regions for your topology, repeat steps 4 through 8 with settings for other regions.

</div>

</div>

<div>

## Modify a Network Region

Modify settings for an existing network region to accommodate changes to the basic region information or changes required by a new feature.

<div>

## To modify a network region using Lync Server Management Shell

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Run the Set-CsNetworkRegion cmdlet to modify an existing network region:
    
        Set-CsNetworkRegion -Identity <String> -CentralSite <String>
    
    For example:
    
        Set-CsNetworkRegion -Identity NorthAmerica -CentralSite CHICAGO -Description "North American Region"
    
    In this example, you modified an existing network region called “NorthAmerica” (created using the procedures earlier in this topic) by changing the description. If a description existed for the “NorthAmerica” region, this command overwrites it with this value; if no description had been set, then this command sets it.

3.  To modify other network regions, repeat step 2 with settings for other regions.

</div>

<div>

## To modify a network region using Lync Server Control Panel

1.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

2.  In the left navigation bar, click **Network Configuration**.

3.  Click the **Region** navigation button.

4.  In the table, click the network region that you want to modify.

5.  Click **Edit**, and then click **Show details…**.

6.  On the **Edit Region** page, change the values for this network region’s settings as appropriate.

7.  Click **Commit**.

8.  To finish modify network regions, repeat steps 4 through 7 with settings for other regions.

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

