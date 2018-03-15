---
title: "Remove-CsNetworkConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d6945015-67f7-4f04-87ae-7cb977650d96
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsNetworkConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Resets all the network configuration settings for a Lync Server deployment to the default values. This deletes an entire call admission control (CAC) deployment and related E9-1-1 configuration. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsNetworkConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example removes all CAC, location, E9-1-1 network, and media bypass settings. The Confirm parameter is used so you'll be prompted to verify you really want to do this before everything is deleted.
  
```
Remove-CsNetworkConfiguration -Identity Global -Confirm
```

## Detailed Description
<a name="sectionSection1"> </a>

WARNING: Running this cmdlet will delete an entire network configuration, including CAC, E9-1-1 regions and sites, and media bypass.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsNetworkConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsNetworkConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |This will always be Global.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command. It is recommended that you always use this parameter with this cmdlet.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings object. Accepts pipelined input of a network configuration object.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet does not return an object. It removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings object.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Set-CsNetworkConfiguration](set-csnetworkconfiguration.md)
  
[Get-CsNetworkConfiguration](get-csnetworkconfiguration.md)
  
[Get-CsNetworkSite](get-csnetworksite.md)
  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)
  
[Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)
  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)
  
[Get-CsNetworkRegion](get-csnetworkregion.md)
  
[Get-CsNetworkSubnet](get-csnetworksubnet.md)
  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)

