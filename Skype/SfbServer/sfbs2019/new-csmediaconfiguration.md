---
title: "New-CsMediaConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3b60c36f-f824-4948-aa46-6745b40b9641
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# New-CsMediaConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Creates a new collection of media settings. These settings can be used to specify such things as the supported level of encryption and the maximum allowed video resolution. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsMediaConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableQoS <$true | $false>] [-EnableSiren <$true | $false>] [-EncryptionLevel <SupportEncryption | RequireEncryption | DoNotSupportEncryption>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-MaxVideoRateAllowed <CIF250K | VGA600K | Hd720p15M>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="sectionSection0"> </a>

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
<a name="sectionSection1"> </a>

This cmdlet creates a new collection of settings that define behaviors for specific media actions.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsMediaConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsMediaConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |A unique identifier specifying the scope at which this configuration is applied (site or service). A configuration at the site scope would be entered as site:\<site name\>, such as site:Redmond. A service would be entered as \<server role\>:\<fqdn\>, such as MediationServer:pool0.litwareinc.com. A media configuration at the global scope will always exist and cannot be removed, so a new global configuration cannot be created.  <br/>  Media configurations created at the service scope can be created only for the A/V Conferencing service, Mediation Server, and Application Server.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableQoS_ <br/> |Optional  <br/> |System.Boolean  <br/> |QoS monitors the quality of voice signals over a network.  <br/> Default: False  <br/> |
| _EnableSiren_ <br/> |Optional  <br/> |System.Boolean  <br/> |By default, the Mediation Server does not negotiate Siren as a possible codec for calls between itself and other Lync clients. If this setting is True, Siren will be included as a possible codec for use between the Mediation Server and other Lync clients.  <br/> Default: False  <br/> |
| _EncryptionLevel_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Media.EncryptionLevel  <br/> |The level of encryption between unified communications devices.  <br/> Valid values:  <br/> SupportEncryption - secure real-time transport protocol (SRTP) will be used if it can be negotiated.  <br/> RequireEncryption - SRTP must be negotiated.  <br/> DoNotSupportEncryption - SRTP must not be used.  <br/> Default: RequireEncryption  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching Set- cmdlet.  <br/> |
| _MaxVideoRateAllowed_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Media.MaxVideoRateAllowed  <br/> |The maximum rate at which video signals will be transferred at the client endpoints.  <br/> Valid values: Hd720p15M, VGA600K, CIF250K  <br/> Hd720p15M - High definition, with a resolution of 1280 x 720 and aspect ratio 16:9.  <br/> VGA600K - VGA, with a resolution of 640 x 480, 25 fps with the aspect ratio 4:3.  <br/> CIF250K - Common Intermediate Format (CIF) video format, 15 fps with a resolution of 352 x 288.  <br/> Note that these values are not case sensitive; values will be converted to appropriate casing when the configuration is created.  <br/> Default: VGA600K  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

Creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.Media.MediaSettings.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Remove-CsMediaConfiguration](remove-csmediaconfiguration.md)
  
[Set-CsMediaConfiguration](set-csmediaconfiguration.md)
  
[Get-CsMediaConfiguration](get-csmediaconfiguration.md)

