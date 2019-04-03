---
title: 'Managing call admission control for sites'
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Network sites are the offices or locations within each network region of call admission control (CAC), E9-1-1, and media bypass deployments."
---

# Managing call admission control for sites in Skype for Business Server

Network sites are the offices or locations within each network region of call admission control (CAC), E9-1-1, and media bypass deployments. Use the procedures in this article to configure call admission control for network sites.

## Configure network site links

Within a call admission control (CAC) configuration, you can create network inter-site policies that define bandwidth limitations between sites that are directly linked. When network sites share a direct link, bandwidth limitations for audio and video connections can be defined between those two sites. You cannot use the Skype for Business Server Control Panel to configure network site policies, this can be done only by using cmdlets from the Skype for Business Server Management Shell. You can create, modify, and remove a network site link (also known as a network inter-site policy) from the Skype for Business Server Management Shell.

### To create a network site link

1.  Log on to the computer where Skype for Business Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights.

2.  Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business Server**, and then click **Skype for Business Server Management Shell**.

3.  From the command prompt, type the following command, substituting values that are valid for your configuration:
    
        New-CsNetworkInterSitePolicy -Identity Reno_Portland -NetworkSiteID1 Reno -NetworkSiteID2 Portland -BWPolicyProfileID LowBWLimits
    
    This example creates a new network site link named Reno\_Portland that sets bandwidth limitations between the Reno and Portland network sites. The network sites and the bandwidth policy profile must already exist before running this command.

