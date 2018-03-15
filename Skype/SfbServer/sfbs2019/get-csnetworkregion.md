---
title: "Get-CsNetworkRegion"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5c9eef10-16c1-45f7-ae7b-2bee0965b421
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsNetworkRegion
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Retrieves one or more network regions. Network regions represent network hubs or backbones in an enterprise network. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsNetworkRegion [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 retrieves all network regions defined for the organization.
  
```
Get-CsNetworkRegion
```

### EXAMPLE 2

Example 2 retrieves the network regions with the Identity NorthAmerica. Because identities are unique, this command retrieves at most one network region.
  
```
Get-CsNetworkRegion -Identity NorthAmerica
```

### EXAMPLE 3

This example retrieves all network regions with identities that end with the string "America." This would retrieve regions with identities such as NorthAmerica, SouthAmerica, and CentralAmerica.
  
```
Get-CsNetworkRegion | Where-Object {$_.CentralSite -eq "site:Redmond"}
```

### EXAMPLE 4

This example retrieves all network regions associated with the central site Redmond. The command begins by calling the **Get-CsNetworkRegion** cmdlet, with no parameters, to retrieve a collection of all network regions defined for the Lync Server deployment. This collection is then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet filters this collection to return only those items (network regions) where the CentralSite value is equal to (-eq) site:Redmond. 
  
```
Get-CsNetworkRegion | Where-Object {$_.CentralSite -eq "site:Redmond"}
```

## Detailed Description
<a name="sectionSection1"> </a>

A network region interconnects various parts of a network across multiple geographic areas. Every network region must be associated with a central site. Use this cmdlet to retrieve information about one or more network regions, including the associated central site and settings that determine whether alternate paths are allowed for audio and video connections, and that associate the sites within the region with a media bypass configuration.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsNetworkRegion** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsNetworkRegion"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |This parameter allows you to perform a wildcard search on the Identity of all network regions configured for the organization. Use the wildcard character to filter on any part of the Identity.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The unique identifier of the network region you want to retrieve. The Identity will be in the form of a string that uniquely identifies that region. (Note that the Identity is the same as the NetworkRegionID.)  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the network region information from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

Returns one or more objects of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionType.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsNetworkRegion](new-csnetworkregion.md)
  
[Remove-CsNetworkRegion](remove-csnetworkregion.md)
  
[Set-CsNetworkRegion](set-csnetworkregion.md)

