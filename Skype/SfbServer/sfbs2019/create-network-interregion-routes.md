---
title: "Create network interregion routes in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5555262a-a502-4b01-9593-836dd30064f5
description: "A network interregion route defines the route between a pair of network regions. Each pair of network regions in your call admission control deployment requires a network interregion route. This enables every network region within the deployment to access every other region."
---

# Create network interregion routes in Lync Server 2013
[]
A network interregion route defines the route between a pair of network regions. Each pair of network regions in your call admission control deployment requires a network interregion route. This enables every network region within the deployment to access every other region. 
  
While region links set bandwidth limitations on the connections between regions, an interregion route determines which linked path the connection will traverse from one region to another.
  
For details about working with network interregion routes, see the Lync Server Management Shell documentation for the following cmdlets:
  
- [New-CsNetworkInterRegionRoute](new-csnetworkinterregionroute.md)
    
- [Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)
    
- [Set-CsNetworkInterRegionRoute](set-csnetworkinterregionroute.md)
    
- [Remove-CsNetworkInterRegionRoute](remove-csnetworkinterregionroute.md)
    
In the example topology, network interregion routes must be defined for each of the three region pairs: North America/EMEA, EMEA/APAC, and North America/APAC.
  
### To create network interregion routes by using Lync Server Management Shell

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Run the **New-CsNetworkInterRegionRoute** cmdlet to define the required routes. For example, run: 
    
  ```
  New-CsNetworkInterRegionRoute -Identity NorthAmerica_EMEA_Route -NetworkRegionID1 NorthAmerica -NetworkRegionID2 EMEA -NetworkRegionLinkIDs "NA-EMEA-LINK"
  ```

  ```
  New-CsNetworkInterRegionRoute -Identity NorthAmerica_APAC_Route -NetworkRegionID1 NorthAmerica -NetworkRegionID2 APAC -NetworkRegionLinkIDs "NA-EMEA-LINK, EMEA-APAC-LINK"
  ```

  ```
  New-CsNetworkInterRegionRoute -Identity EMEA_APAC_Route -NetworkRegionID1 EMEA -NetworkRegionID2 APAC -NetworkRegionLinkIDs "EMEA-APAC-LINK"
  ```

    > [!NOTE]
    > The North America/APAC network interregion route requires two network region links because there is no direct network region link between them. 
  
### To create network interregion routes by using Lync Server Control Panel

1. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
2. In the left navigation bar, click **Network Configuration**.
    
3. Click the **Region Route** navigation button. 
    
4. Click **New**.
    
5. On the **New Region Route** page, click **Name** and then type a name for the network interregion route. 
    
6. Click **Network Region #1**, and then click a network region in the list that you want to route to Network Region #2.
    
7. Click **Network Region #2**, and then click a network region in the list that you want to route to Network Region #1.
    
8. Click **Add** beside the **Network Region Links** field, and then add a network region link that will be used in the network interregion route. 
    
    > [!NOTE]
    > If you are creating a route for two network regions that do not have a direct network region link between them, you must add all the necessary links to complete the route. For example, the North America/APAC network interregion route requires two network region links because there is no direct network region link between them. 
  
9. Click **Commit**.
    
10. To finish creating network interregion routes for your topology, repeat steps 4 through 9 with settings for other network interregion routes.
    

