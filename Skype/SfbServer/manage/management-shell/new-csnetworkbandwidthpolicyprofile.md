---
title: "New-CsNetworkBandwidthPolicyProfile"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 84940891-37a6-45fc-972d-05b95aa71ba9
description: "Creates a new network bandwidth policy profile. This cmdlet can also be used to set the bandwidth policies within the profile. This cmdlet was introduced in Lync Server 2010."
---

# New-CsNetworkBandwidthPolicyProfile
[]
Creates a new network bandwidth policy profile. This cmdlet can also be used to set the bandwidth policies within the profile. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsNetworkBandwidthPolicyProfile -Identity <XdsGlobalRelativeIdentity> [-AudioBWLimit <String>] [-AudioBWSessionLimit <String>] [-BWPolicy <PSListModifier>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-VideoBWLimit <String>] [-VideoBWSessionLimit <String>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

Example 1 creates a new bandwidth policy profile named LowBWLimits. This new profile will have two policies assigned, an audio policy and a video policy (the only two policies possible in Skype for Business Server 2015). The audio policy is added to the profile by using the AudioBWLimit parameter to assign a limit of (in this case) 2000 kbps to overall audio connections, and the AudioBWSessionLimit parameter to assign 200 kbps as the limit for individual audio sessions. The same is done to create video session limits, but using the VideoBWLimit and VideoBWSessionLimit parameters.
  
```
New-CsNetworkBandwidthPolicyProfile -Identity LowBWLimits -AudioBWLimit 2000 -AudioBWSessionLimit 200 -VideoBWLimit 1400 -VideoBWSessionLimit 500
```

## Detailed Description

As part of call admission control (CAC), a bandwidth policy is used to define bandwidth limitations for certain modalities. (In Skype for Business Server 2015, only audio and video modalities can be assigned bandwidth limitations.) This cmdlet creates a container profile for these policies. You define the individual policies within the container by specifying the audio and video bandwidth limitations when you call this cmdlet.
  
Bandwidth policy profiles are applied to network sites by calling the **New-CsNetworkSite** cmdlet or the **Set-CsNetworkSite** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |A string value that uniquely identifies the policy. All bandwidth policy profiles are created at the global scope. Therefore the scope is implied and only a unique name needs to be specified when creating a new bandwidth policy profile. Note that this value also populates the BWPolicyProfileID property of the profile.  <br/> |
| _AudioBWLimit_ <br/> |Optional  <br/> |System.String  <br/> |The maximum amount of bandwidth to allocate for all audio connections. If a single audio session will cause the audio bandwidth limit to be exceeded, that session will not be allowed to start.  <br/> Expressed in kbps. For example, a value of 1000 would signify 1000 kbps.  <br/> If you supply a value to this parameter, you cannot supply a value to the BWPolicy parameter.  <br/> Default: If you supply a value to the AudioBWSessionLimit parameter but not to AudioBWLimit, AudioBWLimit will default to 0.  <br/> |
| _AudioBWSessionLimit_ <br/> |Optional  <br/> |System.String  <br/> |The maximum amount of bandwidth to allocate per audio session. Expressed in kbps. Value must be 40 or higher.  <br/> If you supply a value to this parameter, you cannot supply a value to the BWPolicy parameter.  <br/> Default: If you supply a value to the AudioBWLimit parameter but not to AudioBWSessionLimit, AudioBWSessionLimit will default to 175.  <br/> |
| _BWPolicy_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |A list of objects containing bandwidth policy profiles. Each object in the list consists of a bandwidth modality (audio or video), a bandwidth limitation, and a bandwidth session limitation.  <br/> If you supply a value to this parameter, you cannot supply a value to the AudioBWLimit, AudioBWSessionLimit, VideoBWLimit, or VideoBWSessionLimit parameter.  <br/> Objects in the list can be created by calling the **New-CsNetworkBWPolicy** cmdlet. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |A description of the bandwidth policy profile. For example, you can use this parameter to clarify the expected use of the profile.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _VideoBWLimit_ <br/> |Optional  <br/> |System.String  <br/> |The maximum amount of bandwidth to allocate for all video connections. If a single video session will cause the video bandwidth limit to be exceeded, that session will not be allowed to start.  <br/> Expressed in kbps. For example, a value of 1000 would signify 1000 kbps.  <br/> If you supply a value to this parameter, you cannot supply a value to the BWPolicy parameter.  <br/> Default: If you supply a value to the VideoBWSessionLimit parameter but not to VideoBWLimit, VideoBWLimit will default to 0.  <br/> |
| _VideoBWSessionLimit_ <br/> |Optional  <br/> |System.String  <br/> |The maximum amount of bandwidth to allocate per video session. Expressed in kbps. Value must be 100 or higher.  <br/> If you supply a value to this parameter, you cannot supply a value to the BWPolicy parameter.  <br/> Default: If you supply a value to the VideoBWLimit parameter but not to VideoBWSessionLimit, VideoBWSessionLimit will default to 700.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

Creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType.
  
## See also

#### 

[Remove-CsNetworkBandwidthPolicyProfile](remove-csnetworkbandwidthpolicyprofile.md)
  
[Set-CsNetworkBandwidthPolicyProfile](set-csnetworkbandwidthpolicyprofile.md)
  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)
  
[New-CsNetworkBWPolicy](new-csnetworkbwpolicy.md)

