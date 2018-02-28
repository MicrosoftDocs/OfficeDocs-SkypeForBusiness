---
title: "Remove-CsLisSubnet"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f8a87038-cc71-4fec-8496-574da0aa963f
description: "Removes a Location Information Server (LIS) subnet. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsLisSubnet
[]
Removes a Location Information Server (LIS) subnet. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsLisSubnet -Subnet <String> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

Example 1 removes the LIS subnet location entry for the subnet with the IP address 192.10.10.0. The command in this example includes only one (required) parameter: Subnet. The value of the Subnet in this example is an IPv4 address, 192.10.10.0.
  
If this subnet is associated with a location, that location will not be removed, only the subnet will be removed from the location mapping.
  
```
Remove-CsLisSubnet -Subnet 192.10.10.0
```

### EXAMPLE 2

This example removes all subnets that are associated with the location Bldg30/Room1000. The example begins with a call to the **Get-CsLisSubnet** cmdlet, which returns a collection of all LIS subnets. This collection is piped to the **Where-Object** cmdlet, which finds the items in that collection that have a Location property that is equal to (-eq) the string Bldg30/Room1000. Finally, we pipe this collection of subnets with that Location to the **Remove-CsLisSubnet** cmdlet, which removes everything in that collection.
  
Note that, as in Example 1, no locations are removed from the location configuration database, only the subnets that reference those locations are removed. You can remove locations by calling the **Remove-CsLisLocation** cmdlet.
  
```
Get-CsLisSubnet | Where-Object {$_.Location -eq "Bldg30/Room1000"} | Remove-CsLisSubnet
```

## Detailed Description

Enhanced 9-1-1 (E9-1-1) allows an emergency operator to identify the location of a caller without having to ask the caller for that information. In the case where a caller is calling from a Voice over Internet Protocol (VoIP) connection, that information must be extracted based on various connection factors. The VoIP administrator must configure a location map (called a wiremap) that will determine a caller's location. This cmdlet removes a subnet from the location configuration database. Removing the subnet will not remove the location associated with that subnet. Use the **Remove-CsLisLocation** cmdlet to remove a location.
  
If you attempt to remove a subnet that does not exist, no action will be taken and you will not receive an error or a warning message.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Subnet_ <br/> |Required  <br/> |System.String  <br/> |The IP address of the subnet you want to remove. This value will be an IPv4 address (digits separated by periods, such as 192.0.2.0).  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

Accepts pipelined input of Location Information Server (LIS) subnet objects.
  
## Return Types

This cmdlet removes an object of type System.Management.Automation.PSCustomObject.
  
## See also

#### 

[Set-CsLisSubnet](set-cslissubnet.md)
  
[Get-CsLisSubnet](get-cslissubnet.md)
  
[Remove-CsLisLocation](remove-cslislocation.md)

