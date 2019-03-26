---
title: 'Lync Server 2013: Creating or modifying network region routes'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Creating or modifying network region routes
ms:assetid: 76993daa-76c2-4cec-8363-de8aebef0145
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg521016(v=OCS.15)
ms:contentKeyID: 48184540
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Creating or modifying network region routes in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-08_

Every region within a call admission control (CAC) configuration must have some way to access every other region. While region links set bandwidth limitations on the connections between regions and also represent the physical links, a route determines which linked path the connection will traverse from one region to another. You can use Lync Server Control Panel to configure network region routes. From Lync Server Control Panel, you can create, modify, or delete a network region route. Use this topic to create or modify a network region route. For details about deleting an existing network region routes, see [Deleting existing network region routes in Lync Server 2013](lync-server-2013-deleting-existing-network-region-routes.md).

<div>

## To create a network region route

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Network Configuration** and then click **Region Route**.

4.  On the **Region Route** page, click **New**.

5.  In **New Region Route**, type a value in the **Name** field.
    
    <div>
    

    > [!NOTE]  
    > This value must be unique within your Microsoft Lync Server 2013 deployment.

    
    </div>

6.  From the **Network region \#1** drop-down list, select one of the two regions to be connected by this route.

7.  From the **Network region \#2** drop-down list, select the other region for this route. This region must be different from the region selected for Network region \#1.

8.  Use the **Network region links** list box to add region links to the route. Click the **Add** button to display the **Region Link** page. Click a region link to add to this route, and then click **OK**.
    
    <div>
    

    > [!NOTE]  
    > Continue to click the <STRONG>Add</STRONG> button to add more links, or select a link and click <STRONG>Remove</STRONG> to remove a link.

    
    </div>

9.  Click **Commit**.

</div>

<div>

## To modify a network region route

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Network Configuration** and then click **Region Route**.

4.  On the **Region Route** page, click the region route that you want to modify.

5.  On the **Edit** menu, click **Show details**.

6.  In **Edit Region Route**, you can modify the regions joined by this route and the region links associated with the route.

7.  Click **Commit**.

</div>

<div>

## See Also


[Deleting existing network region routes in Lync Server 2013](lync-server-2013-deleting-existing-network-region-routes.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

