---
title: "Viewing network region information in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 665740d0-a3ed-460f-8337-5ed945f90589
description: "A network region interconnects various parts of a network across multiple geographic areas. Every network region must be associated with a central site. The central site is the data center site on which the call admission control (CAC) bandwidth policy service is running. You can use Lync Server Control Panel to view network regions. Network regions include settings that determine whether alternate paths through the Internet are allowed for audio and video connections. Use this topic to view existing network regions. For details about creating or modifying existing network regions, see Creating or modifying network regions in Lync Server 2013."
---

# Viewing network region information in Lync Server 2013
[]
A network region interconnects various parts of a network across multiple geographic areas. Every network region must be associated with a central site. The central site is the data center site on which the call admission control (CAC) bandwidth policy service is running. You can use Lync Server Control Panel to view network regions. Network regions include settings that determine whether alternate paths through the Internet are allowed for audio and video connections. Use this topic to view existing network regions. For details about creating or modifying existing network regions, see [Creating or modifying network regions in Lync Server 2013](creating-or-modifying-network-regions.md).
  
### To view information about a network region with Lync Server Control Panel

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Network Configuration** and then click **Region**.
    
4. On the **Region** page, click the region you want to view. 
    
    > [!NOTE]
    > You can only view one region at a time. 
  
5. On the **Edit** menu, click **Show details**.
    
## Viewing Network Region Information by Using Windows PowerShell Cmdlets

You can view network region information by using Windows PowerShell and the **Get-CsNetworkRegion** cmdlet. You can run this cmdlet either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To view network region information

- To view information about all your network regions, type the following command in the Lync Server Management Shell and then press ENTER:
    
  ```
  Get-CsNetworkRegion
  ```

    That will return information similar to this:
    
  ```
  Identity         : Pacific Northwest
  Description      :
  BypassID         : 3b232b84-2c1d-4da2-8181-e9330bafebe9
  CentralSite      : Site:Redmond1
  BWAlternatePaths : {BWPolicyModality=Audio;AlternatePath=True, 
                     BWPolicyModality=Video;AlternatePath=True}
  NetworkRegionID  : Pacific Northwest
  
  ```

For more information, see the help topic for the [Get-CsNetworkRegion](get-csnetworkregion.md) cmdlet. 
  
## See also

#### 

[Creating or modifying network regions in Lync Server 2013](creating-or-modifying-network-regions.md)
  
[Deleting existing network regions in Lync Server 2013](deleting-existing-network-regions.md)

