---
title: "New-CsNetworkMediaBypassConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 24055ae5-7fc8-4ca5-9e65-ac3a1f17b405
description: "Creates new global settings for media bypass. This cmdlet was introduced in Lync Server 2010."
---

# New-CsNetworkMediaBypassConfiguration
 
Creates new global settings for media bypass. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsNetworkMediaBypassConfiguration [-AlwaysBypass <$true | $false>] [-BypassID <String>] [-Enabled <$true | $false>] [-EnableDefaultBypassID <$true | $false>] [-EnabledForAudioVideoConferences <$true | $false>] [-ExternalBypassMode <Off | ICE | Any>] [-InternalBypassMode <Off | ICE | Any>]

```

## Examples

### EXAMPLE 1

The commands in this example enable media bypass and configure it to always attempt bypass. The first line in the example is a call to the **New-CsNetworkMediaBypassConfiguration** cmdlet. We pass two parameters to this cmdlet: AlwaysBypass and Enabled, setting both to True ($true). Setting Enabled to True enables media bypass, while setting AlwaysBypass to True assures that media bypass will be attempted on all calls. (Note that setting these two parameters will automatically generate a value for the BypassID property.) The **New-CsNetworkMediaBypassConfiguration** cmdlet creates the object only in memory, so we assign that object to the variable $a.
  
The media bypass configuration is stored with the network configuration settings. Therefore, in line 2 of the example, we save the media bypass configuration changes to the network configuration by calling the **Set-CsNetworkConfiguration** cmdlet and passing the media bypass configuration object ($a) we created in line 1 to the MediaBypassSettings parameter.
  
```
$a = New-CsNetworkMediaBypassConfiguration -AlwaysBypass $true -Enabled $true
Set-CsNetworkConfiguration -MediaBypassSettings $a
```

### EXAMPLE 2

There is no **Set-CsNetworkMediaBypassConfiguration** cmdlet in Skype for Business Server 2015, so in order to modify existing settings you must either create a new configuration (as shown in Example 1) to replace the existing configuration, or you must modify the settings by retrieving the existing settings, modifying them, and then using the **Set-CsNetworkConfiguration** cmdlet to save the changes. This example demonstrates turning off the Always Bypass option by using this latter option.
  
The first line in the example retrieves the existing media bypass settings. It does this by calling the **Get-CsNetworkConfiguration** cmdlet. The call to this cmdlet is within parentheses to ensure the cmdlet is completed before any other part of the command is run. The **Get-CsNetworkConfiguration** cmdlet retrieves all settings for an entire network configuration. Because we're interested in only the media bypass settings, we specify the MediaBypassSettings property to retrieve only those settings. We assign those settings to the variable $a.
  
In line 2 we modify the settings stored in variable $a by assigning the value False ($false) to the AlwaysBypass property. Finally, in line 3 we call the **Set-CsNetworkConfiguration** cmdlet, passing the MediaBypassSettings parameter the variable $a, which saves the change we made to the AlwaysBypass property.
  
```
$a = (Get-CsNetworkConfiguration).MediaBypassSettings
$a.AlwaysBypass = $false
Set-CsNetworkConfiguration -MediaBypassSettings $a
```

## Detailed Description

This cmdlet creates global settings for media bypass of audio connections.
  
Unlike most New- cmdlets in Skype for Business Server 2015, this cmdlet does not immediately save the new configuration; it creates the settings only in memory. The object created by this cmdlet must be saved to a variable and then assigned to the MediaBypassSettings property of the network configuration. (For more details, see the Examples section in this topic.)
  
The settings created with this cmdlet can be retrieved only by accessing the MediaBypassSettings property of the global network configuration. To retrieve these settings, run this command: (Get-CsNetworkConfiguration).MediaBypassSettings.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AlwaysBypass_ <br/> |Optional  <br/> |Boolean  <br/> |Setting this parameter to True will attempt media bypass on all calls.  <br/> Set this parameter value to True only if call admission control (CAC) is disabled. Set this parameter to True only for deployments where:  <br/> - There is no need for bandwidth control.  <br/> - There is no need for fine-grained configuration to determine when bypass should happen.  <br/> - There is full connectivity between gateways and clients.  <br/> If the Enabled parameter is set to True and AlwaysBypass is set to False, bypass logic will use network configuration sites and regions to determine when bypass is possible.  <br/> If you set AlwaysBypass to True but do not also set the value of the Enabled parameter to True, you'll receive a warning message: AlwaysBypass setting is ignored if Enabled is set to false.  <br/> Setting AlwaysBypass and Enabled both to True will auto-generate a bypass ID that will be stored in the BypassID property.  <br/> Default: False  <br/> |
| _BypassID_ <br/> |Optional  <br/> |String  <br/> |The media bypass ID. If the AlwaysBypass parameter is set to True and a value is supplied for this parameter, this BypassID will be associated with all subnets. If AlwaysBypass is False, the BypassID value is associated with all subnets that are not found in network configuration sites and regions.  <br/> This ID must be in the format of a GUID (for example, 96f14dea-5170-429a-b92b-f1cb909c4bb6). However, you will typically not have to set or change this parameter. This value is automatically generated when Enabled is set to True and either: 1) AlwaysBypass is set to True, or 2) the EnableDefaultBypassID parameter is set to True.  <br/> |
| _Enabled_ <br/> |Optional  <br/> |Boolean  <br/> |Set this parameter to True to enable media bypass. At that point bypass decisions will be based on the value of the AlwaysBypass setting as follows:  <br/> - If AlwaysBypass is True, attempt bypass for all calls.  <br/> - If AlwaysBypass is False, use the network configuration site and region to determine whether bypass is possible.  <br/> Default: False  <br/> |
| _EnableDefaultBypassID_ <br/> |Optional  <br/> |Boolean  <br/> |This value applies only when AlwaysBypass is set to False.  <br/> Setting this value to True will automatically generate a default bypass ID. This auto-generated value will be stored in the BypassID property.  <br/> This parameter is useful when there is a well-connected core with remote sites that have bandwidth constrained links. The administrator will need to define only the subnets associated with the remote sites by way of network configuration sites and regions. Any subnets associated with the core need not be defined and bypass will automatically be attempted between those subnets.  <br/> Default: False  <br/> |
| _EnabledForAudioVideoConferences_ <br/> |Optional  <br/> |Boolean  <br/> |Indicates whether media bypass should be used for audio/video conferences. The default value is False ($False).  <br/> |
| _ExternalBypassMode_ <br/> |Optional  <br/> |BypassModeEnumType  <br/> |Reserved for future use. External media bypass is not supported in Skype for Business Server 2015.  <br/> Default: Off  <br/> |
| _InternalBypassMode_ <br/> |Optional  <br/> |BypassModeEnumType  <br/> |The value of this parameter controls when clients connecting from inside the organization's network can try to perform media bypass. If Enabled is set to True, this value will automatically be changed to Any. Other values for this parameter are reserved for future use.  <br/> Default: Off  <br/> |
   
## Input Types

None.
  
## Return Types

Creates an object reference of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.MediaBypassSettingsType.
  
## See also

#### 

[Get-CsNetworkConfiguration](get-csnetworkconfiguration.md)
  
[Set-CsNetworkConfiguration](set-csnetworkconfiguration.md)

