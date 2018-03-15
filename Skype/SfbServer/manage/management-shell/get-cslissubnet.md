---
title: "Get-CsLisSubnet"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 670b50b9-a5ab-4b70-bdb9-bdf3c1b09d0b
description: "Retrieves one or more subnets from the location configuration database. Each subnet can be associated with a location, in which case this cmdlet will also retrieve the location information of the subnets. This location association is used in an Enhanced 9-1-1 (E9-1-1) Enterprise Voice implementation to notify an emergency services operator of the caller's location. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsLisSubnet
 
Retrieves one or more subnets from the location configuration database. Each subnet can be associated with a location, in which case this cmdlet will also retrieve the location information of the subnets. This location association is used in an Enhanced 9-1-1 (E9-1-1) Enterprise Voice implementation to notify an emergency services operator of the caller's location. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsLisSubnet

```

## Examples

### EXAMPLE 1

Example 1 retrieves all Location Information Server (LIS) subnets that have been defined in the Skype for Business Server 2015 deployment.
  
```
Get-CsLisSubnet
```

### EXAMPLE 2

This example retrieves all information for the subnet with the IP address 192.0.10.0. The command begins by calling the **Get-CsLisSubnet** cmdlet to retrieve all subnet location associations. This collection of subnet locations is piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet checks the Subnet property of each item in the collection to determine whether the value is equal to (-eq) 192.0.10.0. Because the Subnet ID must be unique, this command will return, at most, one object.
  
```
Get-CsLisSubnet | Where-Object {$_.Subnet -eq "192.0.10.0"}
```

## Detailed Description

Enhanced 9-1-1 allows an emergency operator to identify the location of a caller without having to ask the caller for that information. In the case where a caller is calling from a Voice over Internet Protocol (VoIP) connection, that information must be extracted based on various connection factors. The VoIP administrator must configure a location map (called a wiremap) that will determine a caller's location. This cmdlet retrieves information on associations between physical locations and the subnet through which calls are routed.
  
This cmdlet does not take any parameters (other than the Windows PowerShell common parameters). The cmdlet will retrieve all instances of subnet to location mappings. To narrow down the information retrieved, you must pipe the output from this cmdlet to another Windows PowerShell cmdlet such as the **Where-Object** cmdlet or the **Select-Object** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|||||
|This cmdlet provides only common Windows PowerShell parameters.  <br/> ||||
   
## Input Types

None.
  
## Return Types

This cmdlet retrieves an object of type System.Management.Automation.PSCustomObject.
  
## See also

#### 

[Remove-CsLisSubnet](remove-cslissubnet.md)
  
[Set-CsLisSubnet](set-cslissubnet.md)

