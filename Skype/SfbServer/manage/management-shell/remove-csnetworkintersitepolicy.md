---
title: "Remove-CsNetworkInterSitePolicy"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: daf1afc8-cce4-4192-8ba4-05d26817198e
description: "Removes a network inter-site policy that defines bandwidth limitations between sites that are directly linked within a call admission control (CAC) configuration. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsNetworkInterSitePolicy
 
Removes a network inter-site policy that defines bandwidth limitations between sites that are directly linked within a call admission control (CAC) configuration. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsNetworkInterSitePolicy -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

This example removes the network site policy with the Identity Reno_Portland.
  
```
Remove-CsNetworkInterSitePolicy -Identity Reno_Portland
```

### EXAMPLE 2

In Example 2, we remove all network site policies defined within the CAC configuration. We begin by calling the **Get-CsNetworkInterSitePolicy** cmdlet to retrieve a collection of all network site policies. That collection is then piped to the **Remove-CsNetworkInterSitePolicy** cmdlet, which removes each item in the collection.
  
```
Get-CsNetworkInterSitePolicy | Remove-CsNetworkInterSitePolicy
```

## Detailed Description

When network sites share a direct link, bandwidth limitations for audio and video connections can be defined between those two sites. This cmdlet removes a network site policy that associates a bandwidth limitation policy with two directly connected sites.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The unique identifier of the network site policy you want to remove. Network site policies are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies that site policy.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType object. Accepts pipelined input of network inter-site policy objects.
  
## Return Types

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType.
  
## See also

#### 

[New-CsNetworkInterSitePolicy](new-csnetworkintersitepolicy.md)
  
[Set-CsNetworkInterSitePolicy](set-csnetworkintersitepolicy.md)
  
[Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)

