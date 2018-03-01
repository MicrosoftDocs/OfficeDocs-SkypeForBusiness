---
title: "Remove-CsNetworkRegionLink"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f26cde90-e789-44a7-a304-695c85e64403
description: "Removes a link between two regions configured for call admission control (CAC). This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsNetworkRegionLink
 
Removes a link between two regions configured for call admission control (CAC). This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsNetworkRegionLink -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

This first example removes the network region link with the Identity NA_EMEA.
  
```
Remove-CsNetworkRegionLink -Identity NA_EMEA
```

### EXAMPLE 2

Example 2 removes all network region links that are using the bandwidth policy profile named HighBWLimits. The first cmdlet called in the example is the **Get-CsNetworkRegionLink** cmdlet (with no parameters), which will retrieve all region links. This collection of links is then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet looks through each member of the collection one-by-one, checking the value of the BWPolicyProfileID property. If this property is equal to (-eq) HighBWLimits, we pipe that member to the **Remove-CsNetworkRegionLink** cmdlet, which removes the link.
  
```
Get-CsNetworkRegionLink | Where-Object {$_.BWPolicyProfileID -eq "HighBWLimits"} | Remove-CsNetworkRegionLink
```

## Detailed Description

Regions within a network are linked through physical WAN connectivity. This cmdlet does not impact any physical connections, but it does remove the link from the CAC configuration.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The unique identifier of the network region link you want to remove. Network region links are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies that link.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType object. Accepts pipelined input of network region link objects.
  
## Return Types

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType.
  
## See also

#### 

[New-CsNetworkRegionLink](new-csnetworkregionlink.md)
  
[Set-CsNetworkRegionLink](set-csnetworkregionlink.md)
  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)

