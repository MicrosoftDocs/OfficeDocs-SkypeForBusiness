---
title: Manage your network topology for cloud voice features in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: jastark, roykuntz
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-voice
f1keywords: ms.teamsadmincenter.networktopology.overview
appliesto: 
- Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn how to configure network settings for cloud voice features in Microsoft Teams. 
---

# Manage your network topology for cloud voice features in Microsoft Teams
Learn about network regions, network sites, network subnets, and trusted IP addresses. These terms and concepts are used throughout our cloud voice documentation for [Location-Based Routing for Direct Routing](location-based-routing-plan.md) and [dynamic emergency calling](configure-dynamic-emergency-calling.md). If you're deploying these cloud features in your organization, you must configure network settings for use with these features in Microsoft Teams.

# Network settings for cloud voice features in Microsoft Teams

> [!NOTE]
> Any feature-specific requirements for network settings are documented in the configuration topics for that feature.

## Overview

If your organization is deploying [Location-Based Routing for Direct Routing](location-based-routing-plan.md) or [dynamic emergency calling](configure-dynamic-emergency-calling.md), you must configure network settings for use with these cloud voice features in Microsoft Teams. Network settings are used to determine the location of a Teams client and include network regions, network sites, subnets, and trusted IP addresses. Depending on the cloud voice feature and capability that you're deploying, you configure some or all these settings. To learn more about these terms, see [Network settings for cloud voice features](cloud-voice-network-settings.md).

You configure network settings on the **Network topology** page of the Microsoft Teams admin center or by using Windows PowerShell.

## Configure network settings in the Microsoft Teams admin center

[!INCLUDE [preview-feature](includes/preview-feature.md)]

You define network regions, network sites, and subnets on the **Network sites** tab of the **Network topology** page. Here, you can create or modify a network site, associate a site with a network region, associate a subnet to the site, turn on Location-based Routing, and assign emergency policies to the site. You can also add network regions that can be used globally for all sites.

### Manage network sites

A *network site* represents a location where your organization has a physical venue, such as an office, a set of buildings, or a campus. Network sites are defined as a collection of IP subnets. Each network site must be associated with a network region.

You can also use network sites to enable and configure emergency calling.

#### Add a network site
1. In the left navigation of the Microsoft Teams admin center, go to **Locations** > **Network topology**, and then click the **Network sites** tab.
2. Click **New**, and then enter a name and description for the site.

    ![Screenshot of the Add network site page](media/manage-network-topology-add-site.png)

3. To associate the site with a network region, click *Link network region*, select an existing region or click **Add** to add a region, and then click **Link**.  
4. To enable Location-Based Routing for the site, turn on **Location based routing**.
5. To assign emergency services policies to the site, do one or both of the following:

    - If your organization uses Calling Plans or deployed Phone System Direct Routing, under **Emergency calling policy**, select the policy that you want.
    - If your organization deployed Phone System Direct Routing, under **Emergency call routing policy**, select the  policy that you want.

#### Associate a subset to a network 
Each *subnet* must be associated with a specific network site. A client's location is determined based on the network subnet and the associated network site. You can associate multiple subnets with the same network site but you can't associate multiple sites with the same subnet.

Subnet information is used to determine the network site on which an endpoint is located when a new session is initiated. When the location of each party in a session is known, the cloud voice feature can apply that information to determine how to handle call setup or routing.

For each network site, work with your network admin to determine which IP subnets are assigned to each network site. For example, the New York site in the North America region can be assigned the following IP subnets: 172.29.80.0/23, 157.57.216.0/25, 172.29.91.0/23, 172.29.81.0/24. If Bob, who usually works in Detroit, travels to the New York office for training, turns on his computer and connects to the network, his computer will get an IP address in one of the four ranges that are allocated for New York, for example, 172.29.80.103.
1. Under **Subnets**, click **Add subnets**. 
2. Specify the IP version, IP address, network range, add a description, and then click **Apply**. Each subnet must be associated with a specific site.
3. Click **Save**.

