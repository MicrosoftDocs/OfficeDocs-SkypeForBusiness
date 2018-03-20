---
title: "New-CsNetworkRegionLink"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 61a6a7be-8078-4d59-a78a-2f241f6bf800
description: "Creates a link between two regions configured for call admission control (CAC). This cmdlet was introduced in Lync Server 2010."
---

# New-CsNetworkRegionLink
 
Creates a link between two regions configured for call admission control (CAC). This cmdlet was introduced in Lync Server 2010.
  
```
New-CsNetworkRegionLink -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

This example creates a new network region link named NA_EMEA to link the regions NorthAmerica and EMEA. The region link name is specified as the value for the Identity parameter. (This will automatically be assigned as the value of the NetworkRegionLinkID.) The two network regions being linked are required parameters for creating the link, in this case the regions named NorthAmerica and EMEA. In this example we've also assigned a value to the BWPolicyProfile parameter. This will assign the bandwidth limitations defined in that bandwidth policy profile (LowBWLimits) to connections between these regions. If no BWPolicyProfileID is supplied, there are no bandwidth limitations on connections between these two regions. (There could still be limitations between sites. For details, see the **New-CsNetworkSite** cmdlet help topic.)
  
```
New-CsNetworkRegionLink -Identity NA_EMEA -NetworkRegionID1 NorthAmerica -NetworkRegionID2 EMEA -BWPolicyProfileID LowBWLimits
```

## Detailed Description

Regions within a network are linked through physical WAN connectivity. This cmdlet defines a link between two regions and sets the bandwidth limitations on audio and video connections between these regions.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |A unique identifier for the newly created network region link. Network region links are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies that link.  <br/> |
| _NetworkRegionID1_ <br/> |Required  <br/> |System.String  <br/> |The Identity (NetworkRegionID) of the region that is linked to the region identified by the NetworkRegionID2 parameter.  <br/> |
| _NetworkRegionID2_ <br/> |Required  <br/> |System.String  <br/> |The Identity (NetworkRegionID) of the region that is linked to the region identified by the NetworkRegionID1 parameter.  <br/> |
| _NetworkRegionLinkID_ <br/> |Required  <br/> |System.String  <br/> |This value is the same as the Identity. You cannot specify both an Identity and a NetworkRegionLinkID; a value entered for one will be automatically used for both.  <br/> |
| _BWPolicyProfileID_ <br/> |Optional  <br/> |System.String  <br/> |The Identity of the bandwidth policy profile that will define the bandwidth limitations for this link. You can retrieve a list of available profiles by calling the **Get-CsNetworkBandwidthPolicyProfile** cmdlet. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

This cmdlet creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType.
  
## See also

#### 

[Remove-CsNetworkRegionLink](remove-csnetworkregionlink.md)
  
[Set-CsNetworkRegionLink](set-csnetworkregionlink.md)
  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)
  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)
  
[New-CsNetworkSite](new-csnetworksite.md)

