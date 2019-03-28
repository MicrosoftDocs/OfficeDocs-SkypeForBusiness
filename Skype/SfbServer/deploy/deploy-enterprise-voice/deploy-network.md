---
title: "Deploy network regions, sites and subnets in Skype for Business"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: bf7a3dc4-71a2-4559-a547-d90305d4f904
description: "Create or modify network regions, network sites, and associate network subnets in Skype for Business Server. All these are used for the advanced Enterprise Voice features: media bypass, call admission control, and location-based routing."
---

# Deploy network regions, sites and subnets in Skype for Business

Create or modify network regions, network sites, and associate network subnets in Skype for Business Server. All these are used for the advanced Enterprise Voice features: media bypass, call admission control, and location-based routing.

The advanced Enterprise Voice features are [call admission control](../../plan-your-deployment/enterprise-voice-solution/call-admission-control.md), [media bypass](../../plan-your-deployment/enterprise-voice-solution/media-bypass.md), [ location-based routing](../../plan-your-deployment/enterprise-voice-solution/location-based-routing.md), and [E9-1-1](../../plan-your-deployment/enterprise-voice-solution/emergency-services.md). These features all require you to create network regions, network sites, and subnets. For example, all of these features require that each subnet in your topology be associated with a specific network site, and each network site must be associated with a network region. For more information on these terms, see [Network settings for the advanced Enterprise Voice features in Skype for Business Server](../../plan-your-deployment/enterprise-voice-solution/network-settings-for-advanced-features.md)

Call admission control and E9-1-1 have additional configuration requirements for network sites:

- Call admission control requires that a bandwidth policy profile be specified for each site that is constrained by WAN bandwidth limitations. If you plan to deploy call admission control, you must [Create bandwidth policy profiles in Skype for Business Server](create-bandwidth-policy-profiles.md) before you configure your network sites.

- E9-1-1 requires that a location policy be specified for each site. If you plan to deploy E9-1-1, you must [Create location policies in Skype for Business Server](create-location-policies.md) before you configure your network sites.

## Create or modify a Network Region

If you have already created network regions for one of these features, you do not need to create new network regions; other advanced Enterprise Voice features will use those same network regions.

You may, however, need to modify an existing network region definition to apply feature-specific settings. For example, if you have created network regions for E9-1-1 (which do not require an associated central site) and you then deploy call admission control, you need to modify the network region definitions to specify a central site.

### To create a network region using Skype for Business Server Management Shell

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.

2. Run the New-CsNetworkRegion cmdlet to create network regions:

   ```
   New-CsNetworkRegion -Identity <String> -CentralSite <String>
   ```

    For example:

   ```
   New-CsNetworkRegion -Identity NorthAmerica -CentralSite CHICAGO -Description "All North America Locations"
   ```

    In this example, you created a network region called "NorthAmerica" that is associated with a central site with site ID CHICAGO.

3. To finish creating network regions for your topology, repeat step 2 with settings for each network region.

### To create a network region using Skype for Business Server Control Panel

1. Open Skype for Business Server Control Panel.

2. In the left navigation bar, click **Network Configuration**.

3. Click **Region**.

4. Click **New**.

5. On the **New Region** page, click **Name** and then type a name for the network region.

6. Click **Central site**, and then click a central site in the list.

7. Optionally, click **Description**, and then type additional information to describe this network site.

8. Click **Commit**.

9. To finish creating network regions for your topology, repeat steps 4 through 8 with settings for other regions.

### To modify a network region using Skype for Business Server Management Shell

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.

2. Run the Set-CsNetworkRegion cmdlet to modify an existing network region:

   ```
   Set-CsNetworkRegion -Identity <String> -CentralSite <String>
   ```

    For example:

   ```
   Set-CsNetworkRegion -Identity NorthAmerica -CentralSite CHICAGO -Description "North American Region"
   ```

    In this example, you modified an existing network region called "NorthAmerica" (created using the procedures earlier in this topic) by changing the description. If a description existed for the "NorthAmerica" region, this command overwrites it with this value; if no description had been set, then this command sets it.

3. To modify other network regions, repeat step 2 with settings for other regions.

### To modify a network region using Skype for Business Server Control Panel

1. Open Skype for Business Server Control Panel.

2. In the left navigation bar, click **Network Configuration**.

3. Click the **Region** navigation button.

4. In the table, click the network region that you want to modify.

5. Click **Edit**, and then click **Show details…**.

6. On the **Edit Region** page, change the values for this network region's settings as appropriate.

7. Click **Commit**.