#### Modify a network site
1. In the left navigation of the Microsoft Teams admin center, go to **Locations** > **Network topology**, and then click the **Network sites** tab.
2. Select the site by clicking to the left of the site name, and then selecting **Edit**.
3. Make the changes that you want, and then click **Save.**
### Manage trusted IP addresses

*Trusted IP addresses* are the internet external IP addresses of the enterprise network. They determine whether the user’s endpoint is inside the corporate network before checking for a specific site match.

If the user’s external IP address matches an IP address that's in the trusted IP address list, the cloud voice feature checks to determine the internal subnet where the user’s endpoint is located. A match can be made against either IPv4 or IPv6 IP addresses and is dependent upon the format of the IP packet sent to the network settings. (If a public IP address has both IPv4 and IPv6, you must add both as trusted IP addresses.)

If the user’s external IP address doesn’t match an IP address that's in the trusted IP address list, the endpoint is classified as being at an unknown location.
#### Add a trusted IP address
1. In the left navigation of the Microsoft Teams admin center, go to **Locations** > **Network topology**, and then click the **Trusted IPs** tab.
2. Click **New**.
3. In the **Add trusted IP address** pane, specify the IP version, IP address, network range, add a description, and then click **Apply**.

    ![Screenshot of the Add trusted IP address pane](media/manage-network-topology-add-trusted-ip.png)
#### Edit a trusted IP address
1. In the left navigation of the Microsoft Teams admin center, go to **Locations** > **Network topology**, and then click the **Trusted IPs** tab.
2. Select the IP address by clicking to the left of it, and then click **Edit**.
3. In the **Edit trusted IP address** pane, make the changes that you want, and then click **Apply**.

## Configure network settings using PowerShell
To complete the steps in this section, you'll need some familiarity with PowerShell cmdlets. To learn more, see [Teams PowerShell Overview](teams-powershell-overview.md).
### Define network regions

A *network region* contains a collection of network sites. It interconnects various parts of a network across multiple geographic areas. For example, if your organization has many sites located in India, you may choose to designate “India” as a network region. Each network site must be associated with a network region.

The same network regions are shared by Location-Based Routing for Direct Routing and enhanced emergency services. 

