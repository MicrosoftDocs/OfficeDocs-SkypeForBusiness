---
title: "Remove-CsNetworkInterRegionRoute"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 91948c03-2bcb-4e25-b0b6-23827e85bbb3
description: "Removes a route that connects network regions within a call admission control (CAC) configuration. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsNetworkInterRegionRoute
 
Removes a route that connects network regions within a call admission control (CAC) configuration. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsNetworkInterRegionRoute -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

Example 1 removes the route with the Identity NA_APAC_Route.
  
```
Remove-CsNetworkInterRegionRoute -Identity NA_APAC_Route
```

### EXAMPLE 2

Example 2 removes all region routes that include the NorthAmerica region. The first part of the command is a call to the **Get-CsNetworkInterRegionRoute** cmdlet. This cmdlet, called with no parameters, will retrieve all region routes. Next, this collection of routes is piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet will narrow the collection down to only those routes that have NorthAmerica defined as one of the regions in the route. It does this by checking to see if the route has a NetworkRegionID1 value equal to (-eq) NorthAmerica, or (-or) a NetworkRegionID2 value equal to NorthAmerica. Once the collection contains only the routes that include the NorthAmerica region, we pipe the collection to the **Remove-CsNetworkInterRegionRoute** cmdlet, which removes each of those routes.
  
```
Get-CsNetworkInterRegionRoute | Where-Object {$_.NetworkRegionID1 -eq "NorthAmerica" -or $_.NetworkRegionID2 -eq "NorthAmerica"} | Remove-CsNetworkInterRegionRoute
```

## Detailed Description

Every region within a CAC configuration must have some way to access every other region. While region links set bandwidth limitations on the connections between regions and also represent the physical links, a route determines which linked path the connection will traverse from one region to another. This cmdlet removes one of these route associations.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The unique identifier for the network region route you want to remove. Network region routes are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies that route.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType object. Accepts pipelined input of network inter-region route objects.
  
## Return Types

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType.
  
## See also

#### 

[New-CsNetworkInterRegionRoute](new-csnetworkinterregionroute.md)
  
[Set-CsNetworkInterRegionRoute](set-csnetworkinterregionroute.md)
  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)

