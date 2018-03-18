---
title: "Remove-CsNetworkSite"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 07b543a6-3aa0-4fce-85f9-9ddc75d7b14f
description: "Removes a network site that has been defined for call admission control (CAC) or Enhanced 9-1-1 (E9-1-1). This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsNetworkSite
 
Removes a network site that has been defined for call admission control (CAC) or Enhanced 9-1-1 (E9-1-1). This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsNetworkSite -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

This example removes the site with the Identity Vancouver from the CAC or E9-1-1 configuration.
  
```
Remove-CsNetworkSite -Identity Vancouver
```

### EXAMPLE 2

Example 2 removes all sites that are using the bandwidth policy profile named LowBWProfile from the CAC or E9-1-1 configuration. The example first calls the **Get-CsNetworkSite** cmdlet to retrieve all network sites. This collection of sites is piped to the **Where-Object** cmdlet, which narrows the collection to only those sites that have a BWPolicyProfileID equal to (-eq) LowBWProfile. This new collection is then piped to the **Remove-CsNetworkSite** cmdlet to remove those sites.
  
```
Get-CsNetworkSite | Where-Object {$_.BWPolicyProfileID -eq "LowBWProfile"} | Remove-CsNetworkSite
```

## Detailed Description

Network sites are the offices or locations configured within each region of a CAC or E9-1-1 deployment. This cmdlet removes a site from the CAC or E9-1-1 configuration.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The unique identifier of the network site you want to remove. Sites are created only at the global scope, so you do not need to specify a scope. Instead, you need to specify only the site ID.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType object. Accepts pipelined input of network site objects.
  
## Return Types

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType.
  
## See also

#### 

[New-CsNetworkSite](new-csnetworksite.md)
  
[Set-CsNetworkSite](set-csnetworksite.md)
  
[Get-CsNetworkSite](get-csnetworksite.md)

