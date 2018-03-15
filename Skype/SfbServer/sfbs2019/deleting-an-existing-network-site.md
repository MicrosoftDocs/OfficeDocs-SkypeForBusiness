---
title: "Deleting an existing network site in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2762149b-3572-4513-b838-beda7fa9e81e
description: "Network sites are the offices or locations configured within each region of a call admission control (CAC) or Enhanced 9-1-1 deployment. You can use the Lync Server 2013 Control Panel to configure sites and associate them with regions. For example, a network region for North America might be associated with networks sites such as Chicago, Redmond, and Vancouver. A CAC network site must be created for every site within an organization, even if that site has no bandwidth limitations. From the Lync Server Control Panel you can create, modify, and delete network sites. Use the following procedure to delete an existing network site. For details about creating or modifying network sites, see Creating or modifying network sites in Lync Server 2013"
---

# Deleting an existing network site in Lync Server 2013
[]
Network sites are the offices or locations configured within each region of a call admission control (CAC) or Enhanced 9-1-1 deployment. You can use the Lync Server 2013 Control Panel to configure sites and associate them with regions. For example, a network region for North America might be associated with networks sites such as Chicago, Redmond, and Vancouver. A CAC network site must be created for every site within an organization, even if that site has no bandwidth limitations. From the Lync Server Control Panel you can create, modify, and delete network sites. Use the following procedure to delete an existing network site. For details about creating or modifying network sites, see [Creating or modifying network sites in Lync Server 2013](creating-or-modifying-network-sites.md)
  
### To delete a network site

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Network Configuration** and then click **Site**.
    
4. On the **Site** page, click the site that you want to delete. 
    
    > [!NOTE]
    > You can delete more than one site at a time. To do this, press CTRL and select multiple sites while holding down the CTRL key. Or, to select all sites, click **Select all** on the **Edit** menu. 
  
5. On the **Edit** menu, click **Delete**.
    
6. Click **OK**.
    
    > [!CAUTION]
    > You cannot remove a network site if it is associated with a network subnet. If you attempt to remove a site associated with a subnet you will receive an error message. To see if a site is associated with any subnets, click the site and then click **Show details** on the **Edit** menu. 
  

