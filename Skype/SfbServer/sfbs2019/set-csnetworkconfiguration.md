---
title: "Set-CsNetworkConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d54dc154-c092-4be9-8656-f7fec3fbd835
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Set-CsNetworkConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Modifies the settings for a network configuration. This cmdlet will most often be used to enable or disable call admission control (CAC). This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsNetworkConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command in this example will run a validation check against the entire CAC configuration, and then (depending on your responses to any warning prompts that are returned) will enable CAC. If CAC is already enabled (in other words, if the EnableBandwidthPolicyCheck property is True) and you run this command, it will simply run the validation check.
  
```
Set-CsNetworkConfiguration -EnableBandwidthPolicyCheck $True
```

## Detailed Description
<a name="sectionSection1"> </a>

The network configuration object contains all the settings for an entire CAC configuration within a Lync Server deployment, plus media bypass settings. You can use this cmdlet to modify any part of the CAC configuration, and you must use it if you need to change media bypass settings. However, it's recommended that you use cmdlets specific to the object type when modifying most of the CAC configuration settings. For example, to work with network regions, use the cmdlets ending with the noun CsNetworkRegion rather than manipulating the NetworkRegions parameter of this cmdlet.
  
The primary use of this cmdlet is to enable (and disable) CAC and apply media bypass settings. After you've set up the various components required for your configuration (such as regions, sites, and subnets), you must enable the configuration before it will work. To do this, simply set the EnableBandwidthPolicyCheck parameter to True. Note that running this cmdlet with EnableBandwidthPolicyCheck set to True doesn't immediately enable CAC. Before it can be enabled, a series of validation checks are made to ensure the setup is configured properly. Any errors or discrepancies in the setup will prompt with warnings that ask if you want to continue to enable CAC even though there is a problem. If you choose to continue (by pressing Enter or Y), the validation will continue and will prompt you again if another issue is discovered.
  
If you run through the entire validation, choosing to continue at each warning, EnableBandwidthPolicyCheck will be set to True and CAC will be enabled, but until the issues are resolved it probably won't work as expected. If at any point in the validation you choose to stop validation (by typing N at a warning prompt), validation will end and EnableBandwidthPolicyCheck will remain set to False (the default).
  
If EnableBandwidthPolicyCheck is already set to True, you can call the **Set-CsNetworkConfiguration** cmdlet and pass a value of True to the parameter EnableBandwidthPolicyCheck to run the validation without modifying any settings. In addition, when EnableBandwidthPolicyCheck is True, any changes you attempt to make by calling the **Set-CsNetworkConfiguration** cmdlet will again cause the validation check to run. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsNetworkConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsNetworkConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _BWPolicyProfiles_ <br/> |Optional  <br/> |PSListModifier  <br/> |A collection of all the bandwidth policy profiles that can be assigned to sites, inter-site policies, and network region links. Each bandwidth policy profile contains bandwidth limitations (overall limitations and session limitations) for audio and/or video connections. A full list of bandwidth policy profiles can be retrieved by calling the **Get-CsNetworkBandwidthPolicyProfile** cmdlet.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableBandwidthPolicyCheck_ <br/> |Optional  <br/> |Boolean  <br/> |Setting this parameter to True will run a validation check against the entire CAC configuration. If all validation checks pass, or if you choose to ignore all warnings, CAC will be enabled. If a validation check does not pass, you can choose to stop the validation and the value of EnableBandwidthPolicyCheck will not change. You must have region routes defined between each pair of network regions before you running the validation check.  <br/> Setting this value to False will disable CAC.  <br/> Default: False  <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |This parameter does not take a value. If you include this parameter, any changes made to the configuration, including enabling the configuration, will take place with no warnings or validation checks.  <br/> |
| _Identity_ <br/> |Optional  <br/> |XdsIdentity  <br/> |This value will always be Global.  <br/> |
| _Instance_ <br/> |Optional  <br/> |NetworkConfigurationSettings  <br/> |A reference to a network configuration object. This object must be of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings, which can be retrieved by calling the **Get-CsNetworkConfiguration** cmdlet.  <br/> |
| _InterNetworkRegionRoutes_ <br/> |Optional  <br/> |PSListModifier  <br/> |A collection of all the network region routes defined within the CAC configuration. You can retrieve all the members of this collection by calling the **Get-CsNetworkInterRegionRoute** cmdlet.  <br/> |
| _InterNetworkSitePolicies_ <br/> |Optional  <br/> |PSListModifier  <br/> |A collection of network inter-site policies defined within the CAC configuration. You can retrieve all the members of this collection by calling the **Get-CsNetworkInterSitePolicy** cmdlet.  <br/> |
| _MediaBypassSettings_ <br/> |Optional  <br/> |MediaBypassSettingsType  <br/> |A reference to an object that defines the global media bypass settings for the CAC configuration. Setting this value will overwrite all existing media bypass settings. You obtain this object reference by calling the **New-CsNetworkMediaBypassConfiguration** cmdlet and assigning the new configuration settings to a variable. Pass this variable to the MediaBypassSettings parameter to change the global media bypass settings.  <br/> |
| _NetworkRegionLinks_ <br/> |Optional  <br/> |PSListModifier  <br/> |A collection of network region links defined within the CAC configuration. Each network region link defines a connection that exists between two regions and any bandwidth limitations that should be applied to connections between those regions. You can retrieve all the members of this collection by calling the **Get-CsNetworkRegionLink** cmdlet.  <br/> |
| _NetworkRegions_ <br/> |Optional  <br/> |PSListModifier  <br/> |A collection of network regions (each of which represents a hub or backbone within the network) defined within the CAC configuration. You can retrieve all the members of this collection by calling the **Get-CsNetworkRegion** cmdlet.  <br/> |
| _NetworkSites_ <br/> |Optional  <br/> |PSListModifier  <br/> |A collection of network sites (each of which represents an office or location within a region) defined within the CAC configuration. You can retrieve all the members of this collection by calling the **Get-CsNetworkSite** cmdlet.  <br/> |
| _Subnets_ <br/> |Optional  <br/> |PSListModifier  <br/> |A collection of network subnets (each of which associates an endpoint with a site) defined within the CAC configuration. You can retrieve all the members of this collection by calling the **Get-CsNetworkSubnet** cmdlet.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings object. Accepts pipelined input of a network configuration object.
  
## Return Types
<a name="sectionSection3"> </a>

The **Set-CsNetworkConfiguration** cmdlet does not return a value or object. Instead, the cmdlet modifies instances of the Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Remove-CsNetworkConfiguration](remove-csnetworkconfiguration.md)
  
[Get-CsNetworkConfiguration](get-csnetworkconfiguration.md)
  
[Get-CsNetworkSite](get-csnetworksite.md)
  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)
  
[Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)
  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)
  
[Get-CsNetworkRegion](get-csnetworkregion.md)
  
[Get-CsNetworkSubnet](get-csnetworksubnet.md)
  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)
  
[New-CsNetworkMediaBypassConfiguration](new-csnetworkmediabypassconfiguration.md)

