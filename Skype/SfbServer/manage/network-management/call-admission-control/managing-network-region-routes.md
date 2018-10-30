---
title: ''
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: ""
---

# Managing network region routes in Skype for Business Server

A *network region route* defines the route between a pair of network regions. Each pair of network regions in your call admission control deployment requires a network region route. This enables every network region within the deployment to access every other region. Use the procedures in this artilce to view, create, modify, or delete network region routes.

## View network region route information in Lync Server 2013

Every region within a call admission control (CAC) configuration must have some way to access every other region. While region links set bandwidth limitations on the connections between regions and also represent the physical links, a route determines which linked path the connection will traverse from one region to another. Use the following procedures to view existing network region routes in Lync Server 2013 Control Panel or Lync Server 2013 Management Shell. For details about creating or modifying network region routes, see [Creating or modifying network region routes in Lync Server 2013](lync-server-2013-creating-or-modifying-network-region-routes.md).

<div>

### To view network region route information in Lync Server Control Panel

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Network Configuration** and then click **Region Route**.

4.  On the **Region Route** page, click the region route that you want to view.
    
    <div>
    

    > [!NOTE]  
    > You can only view one region route at a time.

    
    </div>

5.  On the **Edit** menu, click **Show details**.

</div>

<div>

### Viewing Network Region Route Information by Using Windows PowerShell Cmdlets

Network region route information can be viewed by using Windows PowerShell and the Get-CsNetworkInterRegionRoute cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

### To view network region route information

  - To view information about all your network region routes, type the following command in the Lync Server Management Shell and then press ENTER:
    
        Get-CsNetworkInterRegionRoute
    
    That will return information similar to this:
    
        Identity                  : TransAmericaRoute
        NetworkRegionLinks        : {NorthwestToNortheast}
        InterNetworkRegionRouteID : TransAmericaRoute
        NetworkRegionID1          : Pacific Northwest
        NetworkRegionID2          : Northeast

</div>

For more information, see the help topic for the [Get-CsNetworkInterRegionRoute](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkInterRegionRoute) cmdlet.


## Create or modify network region routes in Lync Server 2013


Every region within a call admission control (CAC) configuration must have some way to access every other region. While region links set bandwidth limitations on the connections between regions and also represent the physical links, a route determines which linked path the connection will traverse from one region to another. You can use Lync Server Control Panel to configure network region routes. From Lync Server Control Panel, you can create, modify, or delete a network region route. Use this topic to create or modify a network region route. For details about deleting an existing network region routes, see [Deleting existing network region routes in Lync Server 2013](lync-server-2013-deleting-existing-network-region-routes.md).

<div>

### To create a network region route

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

### To modify a network region route

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Network Configuration** and then click **Region Route**.

4.  On the **Region Route** page, click the region route that you want to modify.

5.  On the **Edit** menu, click **Show details**.

6.  In **Edit Region Route**, you can modify the regions joined by this route and the region links associated with the route.

7.  Click **Commit**.


## Delete existing network region routes in Lync Server 2013


Every region within a call admission control (CAC) configuration must have some way to access every other region. While region links set bandwidth limitations on the connections between regions and also represent the physical links, a route determines which linked path the connection will traverse from one region to another. You can use Lync Server Control Panel to configure network region routes. From Lync Server Control Panel, you can create, modify, or delete a network region route. Use this topic to delete existing network region routes. For details about creating or modifying network region routes, see [Creating or modifying network region routes in Lync Server 2013](lync-server-2013-creating-or-modifying-network-region-routes.md).

<div>

### To delete a network region route

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Network Configuration** and then click **Region Route**.

4.  On the **Region Route** page, click the region route that you want to delete.
    
    <div>
    

    > [!NOTE]  
    > You can delete more than one region route at a time. To do this, press CTRL and select multiple region routes while holding down the CTRL key. Or, to select all region routes, click <STRONG>Select all</STRONG> on the <STRONG>Edit</STRONG> menu.

    
    </div>

5.  On the **Edit** menu, click **Delete**.

6.  Click **OK**.



## See Also

Managing network regions 


[New-CsNetworkInterRegionRoute](https://docs.microsoft.com/powershell/module/skype/New-CsNetworkInterRegionRoute)  
[Set-CsNetworkInterRegionRoute](https://docs.microsoft.com/powershell/module/skype/Set-CsNetworkInterRegionRoute)  
[Remove-CsNetworkInterRegionRoute](https://docs.microsoft.com/powershell/module/skype/Remove-CsNetworkInterRegionRoute)  
[Get-CsNetworkInterRegionRoute](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkInterRegionRoute)  