---
title: "Set-CsNetworkInterRegionRoute"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5d9da3c0-56fc-401d-baf3-ed6c0f50f53d
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsNetworkInterRegionRoute
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Modifies an existing route that connects network regions within a call admission control (CAC) configuration. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsNetworkInterRegionRoute [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example modifies the route NA_APAC_Route by changing the region links that will be traversed along the route. The NetworkRegionLinkIDs parameter is used with a value of "NA_SA,SA_APAC", which replaces any existing links with the two specified in that string.
  
```
Set-CsNetworkInterRegionRoute -Identity NA_APAC_Route -NetworkRegionLinkIDs "NA_SA,SA_APAC"
```

### EXAMPLE 2

Like Example 1, Example 2 modifies the links within the NA_APAC_Route route. However, in this example, instead of replacing all links for that route by using the NetworkRegionLinkIDs parameter, the NetworkRegionLinks parameter is used to add a link to the list of links that already exists on that route. In this case, the link SA_EMEA is added to the route. The syntax @{add=\<link\>} adds an element to the list of links. You can also use the syntax @{replace=\<link\>} to replace all existing links with those specified by \<link\> (which essentially behaves the same as using NetworkRegionLinkIDs), or the syntax @{remove=\<link\>} to remove a link from the list.
  
```
Set-CsNetworkInterRegionRoute -Identity NA_APAC_Route -NetworkRegionLinks @{add="SA_EMEA"}
```

### EXAMPLE 3

Example 3 modifies the route named NA_Route5. This example changes one of the regions that comprise this route. The NetworkRegionID2 parameter is used to specify the new region, and then the NetworkRegionLinkIDs parameter is used to create a new list of links to connect the regions of this route.
  
```
Set-CsNetworkInterRegionRoute -Identity NA_Route5 -NetworkRegionID2 SouthAmerica -NetworkRegionLinkIDs "NA_SA,SA_APAC"
```

## Detailed Description
<a name="sectionSection1"> </a>

Every region within a CAC configuration must have some way to access every other region. While region links set bandwidth limitations on the connections between regions and also represent the physical links, a route determines which linked path the connection will traverse from one region to another. This cmdlet modifies that route association.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsNetworkInterRegionRoute** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsNetworkInterRegionRoute"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |XdsGlobalRelativeIdentity  <br/> |The unique identifier for the network region route you want to modify. Network region routes are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies that route.  <br/> |
| _Instance_ <br/> |Optional  <br/> |InterNetworkRegionRouteType  <br/> |An object reference to an existing region route. This object must be of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType, which can be retrieved by calling the **Get-CsNetworkInterRegionRoute** cmdlet.  <br/> |
| _NetworkRegionID1_ <br/> |Optional  <br/> |String  <br/> |The Identity (NetworkRegionID) of one of the two regions connected through this route. The value passed to this parameter must be a different region from the value of the NetworkRegionID2 parameter. (In other words, you can't route a region to itself.) In addition, the combination of NetworkRegionID1 and NetworkRegionID2 must be unique (for example, you can't have two routes defined that connect NorthAmerica and EMEA).  <br/> |
| _NetworkRegionID2_ <br/> |Optional  <br/> |String  <br/> |The Identity (NetworkRegionID) of one of the two regions connected through this route. The value passed to this parameter must be a different region from the value of the NetworkRegionID1 parameter. (In other words, you can't route a region to itself.) In addition, the combination of NetworkRegionID1 and NetworkRegionID2 must be unique (for example, you can't have two routes defined that connect NorthAmerica and EMEA).  <br/> |
| _NetworkRegionLinkIDs_ <br/> |Optional  <br/> |String  <br/> |Allows you to specify all the links for this route as a string of comma-separated values. The values are the identities (NetworkRegionLinkIDs) of the region links. If you enter values for both NetworkRegionLinkIDs and NetworkRegionLinks, NetworkRegionLinkIDs will be ignored. Any links modified using this parameter will replace all existing links in the route.  <br/> |
| _NetworkRegionLinks_ <br/> |Optional  <br/> |PSListModifier  <br/> |A list object containing the identities (NetworkRegionLinkIDs) of the region links that apply to this route. For this cmdlet, this parameter differs from the NetworkRegionLinkIDs in that in addition to allowing you to replace all existing links for this route, you can also add or remove individual links.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType object. Accepts pipelined input of network interregion route objects.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet does not return a value. It modifies an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsNetworkInterRegionRoute](new-csnetworkinterregionroute.md)
  
[Remove-CsNetworkInterRegionRoute](remove-csnetworkinterregionroute.md)
  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)

