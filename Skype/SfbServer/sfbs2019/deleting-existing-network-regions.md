---
title: "Deleting existing network regions in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c7293a2f-2b49-4c4a-903f-f7edcea2bc5f
description: "A network region interconnects various parts of a network across multiple geographic areas. Every network region must be associated with a central site. The central site is the data center site on which the call admission control (CAC) bandwidth policy service is running. You can use Lync Server Control Panel to configure network regions. Network regions include settings that determine whether alternate paths through the Internet are allowed for audio and video connections. From the Lync Server Control Panel, you can create, modify, or delete a network region. Use this topic to delete existing network regions. For details about creating or modifying existing network regions, see Creating or modifying network regions in Lync Server 2013."
---

# Deleting existing network regions in Lync Server 2013
[]
A network region interconnects various parts of a network across multiple geographic areas. Every network region must be associated with a central site. The central site is the data center site on which the call admission control (CAC) bandwidth policy service is running. You can use Lync Server Control Panel to configure network regions. Network regions include settings that determine whether alternate paths through the Internet are allowed for audio and video connections. From the Lync Server Control Panel, you can create, modify, or delete a network region. Use this topic to delete existing network regions. For details about creating or modifying existing network regions, see [Creating or modifying network regions in Lync Server 2013](creating-or-modifying-network-regions.md).
  
### To delete a network region

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Network Configuration** and then click **Region**.
    
4. On the **Region** page, click the region you want to delete. 
    
    > [!NOTE]
    > You can delete more than one region at a time. To do this, press CTRL and select multiple regions while holding down the CTRL key. Or, to select all regions, click **Select all** on the **Edit** menu. 
  
5. On the **Edit** menu, click **Delete**.
    
6. Click **OK**.
    
    > [!CAUTION]
    > A network region cannot be removed if it is associated with a network site. If you attempt to remove a region associated with a site you will receive an error message. To see if a region is associated with any sites, select the region and then click **Show details** on the **Edit** menu. 
  
## See also

#### 

[Creating or modifying network regions in Lync Server 2013](creating-or-modifying-network-regions.md)

