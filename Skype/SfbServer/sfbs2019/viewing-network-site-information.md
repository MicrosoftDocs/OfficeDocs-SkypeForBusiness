---
title: "Viewing network site information in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 24a97d98-b168-4016-81bf-c2c478092b87
description: "Network sites are the offices or locations configured within each region of a call admission control (CAC) or Enhanced 9-1-1 deployment. You can view network site information in either Lync Server 2013 Control Panel or Lync Server Management Shell . For details about creating or modifying network sites, see Creating or modifying network sites in Lync Server 2013."
---

# Viewing network site information in Lync Server 2013
[]
Network sites are the offices or locations configured within each region of a call admission control (CAC) or Enhanced 9-1-1 deployment. You can view network site information in either Lync Server 2013 Control Panel or Lync Server Management Shell . For details about creating or modifying network sites, see [Creating or modifying network sites in Lync Server 2013](creating-or-modifying-network-sites.md).
  
### To view network site information in Lync Server Control Panel

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Network Configuration** and then click **Site**.
    
4. On the **Site** page, click the site that you want to view. 
    
    > [!NOTE]
    > You can only view information for one site at a time. 
  
5. On the **Edit** menu, click **Show details**.
    
## Viewing Network Site Information by Using Windows PowerShell Cmdlets

You can view network site information by using Windows PowerShell and the Get-CsNetworkSite cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To view network site information

- To view information about all your network sites, type the following command in the Lync Server Management Shell and then press ENTER:
    
  ```
  Get-CsNetworkSite
  ```

    That will return information similar to this:
    
  ```
  Identity          : Redmond
  NetworkSiteID     : Redmond
  Description       :
  NetworkRegionID   : Pacific Northwest
  BypassID          : 3b232b84-2c1d-4da2-8181-e9330bafebe9
  BWPolicyProfileID :
  LocationPolicy    :
  
  ```

For more information, see the help topic for the [Get-CsNetworkSite](get-csnetworksite.md) cmdlet. 
  
## See also

#### 

[Creating or modifying network sites in Lync Server 2013](creating-or-modifying-network-sites.md)
  
[Deleting an existing network site in Lync Server 2013](deleting-an-existing-network-site.md)

