---
title: "New-CsNetworkBWPolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: bbc91bd1-453c-4ae6-bb77-3b6be9429ed0
description: "Creates a bandwidth policy in memory that can be applied to the bandwidth policy profile. In Skype for Business Server 2015, the policy applies to either audio or video bandwidth. This cmdlet was introduced in Lync Server 2010."
---

# New-CsNetworkBWPolicy
[]
Creates a bandwidth policy in memory that can be applied to the bandwidth policy profile. In Skype for Business Server 2015, the policy applies to either audio or video bandwidth. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsNetworkBWPolicy -BWLimit <UInt32> -BWPolicyModality <Audio | Video> -BWSessionLimit <UInt32>

```

## Examples

### EXAMPLE 1

This example creates a new bandwidth policy and assigns it to the variable $bwp. All parameters for the **New-CsNetworkBWPolicy** cmdlet are required. In this example we specified a total bandwidth limit (BWLimit) of 2000 kbps and a bandwidth session limit (BWSessionLimit) of 300 kbps, and we applied these limits to video sessions ( `-BWPolicyModality video`).
  
```
$bwp = New-CsNetworkBWPolicy -BWLimit 200 -BWSessionLimit 3000 -BWPolicyModality video
```

### EXAMPLE 2

Example 2 expands on Example 1 by assigning the new bandwidth policy to a policy profile. The command in line 1 is identical to Example 1: it creates video bandwidth limitations. Line 2 then calls the **New-CsNetworkBandwidthPolicyProfile** cmdlet to add that policy to a new profile. The new profile receives an Identity of LowBWLimit. Then we use the BWPolicy parameter, giving it the value $bwp, which is the variable containing the new bandwidth policy we just created in Line 1.
  
```
$bwp = New-CsNetworkBWPolicy -BWLimit 200 -BWSessionLimit 3000 -BWPolicyModality video
New-CsNetworkBandwidthPolicyProfile -Identity LowBWLimit -BWPolicy $bwp
```

## Detailed Description

This cmdlet creates a new bandwidth policy. A bandwidth policy is used to define bandwidth limitations for certain modalities. (In Skype for Business Server 2015, only audio and video modalities can be assigned bandwidth limitations.) The bandwidth policy is created only in memory, so the output must be assigned to a variable and then passed as a value to the BWPolicy parameter of the **New-CsNetworkBandwidthPolicyProfile** cmdlet or the **Set-CsNetworkBandwidthPolicyProfile** cmdlet. Bandwidth policies are applied to policy profiles, which can store multiple policies for a single profile and are part of the global network configuration for call admission control (CAC).
  
Note that the recommended method of assigning audio and video policies is to assign them directly to a bandwidth policy profile by calling the **New-CsNetworkBandwidthPolicyProfile** or the **Set-CsNetworkBandwidthPolicyProfile** cmdlet and specifying values for the AudioBWLimit, AudioBWSessionLimit, VideoBWLimit, and VideoBWSessionLimit parameters.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _BWLimit_ <br/> |Required  <br/> |System.UInt32  <br/> |The maximum total bandwidth, in kbps, for all concurrent sessions of the type specified in the BWPolicyModality parameter.  <br/> |
| _BWPolicyModality_ <br/> |Required  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyModality  <br/> |Determines which type of bandwidth is limited.  <br/> Valid values: Audio, Video  <br/> |
| _BWSessionLimit_ <br/> |Required  <br/> |System.UInt32  <br/> |The maximum bandwidth, in kbps, allowed for a single session of the type specified in the BWPolicyModality parameter.  <br/> |
   
## Input Types

None.
  
## Return Types

Creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyType.
  
## See also

#### 

[New-CsNetworkBandwidthPolicyProfile](new-csnetworkbandwidthpolicyprofile.md)
  
[Set-CsNetworkBandwidthPolicyProfile](set-csnetworkbandwidthpolicyprofile.md)

