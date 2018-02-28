---
title: "Get-CsNetworkInterSitePolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a4a64048-f8d7-483a-9565-0c6f3b0937b7
description: "Retrieves one or more network inter-site policies, which define bandwidth limitations between sites that are directly linked within a call admission control (CAC) configuration. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsNetworkInterSitePolicy
[]
Retrieves one or more network inter-site policies, which define bandwidth limitations between sites that are directly linked within a call admission control (CAC) configuration. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsNetworkInterSitePolicy [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Calling the **Get-CsNetworkInterSitePolicy** cmdlet with no parameters retrieves all network site policies defined between two directly linked network sites.
  
```
Get-CsNetworkInterSitePolicy
```

### EXAMPLE 2

This example retrieves the network site policy with the Identity Reno_Portland.
  
```
Get-CsNetworkInterSitePolicy -Identity Reno_Portland
```

### EXAMPLE 3

Example 3 retrieves all network site policies that have the string Reno anywhere within the Identity value. The wildcard characters (\*) within the value passed to the Filter parameter signify "any character or set of characters." In other words, the string \*Reno\* will match Identity values that begin with any character or characters, followed by the string Reno, followed by any character or characters.
  
```
Get-CsNetworkInterSitePolicy -Filter *Reno*
```

### EXAMPLE 4

This example retrieves all network site policies that do not have a bandwidth policy profile assigned. The command begins by calling the **Get-CsNetworkInterSitePolicy** cmdlet, which, as we saw in Example 1, retrieves a collection of all network site policies. This collection is then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet narrows the collection down to only those site policies that don't have a bandwidth policy profile assigned. It does this by comparing to see if the BWPolicyProfileID property of each site policy is equal to (-eq) Null ($null).
  
```
Get-CsNetworkInterSitePolicy | Where-Object {$_.BWPolicyProfileID -eq $null}
```

## Detailed Description

When network sites share a direct link, bandwidth limitations for audio and video connections can be defined between those two sites. This cmdlet retrieves one or more network site policies that associate bandwidth limitation settings with directly connected sites.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |A string containing wildcard characters that will search for policies with Identity values matching the wildcard string.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The unique identifier of the network site policy you want to retrieve. Network site policies are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies that policy.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the network inter-site policy information from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

Retrieves an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType.
  
## See also

#### 

[New-CsNetworkInterSitePolicy](new-csnetworkintersitepolicy.md)
  
[Remove-CsNetworkInterSitePolicy](remove-csnetworkintersitepolicy.md)
  
[Set-CsNetworkInterSitePolicy](set-csnetworkintersitepolicy.md)

