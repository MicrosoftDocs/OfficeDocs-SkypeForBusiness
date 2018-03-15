---
title: "Remove-CsNetworkRegion"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 661dce40-f601-4181-b8f1-3277a76d5df4
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsNetworkRegion
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes an existing network region. Network regions represent network hubs or backbones in an enterprise network. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsNetworkRegion -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 removes the network region with the Identity NorthAmerica. Because identities are unique this command removes only one network region.
  
```
Remove-CsNetworkRegion -Identity NorthAmerica
```

### EXAMPLE 2

This example removes all network regions associated with the central site Redmond. The command begins by calling the **Get-CsNetworkRegion** cmdlet, with no parameters, to retrieve a collection of all network regions defined for the Lync Server deployment. This collection is then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet filters this collection to return only those items (network regions) where the CentralSite value is equal to (-eq) site:Redmond. After narrowing the collection down to those items, this new collection is piped to the **Remove-CsNetworkRegion** cmdlet, which removes every item in that collection. 
  
```
Get-CsNetworkRegion | Where-Object {$_.CentralSite -eq "site:Redmond"} | Remove-CsNetworkRegion
```

### EXAMPLE 3

This example removes the network region with the Identity NorthAmerica. However, a region cannot be removed if it is associated with a site. So this example first removes any association between the NorthAmerica region and a site.
  
The example begins by calling the **Get-CsNetworkSite** cmdlet, with no parameters, to retrieve a collection of all network sites defined for the Lync Server deployment. This collection is then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet filters this collection to return only those items (network sites) where the NetworkRegionID value is equal to (-eq) NorthAmerica. After narrowing the collection down to those items, this new collection is piped to the **Set-CsNetworkSite** cmdlet. For each site containing the NetworkRegionID NorthAmerica, we set the NetworkRegionID to Null ($null). This removes the reference to the region on that site. However, a site can't have a bypass ID if it isn't associated with a site. So in addition to removing the reference to the region by setting the NetworkRegionID to Null, we must also remove the bypass association by setting BypassID to Null. 
  
After line 1 completes, any site that was associated with the NorthAmerica region is no longer tied to a region or to any bypass settings. At this point we can call line 2, which removes the network region.
  
```
Get-CsNetworkSite | Where-Object {$_.NetworkRegionID -eq "NorthAmerica"} | Set-CsNetworkSite -NetworkRegionID $null -BypassID $null
Remove-CsNetworkRegion -Identity "NorthAmerica"
```

## Detailed Description
<a name="sectionSection1"> </a>

A network region interconnects various parts of a network across multiple geographic areas. Every network region must be associated with a central site. The central site is the data center site on which the bandwidth policy service is running. Use this cmdlet to remove a network region.
  
Note that a network region cannot be removed if it is associated with a network site (in other words, the NetworkRegionID of any site is equal to the Identity of the region). If you attempt to remove a region associated with a site you'll receive an error message.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsNetworkRegion** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsNetworkRegion"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The unique identifier of the network region you want to remove. The Identity will be in the form of a string that uniquely identifies that region.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionType object. Accepts pipelined input of network region objects.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionType.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsNetworkRegion](new-csnetworkregion.md)
  
[Set-CsNetworkRegion](set-csnetworkregion.md)
  
[Get-CsNetworkRegion](get-csnetworkregion.md)

