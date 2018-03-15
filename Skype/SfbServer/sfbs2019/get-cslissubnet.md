---
title: "Get-CsLisSubnet"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 670b50b9-a5ab-4b70-bdb9-bdf3c1b09d0b
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsLisSubnet
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Retrieves one or more subnets from the location configuration database. Each subnet can be associated with a location, in which case this cmdlet will also retrieve the location information of the subnets. This location association is used in an Enhanced 9-1-1 (E9-1-1) Enterprise Voice implementation to notify an emergency services operator of the caller's location. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsLisSubnet
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 retrieves all Location Information Server (LIS) subnets that have been defined in the Lync Server deployment.
  
```
Get-CsLisSubnet
```

### EXAMPLE 2

This example retrieves all information for the subnet with the IP address 192.0.10.0. The command begins by calling the **Get-CsLisSubnet** cmdlet to retrieve all subnet location associations. This collection of subnet locations is piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet checks the Subnet property of each item in the collection to determine whether the value is equal to (-eq) 192.0.10.0. Because the Subnet ID must be unique, this command will return, at most, one object. 
  
```
Get-CsLisSubnet | Where-Object {$_.Subnet -eq "192.0.10.0"}
```

## Detailed Description
<a name="sectionSection1"> </a>

Enhanced 9-1-1 allows an emergency operator to identify the location of a caller without having to ask the caller for that information. In the case where a caller is calling from a Voice over Internet Protocol (VoIP) connection, that information must be extracted based on various connection factors. The VoIP administrator must configure a location map (called a wiremap) that will determine a caller's location. This cmdlet retrieves information on associations between physical locations and the subnet through which calls are routed.
  
This cmdlet does not take any parameters (other than the Windows PowerShell common parameters). The cmdlet will retrieve all instances of subnet to location mappings. To narrow down the information retrieved, you must pipe the output from this cmdlet to another Windows PowerShell cmdlet such as the **Where-Object** cmdlet or the **Select-Object** cmdlet. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsLisSubnet** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsLisSubnet"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|||||
|This cmdlet provides only common Windows PowerShell parameters.  <br/> ||||
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet retrieves an object of type System.Management.Automation.PSCustomObject.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Remove-CsLisSubnet](remove-cslissubnet.md)
  
[Set-CsLisSubnet](set-cslissubnet.md)

