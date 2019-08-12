---
title: 'Linking network regions'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "You can configure links between two network regions as part of call admission control (CAC). "
---


# Linking network regions in Skype for Business Server

You can configure links between two network regions as part of call admission control (CAC). Use the sections in this article to view newtwork region link information or configure or delete netwrok region links. 

## View network region link information 

You can view links between two network regions as part of call admission control (CAC). Regions within a network are linked through physical wide area network (WAN) connectivity. You can use the Skype for Business Server Control Panel to view an existing link between two network regions. 


### To view a network region link in Skype for Business Server Control Panel

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Network Configuration**, and then click **Region Link**.

4.  On the **Region Link** page, click the region link that you want to view.
    
    > [!NOTE]  
    > You can only view information about one region link at a time.

5.  From the **Edit** menu, select **Show details**.

### View network region link information by using Windows PowerShell cmdlets

You can view network region links by using Windows PowerShell and the **Get-CsNetworkRegionLink** cmdlet. You can run this cmdlet from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. 


### To view network region link information

  - To view information about all your network region links, type the following command in the Skype for Business Server Management Shell, and then press ENTER:
    
        Get-CsNetworkRegionLink
    
    This command returns information similar to the following:
    
        Identity            : NorthwestToCalifornia
        BWPolicyProfileID   :
        NetworkRegionLinkID : NorthwestToCalifornia
        NetworkRegionID1    : Pacific Northwest
        NetworkRegionID2    : California


For details, see [Get-CsNetworkRegionLink](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkRegionLink).


## Configure network region links 

You can configure links between two network regions as part of call admission control (CAC). Regions within a network are linked through physical wide area network (WAN) connectivity. You can use the Skype for Business Server Control Panel to define a link between two network regions and set the bandwidth limitations on audio and video connections between these regions.

### To create a network region link

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Network Configuration**, and then click **Region Link**.

4.  On the **Region Link** page, click **New**.

5.  In **New Region Link**, type a value in the **Name** field.
 
    > [!NOTE]  
    > This value must be unique within your Skype for Business Server deployment.

6.  From the **Network region \#1** drop-down list, select one of the two regions to be linked.

7.  From the **Network region \#2** drop-down list, select the other region to be linked. This region must be different from the region selected for Network region \#1.

8.  (Optional) If you want to place bandwidth limitations on audio or video calls between these regions, select a bandwidth policy profile from the **Bandwidth policy** drop-down list.

9.  Click **Commit**.

### To modify a network region link

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Network Configuration**, and then click **Region Link**.

4.  On the **Region Link** page, click the region link that you want to modify.

5.  On the **Edit** menu, click **Show details**.

6.  In **Edit Region Link**, you can modify the regions that are linked or the bandwidth policy profile for this link.

7.  Click **Commit**.


## Delete network region links

You can configure links between two network regions as part of call admission control (CAC). Regions within a network are linked through physical wide area network (WAN) connectivity. You can use the Skype for Business Server Control Panel to delete an existing link between two network regions. 

### To delete a network region link

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Network Configuration**, and then click **Region Link**.

4.  On the **Region Link** page, click the region link that you want to delete.
 
    > [!NOTE]  
    > You can delete more than one region link at a time. To do this, press CTRL and select multiple region links while holding down the CTRL key. Or, to select all region links, click <STRONG>Select all</STRONG> on the <STRONG>Edit</STRONG> menu.

5.  From the **Edit** menu, select **Delete**.

6.  Click **OK**.


## See Also

[New-CsNetworkRegionLink](https://docs.microsoft.com/powershell/module/skype/New-CsNetworkRegionLink)  

[Set-CsNetworkRegionLink](https://docs.microsoft.com/powershell/module/skype/Set-CsNetworkRegionLink)  

[Remove-CsNetworkRegionLink](https://docs.microsoft.com/powershell/module/skype/Remove-CsNetworkRegionLink)  

[Get-CsNetworkRegionLink](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkRegionLink)  
