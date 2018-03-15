---
title: "Create network region links in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f8163910-8935-475d-88a2-3aa44feb9dbe
description: "Regions within a network are linked through physical WAN connectivity. A network region link creates a link between two regions configured for call admission control (CAC) and sets the bandwidth limitations on audio and video traffic between these regions."
---

# Create network region links in Lync Server 2013
[]
Regions within a network are linked through physical WAN connectivity. A network region link creates a link between two regions configured for call admission control (CAC) and sets the bandwidth limitations on audio and video traffic between these regions. 
  
For details about working with network region links, see the Lync Server Management Shell documentation for the following cmdlets:
  
- [New-CsNetworkRegionLink](new-csnetworkregionlink.md)
    
- [Get-CsNetworkRegionLink](get-csnetworkregionlink.md)
    
- [Set-CsNetworkRegionLink](set-csnetworkregionlink.md)
    
- [Remove-CsNetworkRegionLink](remove-csnetworkregionlink.md)
    
The example topology has a link between the North America and APAC regions, and a link between the EMEA and APAC regions. Each of these region links is constrained by WAN bandwidth, as described in Region Link Bandwidth Information table in the [Example: Gathering your requirements for call admission control in Lync Server 2013](example-gathering-your-organization-s-requirements-for-call-admission-control.md) section of the Planning documentation. 
  
### To create network region links by using Lync Server Management Shell

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Run the New-CsNetworkRegionLink cmdlet to create the region links and apply appropriate bandwidth policy profiles. For example, run:
    
  ```
  New-CsNetworkRegionLink -NetworkRegionLinkID NA-EMEA-LINK -NetworkRegionID1 NorthAmerica -NetworkRegionID2 EMEA -BWPolicyProfileID 50Mb_Link
  ```

  ```
  New-CsNetworkRegionLink -NetworkRegionLinkID EMEA-APAC-LINK -NetworkRegionID1 EMEA -NetworkRegionID2 APAC -BWPolicyProfileID 25Mb_Link
  ```

### To create network region links by using Lync Server Control Panel

1. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
2. In the left navigation bar, click **Network Configuration**.
    
3. Click the **Region Link** navigation button. 
    
4. Click **New**.
    
5. On the **New Region Link** page, click **Name** and then type a name for the network region link. 
    
6. Click **Network Region #1**, and then click the network region in the list that you want to link to Network Region #2.
    
7. Click **Network Region #2**, and then click a network region in the list that you want to link to Network Region #1.
    
8. Optionally, click **Bandwidth policy**, and then select the bandwidth policy profile that you want to apply to the network region link.
    
    > [!NOTE]
    > Apply a bandwidth policy only if the network region link is bandwidth-constrained and you want to use CAC to control media traffic on that link. 
  
9. Click **Commit**.
    
10. To finish creating network region links for your topology, repeat steps 4 through 9 with settings for other regions.
    

