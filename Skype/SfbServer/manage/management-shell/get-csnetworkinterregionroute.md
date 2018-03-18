---
title: "Get-CsNetworkInterRegionRoute"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 31c38d92-1cef-40fe-bd04-26e5b373703e
description: "Retrieves one or more routes that connect network regions within a call admission control (CAC) configuration. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsNetworkInterRegionRoute
 
Retrieves one or more routes that connect network regions within a call admission control (CAC) configuration. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsNetworkInterRegionRoute [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 retrieves the route with the Identity NA_APAC_Route.
  
```
Get-CsNetworkInterRegionRoute -Identity NA_APAC_Route
```

### EXAMPLE 2

In Example 2, we use the Filter parameter to retrieve all routes that contain the string APAC anywhere within the Identity.
  
```
Get-CsNetworkInterRegionRoute -Filter *APAC*
```

### EXAMPLE 3

This example retrieves all region routes that use the network region link NA_EMEA. The command begins by calling the **Get-CsNetworkInterRegionRoute** cmdlet. Calling this cmdlet with no parameters retrieves all routes defined with the CAC configuration. This collection of routes is then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet takes the collection and retrieves all items in the collection that have the value NA_EMEA within their NetworkRegionLinks list.
  
```
Get-CsNetworkInterRegionRoute | Where-Object {$_.NetworkRegionLinks -eq "NA_EMEA"}
```

### EXAMPLE 4

Example 4 retrieves all region routes that include the NorthAmerica region. The first part of the command is a call to the **Get-CsNetworkInterRegionRoute** cmdlet. This cmdlet, called with no parameters, will retrieve all region routes. Next, this collection of routes is piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet will narrow the collection down to only those routes that have NorthAmerica defined as one of the regions in the route. It does this by checking to see if the route has a NetworkRegionID1 value equal to (-eq) NorthAmerica, or (-or) a NetworkRegionID2 value equal to NorthAmerica.
  
```
Get-CsNetworkInterRegionRoute | Where-Object {$_.NetworkRegionID1 -eq "NorthAmerica" -or $_.NetworkRegionID2 -eq "NorthAmerica"}
```

## Detailed Description

Every region within a CAC configuration must have some way to access every other region. While region links set bandwidth limitations on the connections between regions and also represent the physical links, a route determines which linked path the connection will traverse from one region to another. This cmdlet retrieves information about these route associations.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |A string that allows you to retrieve routes based on matching the Identity values to the wildcard string passed as a value to this parameter.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The unique identifier for the network region route you want to retrieve. Network region routes are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies a particular route.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the network interregion route information from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

This cmdlet returns one of more objects of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType.
  
## See also

#### 

[New-CsNetworkInterRegionRoute](new-csnetworkinterregionroute.md)
  
[Remove-CsNetworkInterRegionRoute](remove-csnetworkinterregionroute.md)
  
[Set-CsNetworkInterRegionRoute](set-csnetworkinterregionroute.md)

