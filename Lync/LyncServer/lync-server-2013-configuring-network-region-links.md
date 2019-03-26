---
title: 'Lync Server 2013: Configuring network region links'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configuring network region links
ms:assetid: 952bc93e-e6aa-4539-85c7-2b15f14eb382
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182551(v=OCS.15)
ms:contentKeyID: 48184829
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring network region links in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

You can configure links between two network regions as part of call admission control (CAC). Regions within a network are linked through physical wide area network (WAN) connectivity. You can use the Lync Server Control Panel to define a link between two network regions and set the bandwidth limitations on audio and video connections between these regions. For details about deleting an existing network region link, see [Deleting network region links in Lync Server 2013](lync-server-2013-deleting-network-region-links.md).

<div>

## To create a network region link

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Network Configuration** and then click **Region Link**.

4.  On the **Region Link** page, click **New**.

5.  In **New Region Link**, type a value in the **Name** field.
    
    <div>
    

    > [!NOTE]  
    > This value must be unique within your Lync Server 2013 deployment.

    
    </div>

6.  From the **Network region \#1** drop-down list, select one of the two regions to be linked.

7.  From the **Network region \#2** drop-down list, select the other region to be linked. This region must be different from the region selected for Network region \#1.

8.  (Optional) If you want to place bandwidth limitations on audio or video calls between these regions, select a bandwidth policy profile from the **Bandwidth policy** drop-down list.

9.  Click **Commit**.

</div>

<div>

## To modify a network region link

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Network Configuration** and then click **Region Link**.

4.  On the **Region Link** page, click the region link that you want to modify.

5.  On the **Edit** menu, click **Show details**.

6.  In **Edit Region Link**, you can modify the regions that are linked or the bandwidth policy profile for this link.

7.  Click **Commit**.

</div>

<div>

## See Also


[Deleting network region links in Lync Server 2013](lync-server-2013-deleting-network-region-links.md)  


[New-CsNetworkRegionLink](https://docs.microsoft.com/powershell/module/skype/New-CsNetworkRegionLink)  
[Set-CsNetworkRegionLink](https://docs.microsoft.com/powershell/module/skype/Set-CsNetworkRegionLink)  
[Remove-CsNetworkRegionLink](https://docs.microsoft.com/powershell/module/skype/Remove-CsNetworkRegionLink)  
[Get-CsNetworkRegionLink](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkRegionLink)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>
