---
title: "Remove-CsNetworkBandwidthPolicyProfile"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7b1f3c8d-486c-4a7e-aa40-57893f249f66
description: "Removes a network bandwidth policy profile. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsNetworkBandwidthPolicyProfile
 
Removes a network bandwidth policy profile. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsNetworkBandwidthPolicyProfile -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

This example removes the bandwidth policy profile with the Identity LowBWProfile. Because identities must be unique this will remove, at most, one profile.
  
```
Remove-CsNetworkBandwidthPolicyProfile -Identity LowBWProfile
```

### EXAMPLE 2

Example 2 removes all references to the bandwidth policy profile with the Identity LowBWProfile from all sites to which it has been assigned, and then removes that profile. The first line of this example begins with a call to the **Get-CsNetworkSite** cmdlet to retrieve all sites configured for call admission control (CAC). This collection of sites is then piped to the **Where-Object** cmdlet, which looks for only those sites with a BWPolicyProfileID that is equal to (-eq) LowBWProfile. This narrowed-down collection, containing only sites with a BWPolicyProfileID value of LowBWProfile, is piped to the **Set-CSNetworkSite** cmdlet, which modifies each of these sites to change the BWPolicyProfileID to Null ($null). What we've just done is to find all sites with a BWPolicyProfileID of LowBWProfile and set that value to Null. At this point there are no sites using the LowBWProfile profile. We now call the **Remove-CsNetworkBandwidthPolicyProfile** cmdlet on the profile LowBWProfile to remove the profile, knowing that the profile is not in use by any sites.
  
To ensure that the profile is not in use anywhere in the network configuration, perform the same steps in Line 1 against inter-site policies and network region links.
  
```
Get-CsNetworkSite | Where-Object {$_.BWPolicyProfileID -eq "LowBWProfile"} | Set-CsNetworkSite -BWPolicyProfileID $null
Remove-CsNetworkBandwidthPolicyProfile -Identity LowBWProfile
```

## Detailed Description

As part of call admission control (CAC), a bandwidth policy is used to define bandwidth limitations for certain modalities. (In Skype for Business Server 2015, only audio and video modalities can be assigned bandwidth limitations.) This cmdlet removes a container profile for these policies.
  
IMPORTANT: If a profile has been assigned to a site (by using the **New-CsNetworkSite** cmdlet or the **Set-CsNetworkSite** cmdlet), to an inter-site policy (by using the **New-CsNetworkInterSitePolicy** cmdlet or the **Set-CsNetworkInterSitePolicy** cmdlet), or to a network region link (by using the **New-CsNetworkRegionLink** cmdlet or the **Set-CsNetworkRegionLink** cmdlet) it cannot be removed. You will receive an error if you try to remove the profile by calling the **Remove-CsNetworkBandwidthPolicyProfile** cmdlet. You must first remove the profile from all sites, inter-site policies, and network region links, and then you can remove the profile.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |A string value that uniquely identifies the bandwidth policy profile you want to remove. Specifying an Identity will remove, at most, one profile.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType object. Accepts pipelined input of network bandwidth policy profile objects.
  
## Return Types

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType.
  
## See also

#### 

[New-CsNetworkBandwidthPolicyProfile](new-csnetworkbandwidthpolicyprofile.md)
  
[Set-CsNetworkBandwidthPolicyProfile](set-csnetworkbandwidthpolicyprofile.md)
  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)