For detailed parameter descriptions, see [New-CsNetworkInterSitePolicy](https://docs.microsoft.com/powershell/module/skype/New-CsNetworkInterSitePolicy). To retrieve a list of bandwidth policy profiles that can be applied to the network site link, call the **Get-CsNetworkBandwidthPolicyProfile** cmdlet. For details, see [Get-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkBandwidthPolicyProfile).

### To modify a network site link

1.  Log on to the computer where Skype for Business Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights.

2.  Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business Server**, and then click **Skype for Business Server Management Shell**.

3.  Use the **Set-CsNetworkInterSitePolicy** cmdlet to modify the properties of a given network site link. You can modify either (or both) or the connected sites, and you can modify the bandwidth policy profile associated with the link. Here is an example of modifying the bandwidth policy profile of a site link named Reno\_Portland:
    
        Set-CsNetworkInterSitePolicy -Identity Reno_Portland -BWPolicyProfileID HighBWLimits

For detailed parameter descriptions, see [Set-CsNetworkInterSitePolicy](https://docs.microsoft.com/powershell/module/skype/Set-CsNetworkInterSitePolicy).


### To delete a network site link

1.  Log on to the computer where Skype for Business Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights.

2.  Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business Server**, and then click **Skype for Business Server Management Shell**.

3.  Use the **Remove-CsNetworkInterSitePolicy** cmdlet to remove a network site link. The following example deletes the Reno\_Portland network site link:
    
        Remove-CsNetworkInterSitePolicy -Identity Reno_Portland

For detailed parameter descriptions, see [Remove-CsNetworkInterSitePolicy](https://docs.microsoft.com/powershell/module/skype/Remove-CsNetworkInterSitePolicy).


## View network site information

Network sites are the offices or locations configured within each region of a call admission control (CAC) or Enhanced 9-1-1 deployment. You can view network site information in either the Skype for Business Server Control Panel or the Skype for Business Server Management Shell. 

### To view network site information in Skype for Business Server Control Panel

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Network Configuration**, and then click **Site**.

4.  On the **Site** page, click the site that you want to view.
 
    > [!NOTE]  
    > You can only view information for one site at a time.

5.  On the **Edit** menu, click **Show details**.


### Viewing network site information by using Windows PowerShell cmdlets

You can view network site information by using Windows PowerShell and the Get-CsNetworkSite cmdlet. This cmdlet can be run either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. 

### To view network site information

  - To view information about all your network sites, type the following command in the Skype for Business Server Management Shell, and then press ENTER:
    
        Get-CsNetworkSite
    
    That will return information similar to this:
    
        Identity          : Redmond
        NetworkSiteID     : Redmond
        Description       :
        NetworkRegionID   : Pacific Northwest
        BypassID          : 3b232b84-2c1d-4da2-8181-e9330bafebe9
        BWPolicyProfileID :
        LocationPolicy    :

For more information, see the help topic for the [Get-CsNetworkSite](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkSite) cmdlet.


## Create or modify network sites 

Network sites are the offices or locations configured within each region of a call admission control (CAC) or Enhanced 9-1-1 deployment. You can use the Skype for Business Server Control Panel to configure sites and associate them with regions. For example, a network region for North America might be associated with networks sites such as Chicago, Redmond, and Vancouver. A CAC network site must be created for every site within an organization, even if that site has no bandwidth limitations. From the Skype for Business Server Control Panel you can create, modify, and delete network sites. Use the following procedures to create or modify a network site. 

### To create a network site

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Network Configuration**, and then click **Site**.

4.  On the **Site** page, click **New**.

5.  In **New Site**, type a name for this site in the **Name** field.

    > [!NOTE]  
    > Site names must be unique within the Skype for Business Server deployment.

6.  In the **Region** drop-down list, select a network region to associate with this site.

7.  (Optional) If you want to place bandwidth limitations on audio or video calls to this site, select the bandwidth policy profile with the appropriate settings from the **Bandwidth policy** drop-down list.
 
    > [!NOTE]  
    > You can view the details of the available bandwidth policy profiles, or create a new bandwidth policy profile, on the **Policy Profil** page of the **Network Configuration** group. For details, see [Managing network bandwidth policy profiles](managing-network-bandwidth-policy-profiles.md).

8.  (Optional) If you want to provide location settings for this site, select a location policy from the **Location policy** drop-down list.

    > [!NOTE]  
    > The location policy assigns specific Enhanced 9-1-1 (E9-1-1) and client location settings to the site. You can view the details of the available location policies, or create a new location policy, from the **Location Policy** page of the **Network Configuration** group. 

9.  (Optional) Type a value in the **Description** field to provide more information about this site that cannot be expressed by the name alone.

10. Click **Commit**.

    > [!NOTE]  
    > You do not use the **Associated Subnets** table when you create a new network site. You associate a subnet with a site when you create or modify the subnet. For details, see [Managing network subnets](managing-network-subnets.md).

### To modify a network site

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Network Configuration**, and then click **Site**.

4.  On the **Site** page, click the site that you want to modify.

5.  On the **Edit** menu, click **Show details**.

6.  On the **Edit Site** page, you can modify the description, region, bandwidth policy profile, and location policy associated with the site. For details, see [To create a network site](#to-create-a-network-site) above.

7.  Click **Commit**.

You cannot modify the **Associated Subnets** table on this page. The list of associated subnets is provided for reference so that you are aware of what subnets will be affected when you modify the site settings.


## Delete an existing network site

Network sites are the offices or locations configured within each region of a call admission control (CAC) or Enhanced 9-1-1 deployment. You can use the Skype for Business Server Control Panel to configure sites and associate them with regions. For example, a network region for North America might be associated with networks sites such as Chicago, Redmond, and Vancouver. A CAC network site must be created for every site within an organization, even if that site has no bandwidth limitations. From the Skype for Business Server Control Panel you can create, modify, and delete network sites. Use the following procedure to delete an existing network site. For details about creating or modifying network sites, see [Managing call admission control for sites](managing-call-admission-control-for-sites.md).


### To delete a network site

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  In the left navigation bar, click **Network Configuration**, and then click **Site**.

4.  On the **Site** page, click the site that you want to delete.

    > [!NOTE]  
    > You can delete more than one site at a time. To do this, press CTRL and select multiple sites while holding down the CTRL key. Or, to select all sites, click **Select all** on the **Edit** menu.

5.  On the **Edit** menu, click **Delete**.

6.  Click **OK**.
    

    > [!WARNING]  
    > You cannot remove a network site if it is associated with a network subnet. If you attempt to remove a site associated with a subnet you will receive an error message. To see if a site is associated with any subnets, click the site and then click **Show details** on the **Edit** menu.


## See Also


[New-CsNetworkInterSitePolicy](https://docs.microsoft.com/powershell/module/skype/New-CsNetworkInterSitePolicy) 
 
[Set-CsNetworkInterSitePolicy](https://docs.microsoft.com/powershell/module/skype/Set-CsNetworkInterSitePolicy)  

[Remove-CsNetworkInterSitePolicy](https://docs.microsoft.com/powershell/module/skype/Remove-CsNetworkInterSitePolicy)  

[Get-CsNetworkInterSitePolicy](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkInterSitePolicy)  

[Get-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkBandwidthPolicyProfile)  

[New-CsNetworkSite](https://docs.microsoft.com/powershell/module/skype/New-CsNetworkSite)

[Set-CsNetworkSite](https://docs.microsoft.com/powershell/module/skype/Set-CsNetworkSite)

[Remove-CsNetworkSite](https://docs.microsoft.com/powershell/module/skype/Remove-CsNetworkSite)  

[Get-CsNetworkSite](https://docs.microsoft.com/powershell/module/skype/Get-CsNetworkSite)  
