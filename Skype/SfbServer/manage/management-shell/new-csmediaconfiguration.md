---
title: "New-CsMediaConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3b60c36f-f824-4948-aa46-6745b40b9641

description: "Creates a new collection of media settings. These settings can be used to specify such things as the supported level of encryption and the maximum allowed video resolution. This cmdlet was introduced in Lync Server 2010."
---

# New-CsMediaConfiguration
[]
Creates a new collection of media settings. These settings can be used to specify such things as the supported level of encryption and the maximum allowed video resolution. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsMediaConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableInCallQoS <$true | $false>] [-EnableQoS <$true | $false>] [-EnableRtpRtcpMultiplexing <$true | $false>] [-EnableSiren <$true | $false>] [-EnableVideoBasedSharing <$true | $false>] [-EncryptionLevel <SupportEncryption | RequireEncryption | DoNotSupportEncryption>] [-Force <SwitchParameter>] [-InCallQoSIntervalSeconds <UInt16>] [-InMemory <SwitchParameter>] [-MaxVideoRateAllowed <CIF250K | VGA600K | Hd720p15M>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

Example 1 uses the **New-CsMediaConfiguration** cmdlet to create a new media configuration with the Identity site:Redmond1. This new configuration requires both parties involved in a multimedia conversation to use encryption. That requirement is put in place by adding the EncryptionLevel parameter and setting the parameter value to RequireEncryption.
  
```
New-CsMediaConfiguration -Identity site:Redmond1 -EncryptionLevel RequireEncryption
```

### EXAMPLE 2

This example uses the **New-CsMediaConfiguration** cmdlet to create a new media configuration with the Identity MediationServer:pool0.litwareinc.com. This new configuration will have an EnableSiren value of True, which means that Siren is enabled for calls involving this Mediation Server.
  
```
New-CsMediaConfiguration -Identity MediationServer:pool0.litwareinc.com -EnableSiren $True
```

## Detailed Description

This cmdlet creates a new collection of settings that define behaviors for specific media actions.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |A unique identifier specifying the scope at which this configuration is applied (site or service). A configuration at the site scope would be entered as site:\<site name\>, such as site:Redmond. A service would be entered as \<server role\>:\<fqdn\>, such as MediationServer:pool0.litwareinc.com. A media configuration at the global scope will always exist and cannot be removed, so a new global configuration cannot be created.  <br/>  Media configurations created at the service scope can be created only for the A/V Conferencing service, Mediation Server, and Application Server. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableInCallQoS_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, enables call Quality of Service (QoS) settings.  <br/> |
| _EnableQoS_ <br/> |Optional  <br/> |System.Boolean  <br/> |QoS monitors the quality of voice signals over a network.  <br/> Default: False  <br/> |
| _EnableRtpRtcpMultiplexing_ <br/> |Optional  <br/> |System.Boolean  <br/> | `true` to enable the setting; otherwise `false`.  <br/> |
| _EnableSiren_ <br/> |Optional  <br/> |System.Boolean  <br/> |By default, the Mediation Server does not negotiate Siren as a possible codec for calls between itself and clients. If this setting is True, Siren will be included as a possible codec for use between the Mediation Server and other clients.  <br/> Default: False  <br/> |
| _EnableVideoBasedSharing_ <br/> |Optional  <br/> |System.Boolean  <br/> | `true` to enable the setting; otherwise `false`.  <br/> |
| _EncryptionLevel_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Media.EncryptionLevel  <br/> |The level of encryption between unified communications devices.  <br/> Valid values:  <br/> SupportEncryption - secure real-time transport protocol (SRTP) will be used if it can be negotiated.  <br/> RequireEncryption - SRTP must be negotiated.  <br/> DoNotSupportEncryption - SRTP must not be used.  <br/> Default: RequireEncryption  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _InCallQoSIntervalSeconds_ <br/> |Optional  <br/> |System.UInt16  <br/> |Specifies the interval between call QoS actions.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _MaxVideoRateAllowed_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Media.MaxVideoRateAllowed  <br/> |The maximum rate at which video signals will be transferred at the client endpoints.  <br/> Valid values: Hd720p15M, VGA600K, CIF250K  <br/> Hd720p15M - High definition, with a resolution of 1280 x 720 and aspect ratio 16:9.  <br/> VGA600K - VGA, with a resolution of 640 x 480, 25 fps with the aspect ratio 4:3.  <br/> CIF250K - Common Intermediate Format (CIF) video format, 15 fps with a resolution of 352 x 288.  <br/> Note that these values are not case sensitive; values will be converted to appropriate casing when the configuration is created.  <br/> Default: VGA600K  <br/> > [!NOTE]> This parameter is no longer used for Lync Server 2013 clients in Lync Server 2013 conferences but is still used for legacy clients joining a Lync Server 2013 conference.           |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableAVBundling_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableDtls_ <br/> |Optional  <br/> |System.Boolean  <br/> | `true` to enable the Datagram Transport Security Layer; otherwise `false`.  <br/> |
| _EnableH264StdCodec_ <br/> |Optional  <br/> |System.Boolean  <br/> | `true` to enable the setting; otherwise `false`.  <br/> |
| _EnableRtx_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableSilkForAudioVideoConferences_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

Creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.Media.MediaSettings.
  
## See also

#### 

[Remove-CsMediaConfiguration](remove-csmediaconfiguration.md)
  
[Set-CsMediaConfiguration](set-csmediaconfiguration.md)
  
[Get-CsMediaConfiguration](get-csmediaconfiguration.md)

