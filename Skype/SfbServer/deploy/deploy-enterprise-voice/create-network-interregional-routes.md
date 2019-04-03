---
title: "Create network interregional routes in Skype for Business Server"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: 5555262a-a502-4b01-9593-836dd30064f5
description: "Create or modify network interregional routes, which are used by Enterprise Voice call admission control in Skype for Business Server."
---

# Create network interregional routes in Skype for Business Server
 
Create or modify network interregional routes, which are used by Enterprise Voice call admission control in Skype for Business Server. 
  
A network interregional route defines the route between a pair of network regions. Each pair of network regions in your call admission control deployment requires a network interregional route. This enables every network region within the deployment to access every other region.
  
While region links set bandwidth limitations on the connections between regions, an interregional route determines which linked path the connection will traverse from one region to another.
  
In the example topology, network interregional routes must be defined for each of the three region pairs: North America/EMEA, EMEA/APAC, and North America/APAC. 
  
### To create network interregional routes by using Skype for Business Server Management Shell

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
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
    > The North America/APAC network interregional route requires two network region links because there is no direct network region link between them. 
  
### To create network interregional routes by using Skype for Business Server Control Panel

1. Open Skype for Business Server Control Panel.
    
2. In the left navigation bar, click **Network Configuration**.
    
3. Click the **Region Route** navigation button.
    
4. Click **New**.
    
5. On the **New Region Route** page, click **Name** and then type a name for the network interregional route.
    
6. Click **Network Region #1**, and then click a network region in the list that you want to route to Network Region #2.
    
7. Click **Network Region #2**, and then click a network region in the list that you want to route to Network Region #1.
    
8. Click **Add** beside the **Network Region Links** field, and then add a network region link that will be used in the network interregional route.
    
    > [!NOTE]
    > If you are creating a route for two network regions that do not have a direct network region link between them, you must add all the necessary links to complete the route. For example, the North America/APAC network interregional route requires two network region links because there is no direct network region link between them. 
  
9. Click **Commit**.
    
10. To finish creating network interregional routes for your topology, repeat steps 4 through 9 with settings for other network interregional routes.
    
## See also

[New-CsNetworkInterRegionRoute](https://docs.microsoft.com/powershell/module/skype/new-csnetworkinterregionroute?view=skype-ps)
  
[Get-CsNetworkInterRegionRoute](https://docs.microsoft.com/powershell/module/skype/get-csnetworkinterregionroute?view=skype-ps)
  
[Set-CsNetworkInterRegionRoute](https://docs.microsoft.com/powershell/module/skype/set-csnetworkinterregionroute?view=skype-ps)
  
[Remove-CsNetworkInterRegionRoute](https://docs.microsoft.com/powershell/module/skype/remove-csnetworkinterregionroute?view=skype-ps)
