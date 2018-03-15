---
title: "Viewing network region link information in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7b6b2ea2-83d8-4376-afb2-70e5d2cf6444
description: "You can view links between two network regions as part of call admission control (CAC). Regions within a network are linked through physical wide area network (WAN) connectivity. You can use the Lync Server Control Panel to view an existing link between two network regions. For details about creating or modifying network region link, see Configuring network region links in Lync Server 2013."
---

# Viewing network region link information in Lync Server 2013
[]
You can view links between two network regions as part of call admission control (CAC). Regions within a network are linked through physical wide area network (WAN) connectivity. You can use the Lync Server Control Panel to view an existing link between two network regions. For details about creating or modifying network region link, see [Configuring network region links in Lync Server 2013](configuring-network-region-links.md).
  
### To view a network region link in Lync Server Control Panel

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Network Configuration** and then click **Region Link**.
    
4. On the **Region Link** page, click the region link that you want to view. 
    
    > [!NOTE]
    > You can only view information about one region link at a time. 
  
5. From the **Edit** menu, select **Show details**.
    
## Viewing Network Region Link Information by Using Windows PowerShell Cmdlets

You can view network region links by using Windows PowerShell and the **Get-CsNetworkRegionLink** cmdlet. You can run this cmdlet from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To view network region link information

- To view information about all your network region links, type the following command in the Lync Server Management Shell and then press ENTER:
    
  ```
  Get-CsNetworkRegionLink
  ```

    This command returns information similar to the following:
    
  ```
  Identity            : NorthwestToCalifornia
  BWPolicyProfileID   :
  NetworkRegionLinkID : NorthwestToCalifornia
  NetworkRegionID1    : Pacific Northwest
  NetworkRegionID2    : California
  ```

For details, see [Get-CsNetworkRegionLink](get-csnetworkregionlink.md).
  
## See also

#### 

[Configuring network site links in Lync Server 2013](configuring-network-site-links.md)

