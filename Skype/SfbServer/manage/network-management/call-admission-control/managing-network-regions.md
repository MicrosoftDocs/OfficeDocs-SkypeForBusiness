---
title: 'Managing network regions'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Network region* are the network hubs or backbones used in the configuration of call admission control, E9-1-1, and media bypass."
---

# Managing network regions in Skype for Business Server

*Network regions* are the network hubs or backbones used in the configuration of call admission control, E9-1-1, and media bypass. Use the following procedures to view, create, or modify network regions. For example, if you have already created network regions for one Voice feature, you do not need to create new network regions; other advanced Enterprise Voice features will use those same network regions. You may, however, need to modify an existing network region definition to apply feature-specific settings. For example, if you have created network regions for E9-1-1 (which do not require an associated central site) and you then deploy call admission control, you need to modify the network region definitions to specify a central site. 

Use the procedures in this article to view network region information or create, modify, or delete network regions. 

## View network region information 


A network region interconnects various parts of a network across multiple geographic areas. Every network region must be associated with a central site. The central site is the data center site on which the call admission control (CAC) bandwidth policy service is running. You can use Skype for Business Server Control Panel to view network regions. Network regions include settings that determine whether alternate paths through the Internet are allowed for audio and video connections. Use this topic to view existing network regions. 

### To view information about a network region with Skype for Business Server Control Panel

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Network Configuration**, and then click **Region**.

4.  On the **Region** page, click the region you want to view.
  
    > [!NOTE]  
    > You can only view one region at a time.

5.  On the **Edit** menu, click **Show details**.


### Viewing network region information by using Windows PowerShell cmdlets

You can view network region information by using Windows PowerShell and the **Get-CsNetworkRegion** cmdlet. You can run this cmdlet either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. 

### To view network region information

  - To view information about all your network regions, type the following command in the Skype for Business Server Management Shell, and then press ENTER:
    
        Get-CsNetworkRegion
    
    That will return information similar to this:
    
        Identity         : Pacific Northwest
        Description      :
        BypassID         : 3b232b84-2c1d-4da2-8181-e9330bafebe9
        CentralSite      : Site:Redmond1
        BWAlternatePaths : {BWPolicyModality=Audio;AlternatePath=True, 
                           BWPolicyModality=Video;AlternatePath=True}
        NetworkRegionID  : Pacific Northwest

For more information, see the help topic for the [Get-CsNetworkRegion](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkRegionLink) cmdlet.


## Create or modify network regions 

A network region interconnects various parts of a network across multiple geographic areas. Every network region must be associated with a central site. The central site is the data center site on which the call admission control (CAC) bandwidth policy service is running. You can use the Skype for Business Server Control Panel to configure network regions. Network regions include settings that determine whether alternate paths through the Internet are allowed for audio and video connections. From the Skype for Business Server Control Panel, you can create, modify, or delete a network region. Use this topic to create and modify network regions. 

### To create a network region

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Network Configuration**, and then click **Region**.

4.  On the **Region** page, click **New**.

5.  In the **New Region** page, type a value in the **Name** field. This value must be unique within your Skype for Business Server deployment.

6.  From the **Central site** drop-down list, select the central site for this network region.

7.  The **Enable audio alternate path** check box is checked by default. This field determines whether audio calls will be routed through an alternate path if adequate bandwidth does not exist in the primary path. Clear this check box only if you need to turn off the offload to the Internet. If any of your calls will be Internet calls, this check box must be checked, regardless of bandwidth settings.

8.  The **Enable video alternate path** check box is checked by default. This field determines whether video calls will be routed through an alternate path if adequate bandwidth does not exist in the primary path. Clear this check box only if you need to turn off the offload to the Internet. If any of your calls will be Internet calls, this check box must be checked, regardless of bandwidth settings.

9.  (Optional) Type a value in the **Description** field to provide more information about this region that cannot be expressed by the name alone.

10. Click **Commit**.

The **Associated sites** table is not used for creating a network region. You associate a site with a region when you create or modify the site. For details, see [Managing call admission control for sites](managing-call-admission-control-for-sites.md).

### To modify a network region

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Network Configuration**, and then click **Region**.

4.  On the **Region** page, click the region that you want to modify.

5.  On the **Edit** menu, click **Show details**.

6.  On the **Edit Region** page, you can modify the settings for enabling and disabling audio and video alternate paths, and change the description (for details, see the "To create a network region" section earlier in this topic.

7.  Click **Commit**.

You cannot modify the **Associated sites** on this page. The list of associated sites is provided for reference so you are aware of which sites will be affected when you modify the region settings.


## Delete existing network regions 

A network region interconnects various parts of a network across multiple geographic areas. Every network region must be associated with a central site. The central site is the data center site on which the call admission control (CAC) bandwidth policy service is running. You can use the Skype for Business Server Control Panel to configure network regions. Network regions include settings that determine whether alternate paths through the Internet are allowed for audio and video connections. From the Skype for Business Server Control Panel, you can create, modify, or delete a network region. Use this topic to delete existing network regions. 

### To delete a network region

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Network Configuration**, and then click **Region**.

4.  On the **Region** page, click the region you want to delete.
  
    > [!NOTE]  
    > You can delete more than one region at a time. To do this, press CTRL and select multiple regions while holding down the CTRL key. Or, to select all regions, click **Select all** on the **Edit** menu.

5.  On the **Edit** menu, click **Delete**.

6.  Click **OK**.


    > [!WARNING]  
    > A network region cannot be removed if it is associated with a network site. If you attempt to remove a region associated with a site, you will receive an error message. To see if a region is associated with any sites, select the region and then click **Show details** on the **Edit** menu.


## See Also

[Managing network region routes](managing-network-region-routes.md)

[New-CsNetworkRegion](https://docs.microsoft.com/powershell/module/skype/New-CsNetworkRegion)  

[Set-CsNetworkRegion](https://docs.microsoft.com/powershell/module/skype/Set-CsNetworkRegion)  

[Remove-CsNetworkRegion](https://docs.microsoft.com/powershell/module/skype/Remove-CsNetworkRegion)  

[Get-CsNetworkRegion](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkRegionLink)  
