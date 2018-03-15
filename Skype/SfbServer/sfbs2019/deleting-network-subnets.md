---
title: "Deleting network subnets in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c1850f38-40a3-48c9-b6f1-f181c5e63b6b
description: "You can use the following procedure to delete a subnet. From the Lync Server Control Panel, you can create, modify, or delete a network subnet. For details on creating or modifying network subnets, see Create or modify network subnets in Lync Server 2013."
---

# Deleting network subnets in Lync Server 2013
[]
You can use the following procedure to delete a subnet. From the Lync Server Control Panel, you can create, modify, or delete a network subnet. For details on creating or modifying network subnets, see [Create or modify network subnets in Lync Server 2013](create-or-modify-network-subnets.md).
  
In most deployments of Microsoft Lync Server 2013 where call admission control (CAC) is implemented, there will typically be a large number of subnets. Because of this, it is often best to configure subnets from the Lync Server Management Shell. From there you can call **New-CsNetworkSubnet** in conjunction with the Windows PowerShell cmdlet **Import-CSV**. By using these cmdlets together, you can read in subnet settings from a comma-separated values (.csv) file and create multiple subnets at the same time. For examples of how to create subnets from a .csv file, see [New-CsNetworkSubnet](new-csnetworksubnet.md).
  
### To delete a network subnet

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Network Configuration** and then click **Subnet**.
    
4. On the **Subnet** page, click the subnet that you want to delete. 
    
    > [!NOTE]
    > You can delete more than one subnet at a time. To do this, press CTRL and select multiple subnets while holding down the CTRL key. Or, to select all subnets, click **Select all** on the **Edit** menu. 
  
5. On the **Edit** menu, click **Delete**.
    
6. Click **OK**.
    
## See also

#### 

[Create or modify network subnets in Lync Server 2013](create-or-modify-network-subnets.md)

