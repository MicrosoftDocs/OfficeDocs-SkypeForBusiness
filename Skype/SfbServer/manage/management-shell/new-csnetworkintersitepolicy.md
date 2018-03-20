---
title: "New-CsNetworkInterSitePolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e127153f-a1c3-4a31-8dd3-f08d45eca800
description: "Creates a new network inter-site policy that defines bandwidth limitations between sites that are directly linked within a call admission control (CAC) configuration. This cmdlet was introduced in Lync Server 2010."
---

# New-CsNetworkInterSitePolicy
 
Creates a new network inter-site policy that defines bandwidth limitations between sites that are directly linked within a call admission control (CAC) configuration. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsNetworkInterSitePolicy -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

This example creates a new network inter-site policy that limits bandwidth between the connected sites Reno and Portland. The bandwidth limitations for audio and video connections between these sites are limited based on the setting configured for the bandwidth policy profile LowBWLimits.
  
```
New-CsNetworkInterSitePolicy -Identity Reno_Portland -NetworkSiteID1 Reno -NetworkSiteID2 Portland -BWPolicyProfileID LowBWLimits
```

## Detailed Description

When network sites share a direct link, bandwidth limitations for audio and video connections can be defined between those two sites. This cmdlet creates a network site policy that associates a bandwidth limitation policy with two directly connected sites.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |A unique identifier for the newly created network inter-site policy. Network inter-site policies are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies that site policy.  <br/> |
| _InterNetworkSitePolicyID_ <br/> |Required  <br/> |System.String  <br/> |This value is the same as the Identity. You cannot specify both an Identity and an InterNetworkSitePolicyID; a value entered for one will be automatically used for both.  <br/> |
| _NetworkSiteID1_ <br/> |Required  <br/> |System.String  <br/> |The Identity (NetworkSiteID) of one of the two sites associated with this policy. The combination of NetworkSiteID1 and NetworkSiteID2 must be unique (for example, you can't have two site policies defined that connect Reno and Portland).  <br/> |
| _NetworkSiteID2_ <br/> |Required  <br/> |System.String  <br/> |The Identity (NetworkSiteID) of one of the two sites associated with this policy. The combination of NetworkSiteID1 and NetworkSiteID2 must be unique (for example, you can't have two site policies defined that connect Reno and Portland).  <br/> |
| _BWPolicyProfileID_ <br/> |Optional  <br/> |System.String  <br/> |The Identity of the bandwidth policy profile that will define the limitations for this site policy. You can retrieve a list of available profiles by calling the **Get-CsNetworkBandwidthPolicyProfile** cmdlet. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

Creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType.
  
## See also

#### 

[Remove-CsNetworkInterSitePolicy](remove-csnetworkintersitepolicy.md)
  
[Set-CsNetworkInterSitePolicy](set-csnetworkintersitepolicy.md)
  
[Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)

