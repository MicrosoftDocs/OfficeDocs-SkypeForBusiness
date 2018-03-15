---
title: "Get-CsNetworkSubnet"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ad74155a-8d83-42f6-bb1e-8bfc7d57d5b0
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsNetworkSubnet
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Retrieves information about one or more network subnets. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsNetworkSubnet [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example retrieves all subnets within the Lync Server deployment.
  
```
Get-CsNetworkSubnet
```

### EXAMPLE 2

This example retrieves all information about the subnet with the Identity (the Subnet ID) 172.11.15.0.
  
```
Get-CsNetworkSubnet -Identity 172.11.15.0
```

### EXAMPLE 3

This example retrieves all subnets with identities that begin with 172.11..
  
```
Get-CsNetworkSubnet -Filter 172.11.*
```

### EXAMPLE 4

Example 4 retrieves all subnets associated with the Vancouver site. We first call the **Get-CsNetworkSubnet** cmdlet with no parameters, which, as we saw in Example 2, retrieves all defined subnets. We then pipe this collection of subnets to the **Where-Object** cmdlet. The **Where-Object** cmdlet takes that collection and narrows it down to only those subnets with a NetworkSiteID equal to (-eq) Vancouver. 
  
```
Get-CsNetworkSubnet | Where-Object {$_.NetworkSiteID -eq "Vancouver"}
```

## Detailed Description
<a name="sectionSection1"> </a>

Each subnet must be associated with a network site for the purposes of determining the geographic location of the host belonging to this subnet. Use this cmdlet to retrieve information about the subnet, including the Identity (the subnet ID), the number of mask bits, the associated network site, and the description of the subnet.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsNetworkSubnet** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsNetworkSubnet"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Use this parameter to perform a wildcard search of all subnets based on Identity. For example, the Filter value 172.11.\* will retrieve all subnets with an Identity beginning with 172.11. (such as 172.11.10.0, 172.11.25.0, etc.).  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |The unique subnet ID of the subnet you want to retrieve. This value will be an IP address (such as 174.11.12.0).  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the network subnet information from the local replica of the Central Management store, rather than the Central Management store itself.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

Returns one or more objects of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsNetworkSubnet](new-csnetworksubnet.md)
  
[Remove-CsNetworkSubnet](remove-csnetworksubnet.md)
  
[Set-CsNetworkSubnet](set-csnetworksubnet.md)

