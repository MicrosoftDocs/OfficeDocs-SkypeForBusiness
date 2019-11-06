---
title: Configure network settings for cloud voice features in Microsoft Teams
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.date: 2/1/2019
ms.topic: article
ms.reviewer: roykuntz
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to create and set up network regions, sites, and subnets for cloud voice features, including Location-Based Routing for Direct Routing and enhanced emergency services.
localization_priority: Normal
ms.collection: 
  - M365-voice
appliesto: 
  - Microsoft Teams
---

# Configure network settings for cloud voice features in Microsoft Teams

> [!INCLUDE [Preview customer token](includes/preview-feature.md)]

If your organization is deploying Location-Based Routing for Direct Routing or enhanced emergency services, you must configure network settings for use with these cloud voice features in Microsoft Teams. These features have common configuration requirements to create network regions, network sites, and subnets. For example, you must associate each network site in your topology with a network region and associate each subnet with a network site. To learn more about these terms, see TBD.

You can configure network settings in the Microsoft Teams admin center or by using Windows PowerShell. This article describes how to do so by using PowerShell. For steps on how to do this in the Microsoft Teams admin center, see [Manage your network topology in Teams](manage-your-network-topology.md).

To complete the steps in this article, you'll need some familiarity with PowerShell cmdlets. To learn more, see [Teams PowerShell Overview](teams-powershell-overview.md).

## Define network regions

 A network region interconnects various parts of a network across multiple geographic areas. Use the [New-CsTenantNetworkRegion](https://docs.microsoft.com/powershell/module/skype/New-CsTenantNetworkRegion?view=skype-ps) cmdlet to define network regions. Note that the RegionID parameter is a logical name that represents the geography of the region and has no dependencies or restrictions and the CentralSite &lt;site ID&gt; parameter is optional. 

```
New-CsTenantNetworkRegion -NetworkRegionID <region ID>  
```

In this example, we create a network region named India. 
```
New-CsTenantNetworkRegion -NetworkRegionID "India"  
```

## Define network sites

Use the [New-CsTenantNetworkSite](https://docs.microsoft.com/powershell/module/skype/new-cstenantnetworksite?view=skype-ps) cmdlet to define network sites. 

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

## Define network subnets

Use the [New-CsTenantNetworkSubnet](https://docs.microsoft.com/powershell/module/skype/new-cstenantnetworksubnet?view=skype-ps) cmdlet to define network subnets and associate them to network sites. Each internal subnet can only be associated with one site. 
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

## Define external subnets
Use the [New-CsTenantTrustedIPAddress](https://docs.microsoft.com/powershell/module/skype/new-cstenanttrustedipaddress?view=skype-ps) cmdlet to define external subnets and assign them to the tenant. You can define an unlimited number of subnets for a tenant.
```
New-CsTenantTrustedIPAddress -IPAddress <External IP address> -MaskBits <Subnet bitmask> -Description <description> 
```
For example:
```
New-CsTenantTrustedIPAddress -IPAddress 198.51.100.0 -MaskBits 30 -Description "Contoso address"  
```

### Related topics

- [Plan Location-Based Routing for Direct Routing](location-based-routing-plan.md)