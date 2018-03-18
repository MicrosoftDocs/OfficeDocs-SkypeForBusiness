---
title: "New-CsNetworkInterRegionRoute"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 97deeba5-b49f-4078-9843-fee7b2d1e72e
description: "Creates a new route that connects network regions within a call admission control (CAC) configuration. This cmdlet was introduced in Lync Server 2010."
---

# New-CsNetworkInterRegionRoute
 
Creates a new route that connects network regions within a call admission control (CAC) configuration. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsNetworkInterRegionRoute -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 creates a new network region route between the NorthAmerica region and the APAC region. We give the new route the Identity NA_APAC_Route. (This will automatically be assigned as the InterNetworkRegionRouteID.) The regions being connected are NorthAmerica, which is passed as the value to the NetworkRegionID1 parameter, and APAC, which is passed as the value to the NetworkRegionID2 parameter. In this example we're assuming there is no region link configured to link NorthAmerica directly to APAC. However, there are links from NorthAmerica to EMEA (NA_EMEA), and from EMEA to APAC (EMEA_APAC). We use both those links, separated by commas, as the value of the NetworkRegionLinkIDs parameter. This will route connections from NorthAmerica to APAC through EMEA and apply any bandwidth limitations to audio and video connections associated with those links.
  
```
New-CsNetworkInterRegionRoute -Identity NA_APAC_Route -NetworkRegionID1 NorthAmerica -NetworkRegionID2 APAC -NetworkRegionLinkIDs "NA_EMEA,EMEA_APAC"
```

## Detailed Description

Every region within a CAC configuration must have some way to access every other region. While region links set bandwidth limitations on the connections between regions and also represent the physical links, a route determines which linked path the connection will traverse from one region to another. This cmdlet creates that route association.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |A unique identifier for the newly created network region route. Network region routes are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies that route.  <br/> |
| _InterNetworkRegionRouteID_ <br/> |Required  <br/> |System.String  <br/> |This value is the same as the Identity. You cannot specify both an Identity and an InterNetworkRegionRouteID; a value entered for one will be automatically used for both.  <br/> |
| _NetworkRegionID1_ <br/> |Required  <br/> |System.String  <br/> |The Identity (NetworkRegionID) of one of the two regions connected through this route. The value passed to this parameter must be a different region from the value of the NetworkRegionID2 parameter. (In other words, you can't route a region to itself.) In addition, the combination of NetworkRegionID1 and NetworkRegionID2 must be unique (for example, you can't have two routes defined that connect NorthAmerica and EMEA).  <br/> |
| _NetworkRegionID2_ <br/> |Required  <br/> |System.String  <br/> |The Identity (NetworkRegionID) of one of the two regions connected through this route. The value passed to this parameter must be a different region from the value of the NetworkRegionID1 parameter. (In other words, you can't route a region to itself.) In addition, the combination of NetworkRegionID1 and NetworkRegionID2 must be unique (for example, you can't have two routes defined that connect NorthAmerica and EMEA).  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _NetworkRegionLinkIDs_ <br/> |Optional  <br/> |System.String  <br/> |Allows you to specify all the links for this route as a string of comma-separated values. The values are the identities (NetworkRegionLinkIDs) of the region links. If you enter values for both NetworkRegionLinkIDs and NetworkRegionLinks, NetworkRegionLinkIDs will be ignored. This parameter provides a convenient way to specify the list of links without having to construct a list object and pass it to the NetworkRegionLinks parameter.  <br/> |
| _NetworkRegionLinks_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |A list object containing the identities (NetworkRegionLinkIDs) of the region links that apply to this route. For this cmdlet, this parameter differs from the NetworkRegionLinkIDs parameter only in the format if you enter more than one link. The NetworkRegionLinkIDs parameter is the recommended method for defining the initial list with this cmdlet.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

Creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType.
  
## See also

#### 

[Remove-CsNetworkInterRegionRoute](remove-csnetworkinterregionroute.md)
  
[Set-CsNetworkInterRegionRoute](set-csnetworkinterregionroute.md)
  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)

