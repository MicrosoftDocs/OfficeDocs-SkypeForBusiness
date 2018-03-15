---
title: "Viewing network region route information in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 34dd9fa3-e695-4680-b244-3019298b5009
description: "Every region within a call admission control (CAC) configuration must have some way to access every other region. While region links set bandwidth limitations on the connections between regions and also represent the physical links, a route determines which linked path the connection will traverse from one region to another. Use the following procedures to view existing network region routes in Lync Server 2013 Control Panel or Lync Server 2013 Management Shell. For details about creating or modifying network region routes, see Creating or modifying network region routes in Lync Server 2013."
---

# Viewing network region route information in Lync Server 2013
[]
Every region within a call admission control (CAC) configuration must have some way to access every other region. While region links set bandwidth limitations on the connections between regions and also represent the physical links, a route determines which linked path the connection will traverse from one region to another. Use the following procedures to view existing network region routes in Lync Server 2013 Control Panel or Lync Server 2013 Management Shell. For details about creating or modifying network region routes, see [Creating or modifying network region routes in Lync Server 2013](creating-or-modifying-network-region-routes.md).
  
### To view network region route information in Lync Server Control Panel

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Network Configuration** and then click **Region Route**.
    
4. On the **Region Route** page, click the region route that you want to view. 
    
    > [!NOTE]
    > You can only view one region route at a time. 
  
5. On the **Edit** menu, click **Show details**.
    
## Viewing Network Region Route Information by Using Windows PowerShell Cmdlets

Network region route information can be viewed by using Windows PowerShell and the Get-CsNetworkInterRegionRoute cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To view network region route information

- To view information about all your network region routes, type the following command in the Lync Server Management Shell and then press ENTER:
    
  ```
  Get-CsNetworkInterRegionRoute
  ```

    That will return information similar to this:
    
  ```
  Identity                  : TransAmericaRoute
  NetworkRegionLinks        : {NorthwestToNortheast}
  InterNetworkRegionRouteID : TransAmericaRoute
  NetworkRegionID1          : Pacific Northwest
  NetworkRegionID2          : Northeast
  
  ```

For more information, see the help topic for the [Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md) cmdlet. 
  
## See also

#### 

[Creating or modifying network region routes in Lync Server 2013](creating-or-modifying-network-region-routes.md)
  
[Deleting existing network region routes in Lync Server 2013](deleting-existing-network-region-routes.md)

