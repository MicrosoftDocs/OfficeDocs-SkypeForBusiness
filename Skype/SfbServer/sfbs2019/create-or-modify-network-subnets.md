---
title: "Create or modify network subnets in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1ba8c4e3-fbc7-4758-88ac-d651fef17bed
description: "A network subnet must be associated with a network site for the purposes of determining the geographic location of the host belonging to this subnet. You can use Lync Server Control Panel to configure subnets. From the Lync Server Control Panel, you can create, modify, or delete a network subnet. For details about deleting network subnets, see Deleting network subnets in Lync Server 2013."
---

# Create or modify network subnets in Lync Server 2013
[]
A network subnet must be associated with a network site for the purposes of determining the geographic location of the host belonging to this subnet. You can use Lync Server Control Panel to configure subnets. From the Lync Server Control Panel, you can create, modify, or delete a network subnet. For details about deleting network subnets, see [Deleting network subnets in Lync Server 2013](deleting-network-subnets.md).
  
In most deployments of Microsoft Lync Server 2013 where call admission control (CAC) is implemented, there will typically be a large number of subnets. Because of this, it is often best to configure subnets from the Lync Server Management Shell. From there you can call **New-CsNetworkSubnet** in conjunction with the Windows PowerShell cmdlet **Import-CSV**. By using these cmdlets together, you can read in subnet settings from a comma-separated values (.csv) file and create multiple subnets at the same time. For examples of how to create subnets from a .csv file, see [New-CsNetworkSubnet](new-csnetworksubnet.md).
  
### To create a network subnet

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Network Configuration** and then click **Subnet**.
    
4. On the **Subnet** page, click **New**. 
    
5. In **New Subnet**, enter a value in the **Subnet ID** field. This must be an IP address (for example, 174.11.12.0), and it must be the first address in the IP address range defined by the subnet. 
    
6. In the **Mask** field, enter a numeric value from 1 through 32. 
    
    > [!NOTE]
    > This value is the bitmask that is to be applied to the subnet being created. 
  
7. In **Network site ID**, select the site to which this subnet belongs.
    
8. (Optional) Type a value in the **Description** field to provide more information about this subnet that cannot be expressed by the name alone. 
    
9. Click **Commit**.
    
### To modify a network subnet

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Network Configuration** and then click **Subnet**.
    
4. On the **Subnet** page, click the subnet that you want to modify. 
    
5. On the **Edit** menu, click **Show details**. 
    
6. On the **Edit Subnet** page, you can modify the bitmask, associated network site, or description. If you modify the bitmask, keep in mind that the Subnet ID must still be the first address in the IP address range defined by the subnet. 
    
7. Click **Commit**.
    
## See also

#### 

[Deleting network subnets in Lync Server 2013](deleting-network-subnets.md)
#### 

[About network regions, sites, and subnets in Lync Server 2013](about-network-regions-sites-and-subnets.md)
#### 

[New-CsNetworkSubnet](new-csnetworksubnet.md)
  
[Set-CsNetworkSubnet](set-csnetworksubnet.md)
  
[Remove-CsNetworkSubnet](remove-csnetworksubnet.md)
  
[Get-CsNetworkSubnet](get-csnetworksubnet.md)

