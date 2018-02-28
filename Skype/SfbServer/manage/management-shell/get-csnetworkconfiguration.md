---
title: "Get-CsNetworkConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 08bc8eca-b244-4d5e-b089-1cc95605ba14
description: "Retrieves global settings for call admission control (CAC), Enhanced 9-1-1 (E9-1-1), and media bypass. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsNetworkConfiguration
[]
Retrieves global settings for call admission control (CAC), Enhanced 9-1-1 (E9-1-1), and media bypass. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsNetworkConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

This example retrieves the network configuration settings. These settings are defined only at the global scope, so only one item will be returned.
  
```
Get-CsNetworkConfiguration
```

### EXAMPLE 2

Only one set of media bypass settings exists, which is applied globally. These settings are stored as part of the overall network configuration. This command first retrieves that configuration by calling the **Get-CsNetworkConfiguration** cmdlet, and then retrieves the MediaBypassSettings property of the configuration.
  
```
(Get-CsNetworkConfiguration).MediaBypassSettings
```

## Detailed Description

The network configuration object contains all the global settings for media bypass and for an entire CAC configuration within a Skype for Business Server 2015 deployment, including whether or not that configuration has been enabled. You can use this cmdlet to retrieve these configurations and settings. However, other than EnableBandwidthPolicyCheck and MediaBypassSettings, it's recommended that you use cmdlets specific to the object type for retrieving the CAC configuration settings. For example, to retrieve the network regions, it will usually be easier to call the **Get-CsNetworkRegion** cmdlet than to call the **Get-CsNetworkConfiguration** cmdlet and then retrieve the NetworkRegions property of that configuration.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Because there will only ever be one network configuration, you do not need this parameter for this cmdlet.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |This will always be Global.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the network configuration from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

The **Get-CsNetworkConfiguration** cmdlet returns an instance of the Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings object.
  
## See also

#### 

[Remove-CsNetworkConfiguration](remove-csnetworkconfiguration.md)
  
[Set-CsNetworkConfiguration](set-csnetworkconfiguration.md)
  
[Get-CsNetworkSite](get-csnetworksite.md)
  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)
  
[Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)
  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)
  
[Get-CsNetworkRegion](get-csnetworkregion.md)
  
[Get-CsNetworkSubnet](get-csnetworksubnet.md)
  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)

