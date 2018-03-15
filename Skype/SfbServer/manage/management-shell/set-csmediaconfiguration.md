---
title: "Set-CsMediaConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 768bc273-5253-4569-895d-5b1127386b92

description: "Modifies an existing collection of media settings. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsMediaConfiguration
 
Modifies an existing collection of media settings. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsMediaConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 modifies the media configuration collection with the Identity site:Redmond1; in particular, the command sets the value of the MaxVideoRateAllowed property to Hd720p15M. Note that the value passed to the MaxVideoRateAllowed parameter must be one of the values specified in the parameter description. Also note that the values are not case sensitive; the value entered here as hd720p15m will be automatically converted to the appropriate casing (in this instance, to Hd720p15M).
  
```
Set-CsMediaConfiguration -Identity site:Redmond1 -MaxVideoRateAllowed hd720p15m
```

### EXAMPLE 2

This example modifies the media configuration collection with the Identity site:Redmond1 to have an EncryptionLevel value of DoNotSupportEncryption. Note that this value is not case sensitive; the value was entered as donotsupportencryption, but that value will be accepted as a valid value and will be automatically changed to mixed case (DoNotSupportEncryption).
  
```
Set-CsMediaConfiguration site:Redmond1 -EncryptionLevel donotsupportencryption
```

## Detailed Description

This cmdlet modifies a collection of settings that define media configuration. These actions relate to audio and video calls between client endpoints.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableInCallQoS_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableQoS_ <br/> |Optional  <br/> |System.Boolean  <br/> |QoS monitors the quality of voice signals over a network.  <br/> |
| _EnableRtpRtcpMultiplexing_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableSiren_ <br/> |Optional  <br/> |System.Boolean  <br/> |By default, the Mediation Server does not negotiate Siren as a possible codec for calls between itself and other clients. If this setting is True, Siren will be included as a possible codec for use between the Mediation Server and other clients.  <br/> |
| _EnableVideoBasedSharing_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EncryptionLevel_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Media.EncryptionLevel  <br/> |The level of encryption between unified communications devices.  <br/> Valid values:  <br/> SupportEncryption - secure real-time transport protocol (SRTP) will be used if it can be negotiated.  <br/> RequireEncryption - SRTP must be negotiated.  <br/> DoNotSupportEncryption - SRTP must not be used.  <br/> This value is not case sensitive. (For details, see the Examples in this topic.)  <br/> Default: RequireEncryption  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the media configuration settings you want to change. This identifier specifies the scope at which this configuration is applied (global, site, or service).  <br/> |
| _InCallQoSIntervalSeconds_ <br/> |Optional  <br/> |System.UInt16  <br/> |The number of seconds for the interval.  <br/> |
| _Instance_ <br/> |Optional  <br/> |MediaSettings  <br/> |An instance of the Microsoft.Rtc.Management.WritableConfig.Settings.Media.MediaSettings object. You can retrieve this object by calling the **Get-CsMediaConfiguration** cmdlet with a specific Identity. You can then assign new values to the properties of that object, and then save those changes by passing the object to the **Set-CsMediaConfiguration** cmdlet. <br/> |
| _MaxVideoRateAllowed_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Media.MaxVideoRateAllowed  <br/> |The maximum rate at which video signals will be transferred at the client endpoints.  <br/> Valid values: Hd720p15M, VGA600K, CIF250K  <br/> Hd720p15M - High definition, with a resolution of 1280 x 720 and aspect ratio 16:9.  <br/> VGA600K - VGA, with a resolution of 640 x 480, 25 fps with the aspect ratio 4:3.  <br/> CIF250K - Common Intermediate Format (CIF) video format, 15 fps with a resolution of 352 x 288.  <br/> Note that these values are not case sensitive; values will be converted to appropriate casing when the configuration is created. (For details, see the Examples in this topic.)  <br/> Default: VGA600K  <br/> > [!NOTE]> This parameter is no longer used for Lync Server 2013 clients in Lync Server 2013 conferences but is still used for legacy clients joining a Lync Server 2013 conference.           |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableAVBundling_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableDtls_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableH264StdCodec_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableRtx_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableSilkForAudioVideoConferences_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.Media.MediaSettings object. Accepts pipelined input of media configuration objects.
  
## Return Types

The **Set-CsMediaConfiguration** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Media.MediaSettings object.
  
## See also

#### 

[New-CsMediaConfiguration](new-csmediaconfiguration.md)
  
[Remove-CsMediaConfiguration](remove-csmediaconfiguration.md)
  
[Get-CsMediaConfiguration](get-csmediaconfiguration.md)

