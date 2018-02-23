---
title: "Set-CsNetworkSite"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 221a099c-72c4-4eb0-8812-6b2b7639a9ee
description: "Modifies an existing network site that has been defined for call admission control (CAC) or Enhanced 9-1-1 (E9-1-1). This cmdlet was introduced in Lync Server 2010."
---

# Set-CsNetworkSite
[]
Modifies an existing network site that has been defined for call admission control (CAC) or Enhanced 9-1-1 (E9-1-1). This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsNetworkSite [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

In this example the network site named Vancouver is modified. The name of the site being modified is specified as the value for the Identity parameter. The Vancouver site is being moved to a new region, which requires that the NetworkRegionID parameter be changed, in this case to the region named Canada. Because a NetworkRegionID has been supplied but no value has been specified for BypassID, a BypassID value will be automatically generated. Any previously-existing bypass ID will be overwritten.
  
```
Set-CsNetworkSite -Identity Vancouver -NetworkRegionID Canada
```

### EXAMPLE 2

Example 2 simply modifies the bandwidth policy profile associated with the Vancouver site. The site name is specified as the value for the Identity parameter. Then we specify a value for the BWPolicyProfileID parameter: LowBWLimits. The policies associated with that profile will be used for this site.
  
```
Set-CsNetworkSite -Identity Vancouver - BWPolicyProfileID LowBWLimits
```

## Detailed Description

Network sites are the offices or locations configured within each region of a CAC or E9-1-1 deployment. This cmdlet modifies the settings on an existing site. This can include such things as the region with which the site is associated, the description of the site, and the associated bandwidth policy profile.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _BWPolicyProfileID_ <br/> |Optional  <br/> |String  <br/> |The Identity of the bandwidth policy profile that will define the limitations for this site. You can retrieve a list of available profiles by calling the **Get-CsNetworkBandwidthPolicyProfile** cmdlet. <br/> If you specify a value for this parameter, you must also specify a value for the NetworkRegionID parameter.  <br/> |
| _BypassID_ <br/> |Optional  <br/> |String  <br/> |A globally unique identifier (GUID). This GUID is used to map network sites to media bypass settings within a CAC or E9-1-1 network configuration. (Use this BypassID value in the call to the **New-CsNetworkMediaBypassConfiguration** cmdlet.) <br/> If you specify a value for this parameter you must also specify a value for the NetworkRegionID parameter. If you do not specify a value for this parameter but you do specify a NetworkRegionID, a BypassID will be automatically generated.  <br/> If you explicitly specify a value, it must be in the format of a GUID (for example, 3b24a047-dce6-48b2-9f20-9fbff17ed62a). We recommend that you supply a value for NetworkRegionID and allow the BypassID value to be auto-generated. If you manually enter a value, you will receive a confirmation prompt to verify that you don't want the value to be auto-generated.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |String  <br/> |A string that describes the site. This parameter can be used to provide a more descriptive explanation of what the site is for or where it is than can be expressed by the Identity alone.  <br/> |
| _EnableLocationBasedRouting_ <br/> |Optional  <br/> |Boolean  <br/> |When set to True, voice routing will be managed by taking into account the location of both the user placing the call and the user receiving the call. The default value is False.  <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |XdsGlobalRelativeIdentity  <br/> |The unique identifier of the network site you want to modify. Sites are created only at the global scope, so you do not need to specify a scope. Instead, you need to specify only the network site ID.  <br/> |
| _Instance_ <br/> |Optional  <br/> |DisplayNetworkSiteType  <br/> |A reference to a network site object (an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType). This object can be retrieved by calling the **Get-CsNetworkSite** cmdlet. <br/> |
| _LocationPolicy_ <br/> |Optional  <br/> |String  <br/> |The name of the location policy associated with this site. The location policy assigns specific E9-1-1 settings to the site. To retrieve a list of location policies, call the **Get-CsLocationPolicy** cmdlet. <br/> |
| _NetworkRegionID_ <br/> |Optional  <br/> |String  <br/> |The Identity of the network region that this site is associated with. This parameter must contain a value if you want to provide a BypassID (either through auto-generation or manually), or if the EnableBandwidthPolicyCheck property of the network configuration is True. You can retrieve the network configuration settings by calling the **Get-CsNetworkConfiguration** cmdlet. <br/> If a BypassID exists on this site already and you don't specify a value for the BypassID parameter, the existing BypassID will be overwritten by an auto-generated BypassID.  <br/> |
| _VoiceRoutingPolicy_ <br/> |Optional  <br/> |String  <br/> |Per-user voice routing policy to be assigned to the site. For example:  <br/>  `-VoiceRoutingPolicy "RedmondVoiceRouting"` <br/> Note that you must specify a per-user policy; global and/or site policies cannot be assigned to a site using the VoiceRoutingPolicy parameter.  <br/> This parameter was introduced in the February, 2013 release of Lync Server 2013.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType object. Accepts pipelined input of network site objects.
  
## Return Types

This cmdlet does not return a value. It modifies an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType.
  
## See also

#### 

[New-CsNetworkSite](new-csnetworksite.md)
  
[Remove-CsNetworkSite](remove-csnetworksite.md)
  
[Get-CsNetworkSite](get-csnetworksite.md)
  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)
  
[New-CsNetworkMediaBypassConfiguration](new-csnetworkmediabypassconfiguration.md)
  
[Get-CsLocationPolicy](get-cslocationpolicy.md)
  
[Get-CsNetworkConfiguration](get-csnetworkconfiguration.md)