8. To finish modify network regions, repeat steps 4 through 7 with settings for other regions.

## Create or modify a network site

If you have already created network sites for one of these features, you do not need to create new network sites; other advanced Enterprise Voice features will use those same network sites. You may, however, need to modify an existing network site definition to apply feature-specific settings. For example, if you created a network site for E9-1-1, you need to modify the network site during deployment of call admission control to apply a bandwidth policy profile.

### To create a network site by using Skype for Business Server Management Shell

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.

2. Run the New-CsNetworkSite cmdlet to create network sites:

   ```
   New-CsNetworkSite -NetworkSiteID <string>
   ```

    For example:

   ```
   New-CsNetworkSite -NetworkSiteID Chicago -Description "Corporate headquarters"-NetworkRegionID NorthAmerica
   ```

    In this example, you created a network site called "Chicago" that is in the "NorthAmerica" network region.

    > [!NOTE]
    > The NorthAmerica network region must already exist for this command to run successfully.

3. To finish creating network sites for your topology, repeat step 2 with settings for other sites.

### To create a network site by using Skype for Business Server Control Panel

1. Open Skype for Business Server Control Panel.

2. In the left navigation bar, click **Network Configuration**.

3. Click the **Site** navigation button.

4. Click **New**.

5. On the **New Site** page, click **Name** and then type a name for the network site.

6. Click **Region**, and then click a region in the list.

7. Optionally, click **Bandwidth policy**, and then click a bandwidth policy in the list.

    > [!NOTE]
    > Bandwidth policy is required only if you deploy call admission control at the site.

8. Optionally, click **Location policy**, and then click a location policy in the list.

    > [!NOTE]
    > Location policy is required only if you deploy E9-1-1 at the site.

9. Optionally, click **Description**, and then type additional information to describe this network site.

10. Click **Commit**.

11. To finish creating network sites for your topology, repeat steps 4 through 10 with settings for other sites.

### To modify a network site by using Skype for Business Server Management Shell

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.

2. Run the Set-CsNetworkSite cmdlet to modify network sites:

   ```
   Set-CsNetworkSite -Identity <string>
   ```

    For example:

   ```
   Set-CsNetworkSite -Identity Albuquerque -NetworkRegionID NorthAmerica
   ```

    In this example, the site called "Albuquerque" is moved to the "NorthAmerica" network region. To modify the network site configuration to deploy call admission control, E9-1-1, or media bypass, modify the network site settings by running the Set-CsNetworkSite cmdlet with the BWPolicyProfileID or LocationPolicy parameter, respectively.

    > [!NOTE]
    > Although the BypassID parameter exists for media bypass, we strongly recommend that you do not override automatically generated bypass IDs. You do not need to specify additional parameters to configure a network site for media bypass.

3. To finish modifying network sites for your topology, repeat step 2 with settings for other sites.

### To modify a network site by using Skype for Business Server Control Panel

1. Open Skype for Business Server Control Panel.

2. In the left navigation bar, click **Network Configuration**.

3. Click the **Site** navigation button.

4. In the table, click the network site that you want to modify.

5. Click **Edit**, and then click **Show details…**.

6. On the **Edit Site** page, change the values for this network site's settings as appropriate.

7. Click **Commit**.

8. To finish modify network sites, repeat steps 4 through 7 with settings for other sites.

## Associate a subnet with a network site
<a name="BKMK_AssociateSubnets"> </a>

Every subnet in your network must be associated with a specific network site, because subnet information is used to determine the network site on which an endpoint is located while a new session is initiated. When the location of each party in a session is known, advanced Enterprise Voice features can apply that information to determine how to handle the call setup or routing.

All configured public IP addresses of the Audio/Video Edge Servers in your deployment must be added to your network configuration settings. These IP addresses are added as subnets with a mask of 32. The associated network site should correspond to the appropriate configured network site. For example, the public IP address that corresponds to the A/V Edge service in central site Chicago would be NetworkSiteID Chicago.

### To associate a subnet with a network site by using Skype for Business Server Management Shell

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.

2. Run the **New-CsNetworkSubnet** cmdlet to associate a subnet with a network site:

   ```
   New-CsNetworkSubnet -SubnetID <String> -MaskBits <Int32> -NetworkSiteID <String>
   ```

    For example:

   ```
   New-CsNetworkSubnet -SubnetID 172.11.12.13 - MaskBits 20 -NetworkSiteID Chicago
   ```

    In this example, you created an association between the subnet 172.11.12.13 and the network site "Chicago".

3. Repeat step 2 for all subnets in your topology.

