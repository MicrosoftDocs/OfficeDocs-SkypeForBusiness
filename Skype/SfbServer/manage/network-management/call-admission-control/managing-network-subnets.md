---
title: 'Managing network subnets'
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "In most deployments of Skype for Business Server where call admission control (CAC) is implemented, there will typically be a large number of subnets. Because of this, it is often best to configure subnets from the Skype for Business Server Management Shell."
---

# Managing network subnets in Skype for Business Server

You can use either the Skype for Business Server Control Panel or the Skype for Business Server Management Shell to manage network subnets. In most deployments of Skype for Business Server where call admission control (CAC) is implemented, there will typically be a large number of subnets. Because of this, it is often best to configure subnets from the Skype for Business Server Management Shell.

Use the sections in this article to view network subnet information or create, modify, or delete network subnets. 

## View network subnet information 

You can use the following procedure to view a network subnet. From the Skype for Business Server Control Panel, you can create, modify, or delete a network subnet. 

### To view a network subnet

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Network Configuration**, and then click **Subnet**.

4.  On the **Subnet** page, click the subnet that you want to view.
 
    > [!NOTE]  
    > You can only view one subnet at a time.

5.  On the **Edit** menu, click **Show details**.

### View network subnet configuration information by Using Windows PowerShell cmdlets

Network subnet information can be viewed by using Windows PowerShell and the Get-CsNetworkSubnet cmdlet. This cmdlet can be run either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. 

### To view network subnet information

  - To view information about all your network subnets, type the following command in the Skype for Business Server Management Shell and then press ENTER:
    
        Get-CsNetworkSubnet
    
    That will return information similar to this:
    
        Identity      : 172.11.15.0
        MaskBits      : 28
        Description   :
        NetworkSiteID : Redmond
        SubnetID      : 172.11.15.0


For more information, see the help topic for the [Get-CsNetworkSubnet](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkSubnet) cmdlet.


## Create or modify network subnets 

A network subnet must be associated with a network site for the purposes of determining the geographic location of the host belonging to this subnet. You can use the Skype for Business Server Control Panel to configure subnets. From the Skype for Business Server Control Panel, you can create, modify, or delete a network subnet. 

In most deployments of Skype for Business Server where call admission control (CAC) is implemented, there will typically be a large number of subnets. Because of this, it is often best to configure subnets from the Skype for Business Server Management Shell. From there you can call **New-CsNetworkSubnet** in conjunction with the Windows PowerShell cmdlet **Import-CSV**. By using these cmdlets together, you can read in subnet settings from a comma-separated values (.csv) file and create multiple subnets at the same time. For examples of how to create subnets from a .csv file, see [New-CsNetworkSubnet](https://docs.microsoft.com/powershell/module/skype/New-CsNetworkSubnet).


### To create a network subnet

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Network Configuration**, and then click **Subnet**.

4.  On the **Subnet** page, click **New**.

5.  In **New Subnet**, enter a value in the **Subnet ID** field. This must be an IP address (for example, 174.11.12.0), and it must be the first address in the IP address range defined by the subnet.

6.  In the **Mask** field, enter a numeric value from 1 through 32.

    > [!NOTE]  
    > This value is the bitmask that is to be applied to the subnet being created.

7.  In **Network site ID**, select the site to which this subnet belongs.

8.  (Optional) Type a value in the **Description** field to provide more information about this subnet that cannot be expressed by the name alone.

9.  Click **Commit**.


### To modify a network subnet

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Network Configuration**, and then click **Subnet**.

4.  On the **Subnet** page, click the subnet that you want to modify.

5.  On the **Edit** menu, click **Show details**.

6.  On the **Edit Subnet** page, you can modify the bitmask, associated network site, or description. If you modify the bitmask, keep in mind that the Subnet ID must still be the first address in the IP address range defined by the subnet.

7.  Click **Commit**.

## Delete network subnets

You can use the following procedure to delete a subnet. From the Skype for Business Server Control Panel, you can create, modify, or delete a network subnet. 

In most deployments of Skype for Business Server where call admission control (CAC) is implemented, there will typically be a large number of subnets. Because of this, it is often best to configure subnets from the Skype for Business Server Management Shell. From there you can call **New-CsNetworkSubnet** in conjunction with the Windows PowerShell cmdlet **Import-CSV**. By using these cmdlets together, you can read in subnet settings from a comma-separated values (.csv) file and create multiple subnets at the same time. For examples of how to create subnets from a .csv file, see [New-CsNetworkSubnet](https://docs.microsoft.com/powershell/module/skype/New-CsNetworkSubnet).


### To delete a network subnet

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Network Configuration**, and then click **Subnet**.

4.  On the **Subnet** page, click the subnet that you want to delete.
 
    > [!NOTE]  
    > You can delete more than one subnet at a time. To do this, press CTRL and select multiple subnets while holding down the CTRL key. Or, to select all subnets, click **Select all** on the **Edit** menu.

5.  On the **Edit** menu, click **Delete**.

6.  Click **OK**.


## See Also

[New-CsNetworkSubnet](https://docs.microsoft.com/powershell/module/skype/New-CsNetworkSubnet)  

[Set-CsNetworkSubnet](https://docs.microsoft.com/powershell/module/skype/Set-CsNetworkSubnet)  

[Remove-CsNetworkSubnet](https://docs.microsoft.com/powershell/module/skype/Remove-CsNetworkSubnet)  

[Get-CsNetworkSubnet](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkSubnet)  
