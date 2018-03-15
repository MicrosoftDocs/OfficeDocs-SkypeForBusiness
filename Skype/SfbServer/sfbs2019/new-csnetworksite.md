---
title: "New-CsNetworkSite"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 55134dd4-eb2b-483b-8b3d-e9e42ac1acc2
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsNetworkSite
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Creates a new network site for use with call admission control (CAC) or Enhanced 9-1-1 (E9-1-1). This cmdlet was introduced in Lync Server 2010.
  
```
New-CsNetworkSite -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

In this example a new network site named Vancouver is created. The site name is specified as the value for the Identity parameter. A value is also specified for the NetworkRegionID parameter, which associates the site with the region (in this example NorthAmerica). A BypassID value will be automatically generated. Manually setting a value for BypassID is not recommended.
  
Notice that the command in this example did not include the BWPolicyProfileID parameter. Unless (or until) a value is added to this site later using the **Set-CsNetworkSite** cmdlet, it will have no bandwidth limitations for media connections. 
  
```
New-CsNetworkSite -Identity Vancouver -NetworkRegionID NorthAmerica
```

### EXAMPLE 2

In Example 2 we create a new network site named Paris. The site name is specified as the value for the Identity parameter. As in Example 1 we also specify a value for the NetworkRegionID, this time the region EMEA. Once again we are following the recommended path by allowing the cmdlet to generate the BypassID. Unlike Example 1, this example also specifies a value for the BWPolicyProfileID parameter: LowBWLimits. The policies associated with that profile will be used for this site.
  
```
New-CsNetworkSite -Identity Paris -NetworkRegionID EMEA -BWPolicyProfileID LowBWLimits
```

## Detailed Description
<a name="sectionSection1"> </a>

Network sites are the offices or locations configured within each region of a CAC or E9-1-1 deployment. This cmdlet creates a new site and optionally associates it with a region. For example, a network region for North America might be associated with networks sites such as Chicago, Redmond, and Vancouver. A CAC network site must be created for every site within an organization, even if that site has no bandwidth limitations.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsNetworkSite** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsNetworkSite"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |A unique identifier for the newly created network site. Sites are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is unique among all network sites within the Lync Server deployment.  <br/> |
| _NetworkRegionID_ <br/> |Required  <br/> |System.String  <br/> |The Identity of the network region that this site is associated with. This parameter must contain a value if you want to provide a BypassID (either through auto-generation or manually), or if the EnableBandwidthPolicyCheck property of the network configuration is True. You can retrieve the network configuration settings by calling the **Get-CsNetworkConfiguration** cmdlet.  <br/> |
| _NetworkSiteID_ <br/> |Required  <br/> |System.String  <br/> |This value is the same as the Identity. You cannot specify both an Identity and a NetworkSiteID; a value entered for one will be automatically used for both.  <br/> |
| _BWPolicyProfileID_ <br/> |Optional  <br/> |System.String  <br/> |The Identity of the bandwidth policy profile that will define the bandwidth limitations for this site. You can retrieve a list of available profiles by calling the **Get-CsNetworkBandwidthPolicyProfile** cmdlet.  <br/> If you specify a value for this parameter, you must also specify a value for the NetworkRegionID parameter.  <br/> |
| _BypassID_ <br/> |Optional  <br/> |System.String  <br/> |A globally unique identifier (GUID). This GUID is used to map network sites to media bypass settings within a CAC or E9-1-1 network configuration. (Use this BypassID value in the call to the **New-CsNetworkMediaBypassConfiguration** cmdlet.)  <br/> If you do not specify a value for this parameter, a value will be automatically generated, but only if you supply a value for the NetworkRegionID parameter. If you do not supply a NetworkRegionID parameter, no BypassID will be generated. You also cannot explicitly supply a value for the BypassID parameter without also supplying a value for the NetworkRegionID parameter.  <br/> If you explicitly specify a value, it must be in the format of a GUID (for example, 3b24a047-dce6-48b2-9f20-9fbff17ed62a). Auto-generation is recommended. If you manually enter a value, you will receive a confirmation prompt to verify that you don't want to auto-generate the value.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |A string that describes the site. This parameter can be used to provide a more descriptive explanation of what the site is for or where it is than can be expressed by the Identity alone.  <br/> |
| _EnableLocationBasedRouting_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, voice routing will be managed by taking into account the location of both the user placing the call and the user receiving the call. The default value is False.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _LocationPolicy_ <br/> |Optional  <br/> |System.String  <br/> |The name of the location policy associated with this site. The location policy assigns specific E9-1-1 settings to the site. You can retrieve a list of location policies by calling the **Get-CsLocationPolicy** cmdlet.  <br/> |
| _VoiceRoutingPolicy_ <br/> |Optional  <br/> |System.String  <br/> |Per-user voice routing policy to be assigned to the site. For example:  <br/> -VoiceRoutingPolicy "RedmondVoiceRouting"  <br/> Note that you must specify a per-user policy; global and/or site policies cannot be assigned tio a site using the VoiceRoutingPolicy parameter.  <br/> This parameter was introduced in the February, 2013 release of Lync Server 2013.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

Create an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Remove-CsNetworkSite](remove-csnetworksite.md)
  
[Set-CsNetworkSite](set-csnetworksite.md)
  
[Get-CsNetworkSite](get-csnetworksite.md)
  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)
  
[New-CsNetworkMediaBypassConfiguration](new-csnetworkmediabypassconfiguration.md)
  
[Get-CsLocationPolicy](get-cslocationpolicy.md)
  
[Get-CsNetworkConfiguration](get-csnetworkconfiguration.md)

