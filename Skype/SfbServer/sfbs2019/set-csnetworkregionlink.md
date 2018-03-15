---
title: "Set-CsNetworkRegionLink"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b3d5d203-2aa7-4a54-93d4-30bcda391d68
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsNetworkRegionLink
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Modifies a link between two network regions configured for call admission control (CAC). This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsNetworkRegionLink [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example changes the bandwidth policy profile of the network region link named NA_EMEA to the HighBWLimits profile. The name of the network region link we want to modify is specified as the value for the Identity parameter. Next, we've assigned the value HighBWLimits to the BWPolicyProfile parameter. This will assign the bandwidth limitations defined in that bandwidth policy profile (HighBWLimits) to connections between these regions.
  
```
Set-CsNetworkRegionLink -Identity NA_EMEA -BWPolicyProfileID HighBWLimits
```

## Detailed Description
<a name="sectionSection1"> </a>

Regions within a network are linked through physical WAN connectivity. This cmdlet modifies a link between two regions, allowing you to change the regions that are linked as well as the bandwidth limitations on audio and video connections between those regions.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsNetworkRegionLink** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsNetworkRegionLink"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _BWPolicyProfileID_ <br/> |Optional  <br/> |String  <br/> |The Identity of the bandwidth policy profile that will define the limitations for this link. You can retrieve a list of available profiles by calling the **Get-CsNetworkBandwidthPolicyProfile** cmdlet.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |XdsGlobalRelativeIdentity  <br/> |The unique identifier for the network region link you want to modify. Network region links are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies that link.  <br/> |
| _Instance_ <br/> |Optional  <br/> |NetworkRegionLinkType  <br/> |An object reference to a network region link. This object must be of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType, which can be retrieved by calling the **Get-CsNetworkRegionLink** cmdlet.  <br/> |
| _NetworkRegionID1_ <br/> |Optional  <br/> |String  <br/> |The Identity (NetworkRegionID) of the region that is linked to the region identified by the NetworkRegionID2 property.  <br/> |
| _NetworkRegionID2_ <br/> |Optional  <br/> |String  <br/> |The Identity (NetworkRegionID) of the region that is linked to the region identified by the NetworkRegionID1 property.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType object. Accepts pipelined input of network region link objects.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet does not return a value. It modifies an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsNetworkRegionLink](new-csnetworkregionlink.md)
  
[Remove-CsNetworkRegionLink](remove-csnetworkregionlink.md)
  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)
  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)