### To associate subnets with network sites by importing a CSV file

1. Create a CSV file that includes all of the subnets you want to add. For example, create a file named **subnet.csv** with the following content:

     `IPAddress, mask, description, NetworkSiteID`

     `172.11.12.0, 24, "NA:Subnet in Portland", Portland`

     `172.11.13.0, 24, "NA:Subnet in Reno", Reno`

     `172.11.14.0, 25, "EMEA:Subnet in Warsaw", Warsaw`

     `172.11.15.0, 31, "EMEA:Subnet in Paris", Paris`

2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.

3. Run the following cmdlet to import **subnet.csv**, and then store its contents in the Lync Server management store:

   ```
   import-csv subnet.csv | foreach {New-CsNetworkSubnet -Identity $_.IPAddress -MaskBits $_.mask -Description $_.description -NetworkSiteID $_.NetworkSiteID}
   ```

### To associate a subnet with a network site by using Skype for Business Server Control Panel

1. Open Skype for Business Server Control Panel.

2. In the left navigation bar, click **Network Configuration**.

3. Click the **Subnet** navigation button.

4. Click **New**.

5. On the **New Subnet** page, click **Subnet ID**, and then type the first address in the IP address range defined by the subnet you want to associate with a network site.

6. Click **Mask**, and then type the bitmask to apply to the subnet.

7. Click **Network site ID**, and then select the site ID of the site to which you are adding this subnet.

    > [!NOTE]
    > If you have not yet created network sites, this list will be empty. For details about the procedure, see [Create or Modify a Network Site](https://technet.microsoft.com/library/14e24856-9996-4da4-9f31-300940bdf5aa.aspx). You can also retrieve site IDs for your deployment by running the **Get-CsNetworkSite** cmdlet. For details, see the Skype for Business Server Management Shell documentation.

8. Optionally, click **Description**, and then type additional information to describe this subnet.

9. Click **Commit**.

Repeat these steps to add other subnets to a network site.
> [!NOTE]
> A Key Health Indicator (KHI) alert is raised, specifying a list of IP addresses that are present in your network but are either not associated with a subnet, or the subnet that includes the IP addresses is not associated with a network site. This alert will not be raised more than once within an 8-hour period.

The relevant alert information and an example are as follows:

 **Source**: CS Bandwidth Policy Service (Core)

 **Event number**: 36034

 **Level**: 2

 **Description**: The subnets for the following IP addresses: \<List of IP Addresses\> are either not configured or the subnets are not associated to a Network Site.

 **Cause**: The subnets for the corresponding IP addresses are missing from the network configuration settings or the subnets are not associated to a network site.

 **Resolution**: Add subnets corresponding to the list of IP addresses into the network configuration settings and associate every subnet to a network site.

For example, if the IP address list in the alert specifies 10.121.248.226 and 10.121.249.20, either these IP addresses are not associated with a subnet or the subnet they are associated with does not belong to a network site. If 10.121.248.0/24 and 10.121.249.0/24 are the corresponding subnets for these addresses, you can resolve this issue as follows:

1. Be sure that IP address 10.121.248.226 is associated with the 10.121.248.0/24 subnet and IP address 10.121.249.20 is associated with the 10.121.249.0/24 subnet.

2. Be sure that the 10.121.248.0/24 and 10.121.249.0/24 subnets are each associated with a network site.

## See also
<a name="BKMK_AssociateSubnets"> </a>


[New-CsNetworkRegion](https://docs.microsoft.com/powershell/module/skype/new-csnetworkregion?view=skype-ps)

[Get-CsNetworkRegion](https://docs.microsoft.com/powershell/module/skype/get-csnetworkregion?view=skype-ps)

[Set-CsNetworkRegion](https://docs.microsoft.com/powershell/module/skype/set-csnetworkregion?view=skype-ps)

[Remove-CsNetworkRegion](https://docs.microsoft.com/powershell/module/skype/remove-csnetworkregion?view=skype-ps)

[New-CsNetworkSubnet](https://docs.microsoft.com/powershell/module/skype/new-csnetworksubnet?view=skype-ps)

[Get-CsNetworkSubnet](https://docs.microsoft.com/powershell/module/skype/get-csnetworksubnet?view=skype-ps)

[Set-CsNetworkSubnet](https://docs.microsoft.com/powershell/module/skype/set-csnetworksubnet?view=skype-ps)

[Remove-CsNetworkSubnet](https://docs.microsoft.com/powershell/module/skype/remove-csnetworksubnet?view=skype-ps)

