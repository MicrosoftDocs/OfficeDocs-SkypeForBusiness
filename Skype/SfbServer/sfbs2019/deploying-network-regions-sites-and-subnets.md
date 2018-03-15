---
title: "Deploying network regions, sites, and subnets in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c4b75601-3538-4d07-8d23-1ad90459ae48
description: "In this articleDefine Network RegionsDefine Network SitesDefine Network Subnets"
---

# Deploying network regions, sites, and subnets in Lync Server 2013
[]
 **In this article**
  
[Define Network Regions](#sectionSection0)
  
[Define Network Sites](#sectionSection1)
  
[Define Network Subnets](#sectionSection2)
  
Once Enterprise Voice is deployed, you need to configure:
  
- Network regions
    
- Network sites
    
- Network subnets
    
## Define Network Regions
<a name="sectionSection0"> </a>

Use the Lync Server Windows PowerShell command, New-CsNetworkRegion, or Lync Server Control Panel to define network regions.
  
```
New-CsNetworkRegion -NetworkRegionID <region ID> -CentralSite <site ID>
```

For more information, see [New-CsNetworkRegion](new-csnetworkregion.md).
  
For this example, the following Windows PowerShell command illustrates the network region, region 1 (India), defined in this scenario.
  
```
New-CsNetworkRegion -NetworkRegionID "India" -CentralSite "India Central Site"
```

## Define Network Sites
<a name="sectionSection1"> </a>

Use the Lync Server Windows PowerShell command, New-CsNetworkSite, or the Lync Server Control Panel to define network sites.
  
```
New-CsNetworkSite -NetworkSiteID <site ID> -NetworkRegionID <region ID>
```

For more information, see [New-CsNetworkSite](new-csnetworksite.md).
  
For this example, the following table and Lync Server Windows PowerShell command illustrate the network sites defined in this scenario. Only settings that are specific to Location-Based Routing are included in the table for illustration purposes.
  
```
New-CsNetworkSite -NetworkSiteID "Delhi" -NetworkRegionID "India"
New-CsNetworkSite -NetworkSiteID "Hyderabad" -NetworkRegionID "India"
```

****

||**Site 1 (Delhi)**|**Site 2 (Hyderabad)**|
|:-----|:-----|:-----|
|Site ID  <br/> |Site 1 (Delhi)  <br/> |Site 2 (Hyderabad)  <br/> |
|Region ID  <br/> |Region 1 (India)  <br/> |Region 1 (India)  <br/> |
   
## Define Network Subnets
<a name="sectionSection2"> </a>

Use the Lync Server Windows PowerShell command, New-CsNetworkSubnet, or the Lync Server Control Panel to define network subnets and assign them to network sites.
  
```
New-CsNetworkSubnet -SubnetID <Subnet IP address> -MaskBits <Subnet bitmask> -NetworkSiteID <site ID>
```

For more information, see [New-CsNetworkSubnet](new-csnetworksubnet.md).
  
For this example, the following table and Windows PowerShell commands illustrate the assignment of network subnets to the network sites, Delhi and Hyderabad, defined in this scenario. Only settings that are specific to Location-Based Routing are included in the table for illustration purposes.
  
```
New-CsNetworkSubnet -SubnetID "192.168.0.0" -MaskBits "24" -NetworkSiteID "Delhi"
New-CsNetworkSubnet -SubnetID "192.168.1.0" -MaskBits "24" -NetworkSiteID "Hyderabad"
```

****

||**Site 1 (Delhi)**|**Site 2 (Hyderabad)**|
|:-----|:-----|:-----|
|Subnet ID  <br/> |192.168.0.0  <br/> |192.168.1.0  <br/> |
|Mask  <br/> |24  <br/> |24  <br/> |
|Site ID  <br/> |Site 1 (Delhi)  <br/> |Site 2 (Hyderabad)  <br/> |
   
## See also
<a name="sectionSection2"> </a>

#### 

[Configuring Location-Based Routing in Lync Server 2013](configuring-location-based-routing.md)

