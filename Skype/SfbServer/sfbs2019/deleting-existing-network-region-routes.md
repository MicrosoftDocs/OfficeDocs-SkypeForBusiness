---
title: "Deleting existing network region routes in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6256ff80-5f1e-48b4-928b-24aeb3c1a0e7
description: "Every region within a call admission control (CAC) configuration must have some way to access every other region. While region links set bandwidth limitations on the connections between regions and also represent the physical links, a route determines which linked path the connection will traverse from one region to another. You can use Lync Server Control Panel to configure network region routes. From Lync Server Control Panel, you can create, modify, or delete a network region route. Use this topic to delete existing network region routes. For details about creating or modifying network region routes, see Creating or modifying network region routes in Lync Server 2013."
---

# Deleting existing network region routes in Lync Server 2013
[]
Every region within a call admission control (CAC) configuration must have some way to access every other region. While region links set bandwidth limitations on the connections between regions and also represent the physical links, a route determines which linked path the connection will traverse from one region to another. You can use Lync Server Control Panel to configure network region routes. From Lync Server Control Panel, you can create, modify, or delete a network region route. Use this topic to delete existing network region routes. For details about creating or modifying network region routes, see [Creating or modifying network region routes in Lync Server 2013](creating-or-modifying-network-region-routes.md).
  
### To delete a network region route

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Network Configuration** and then click **Region Route**.
    
4. On the **Region Route** page, click the region route that you want to delete. 
    
    > [!NOTE]
    > You can delete more than one region route at a time. To do this, press CTRL and select multiple region routes while holding down the CTRL key. Or, to select all region routes, click **Select all** on the **Edit** menu. 
  
5. On the **Edit** menu, click **Delete**.
    
6. Click **OK**.
    
## See also

#### 

[Creating or modifying network region routes in Lync Server 2013](creating-or-modifying-network-region-routes.md)
#### 

[Configure a Network Region Route](configure-a-network-region-route.md)
#### 

[New-CsNetworkInterRegionRoute](new-csnetworkinterregionroute.md)
  
[Set-CsNetworkInterRegionRoute](set-csnetworkinterregionroute.md)
  
[Remove-CsNetworkInterRegionRoute](remove-csnetworkinterregionroute.md)
  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)

