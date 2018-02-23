---
title: "Set-CsNetworkInterSitePolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 973979bc-db2c-47a6-909e-5949a927f51c
description: "Modifies an existing network inter-site policy that defines bandwidth limitations between sites that are directly linked within a call admission control (CAC) configuration. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsNetworkInterSitePolicy
[]
Modifies an existing network inter-site policy that defines bandwidth limitations between sites that are directly linked within a call admission control (CAC) configuration. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsNetworkInterSitePolicy [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

This example modifies the network site policy with the Identity Reno_Portland. We use the BWPolicyProfileID parameter to change the bandwidth policy profile associated with this network site policy to HighBWLimits.
  
```
Set-CsNetworkInterSitePolicy -Identity Reno_Portland -BWPolicyProfileID HighBWLimits
```

## Detailed Description

When network sites share a direct link, bandwidth limitations for audio and video connections can be defined between those two sites. This cmdlet modifies a network inter-site policy that associates a bandwidth limitation policy with two directly connected sites.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _BWPolicyProfileID_ <br/> |Optional  <br/> |String  <br/> |The Identity of the bandwidth policy profile that will define the limitations for this site policy. You can retrieve a list of available profiles by calling the **Get-CsNetworkBandwidthPolicyProfile** cmdlet. <br/> |
| _Confirm_ <br/> |Optional  <br/> |.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |XdsGlobalRelativeIdentity  <br/> |The unique identifier of the network site policy you want to modify. Network site policies are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies that site policy.  <br/> |
| _Instance_ <br/> |Optional  <br/> |InterNetworkSitePolicyType  <br/> |An object reference to a site policy that has been modified in memory. This object must be of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType, and can be retrieved by calling the **Get-CsNetworkInterSitePolicy** cmdlet. <br/> |
| _NetworkSiteID1_ <br/> |Optional  <br/> |String  <br/> |The Identity (NetworkSiteID) of one of the two sites associated with this policy. The combination of NetworkSiteID1 and NetworkSiteID2 must be unique (for example, you can't have two site policies defined that connect Reno and Portland).  <br/> |
| _NetworkSiteID2_ <br/> |Optional  <br/> |String  <br/> |The Identity (NetworkSiteID) of one of the two sites associated with this policy. The combination of NetworkSiteID1 and NetworkSiteID2 must be unique (for example, you can't have two site policies defined that connect Reno and Portland).  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType object. Accepts pipelined input of network inter-site policy objects.
  
## Return Types

This cmdlet does not return a value. It modifies an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType.
  
## See also

#### 

[New-CsNetworkInterSitePolicy](new-csnetworkintersitepolicy.md)
  
[Remove-CsNetworkInterSitePolicy](remove-csnetworkintersitepolicy.md)
  
[Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)