> [!NOTE]
> If you already created network regions for one feature, you don't have to create new network regions for the other feature.

 Use the [New-CsTenantNetworkRegion](https://docs.microsoft.com/powershell/module/skype/New-CsTenantNetworkRegion) cmdlet to define network regions. Note that the RegionID parameter is a logical name that represents the geography of the region and has no dependencies or restrictions and the CentralSite &lt;site ID&gt; parameter is optional.

```
New-CsTenantNetworkRegion -NetworkRegionID <region ID>  
```

In this example, we create a network region named India.
```
New-CsTenantNetworkRegion -NetworkRegionID "India"  
```

See also [Set-CsTenantNetworkRegion](https://docs.microsoft.com/powershell/module/skype/set-cstenantnetworkregion).

### Define network sites
A *network site* represents a location where your organization has a physical venue, such as an office, a set of buildings, or a campus. Network sites are defined as a collection of IP subnets. Each network site must be associated with a network region.
You can also use network sites to enable and configure emergency calling.

Use the [New-CsTenantNetworkSite](https://docs.microsoft.com/powershell/module/skype/new-cstenantnetworksite?view=skype-ps) cmdlet to define network sites. Each network site must be associated with a network region.

```
New-CsTenantNetworkSite -NetworkSiteID <site ID> -NetworkRegionID <region ID>
```
In this example, we create two new network sites, Delhi and Hyderabad, in the India region.
```
New-CsTenantNetworkSite -NetworkSiteID "Delhi" -NetworkRegionID "India"
New-CsTenantNetworkSite -NetworkSiteID "Hyderabad" -NetworkRegionID "India"
```
The following table shows the network sites defined in this example.

||Site 1 |Site 2 |
|---------|---------|---------|
|Site ID    |    Site 1 (Delhi)     |  Site 2 (Hyderabad)       |
|Region ID  |     Region 1 (India)    |   Region 1 (India)      |

See also [Set-CsTenantNetworkRegion](https://docs.microsoft.com/powershell/module/skype/set-cstenantnetworksite).
### Define network subnetsEach subnet must be associated with a specific network site. A client's location is determined based on the network subnet and the associated network site. You can associate multiple subnets with the same network site, but you cannot associate multiple sites with the same subnet.

*Subnet* information is used to determine the network site on which an endpoint is located when a new session is initiated. When the location of each party in a session is known, the cloud voice feature can apply that information to determine how to handle call setup or routing.

For each network site, work with your network admin to determine which IP subnets are assigned to each network site. For example, the New York site in the North America region can be assigned the following IP subnets: 172.29.80.0/23, 157.57.216.0/25, 172.29.91.0/23, 172.29.81.0/24. If Bob, who usually works in Detroit, travels to the New York office for training, turns on his computer and connects to the network, his computer will get an IP address in one of the four ranges that are allocated for New York, for example, 172.29.80.103.

Use the [New-CsTenantNetworkSubnet](https://docs.microsoft.com/powershell/module/skype/new-cstenantnetworksubnet?view=skype-ps) cmdlet to define network subnets and associate them to network sites. Each network subnet can only be associated with one site.

```
New-CsTenantNetworkSubnet -SubnetID <Subnet IP address> -MaskBits <Subnet bitmask> -NetworkSiteID <site ID>
```

In this example, we create an association between subnet 192.168.0.0 and the Delhi network site and between subnet 2001:4898:e8:25:844e:926f:85ad:dd8e and the Hyderabad network site.
```

New-CsTenantNetworkSubnet -SubnetID "192.168.0.0" -MaskBits "24" -NetworkSiteID "Delhi"
New-CsTenantNetworkSubnet -SubnetID "2001:4898:e8:25:844e:926f:85ad:dd8e" -MaskBits "120" -NetworkSiteID "Hyderabad"

```
The following table shows the subnets defined in this example.

||Site 1 |Site 2 |
|---------|---------|---------|
|Subnet ID   |    192.168.0.0     |  2001:4898:e8:25:844e:926f:85ad:dd8e     |
|Mask  |     24    |   120      |
|Site ID  | Site (Delhi) | Site 2 (Hyderabad) |

For multiple subnets, you can import a CSV file by using a script such as the following.
```
Import-CSV C:\subnet.csv | foreach {New-CsTenantNetworkSubnet –SubnetID $_.SubnetID-MaskBits $_.Mask -NetworkSiteID $_.SiteID}  
```
In this example, the CSV file looks something like this:
```
Identity, Mask, SiteID
172.11.12.0, 24, Redmond
172.11.13.0, 24, Chicago
172.11.14.0, 25, Vancouver
172.11.15.0, 28, Paris
```

See also [Set-CsTenantNetworkSubnet](hhttps://docs.microsoft.com/powershell/module/skype/set-cstenantnetworksubnet).

### Define external subnets (external trusted IP addresses)
Use the [New-CsTenantTrustedIPAddress](https://docs.microsoft.com/powershell/module/skype/new-cstenanttrustedipaddress?view=skype-ps) cmdlet to define external subnets and assign them to the tenant. You can define an unlimited number of external subnets for a tenant.
```
New-CsTenantTrustedIPAddress -IPAddress <External IP address> -MaskBits <Subnet bitmask> -Description <description> 
```
For example:
```
New-CsTenantTrustedIPAddress -IPAddress 198.51.100.0 -MaskBits 30 -Description "Contoso address"  
```
See also [Set-CsTenantTrustedIPAddress](https://docs.microsoft.com/powershell/module/skype/set-cstenanttrustedipaddress).

## Related topics

- [Network settings for cloud voice features in Teams](cloud-voice-network-settings.md)
