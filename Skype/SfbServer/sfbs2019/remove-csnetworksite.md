---
title: "Remove-CsNetworkSite"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 07b543a6-3aa0-4fce-85f9-9ddc75d7b14f
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsNetworkSite
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes a network site that has been defined for call admission control (CAC) or Enhanced 9-1-1 (E9-1-1). This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsNetworkSite -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

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
<a name="sectionSection1"> </a>

Network sites are the offices or locations configured within each region of a CAC or E9-1-1 deployment. This cmdlet removes a site from the CAC or E9-1-1 configuration.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsNetworkSite** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsNetworkSite"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The unique identifier of the network site you want to remove. Sites are created only at the global scope, so you do not need to specify a scope. Instead, you need to specify only the site ID.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType object. Accepts pipelined input of network site objects.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsNetworkSite](new-csnetworksite.md)
  
[Set-CsNetworkSite](set-csnetworksite.md)
  
[Get-CsNetworkSite](get-csnetworksite.md)

