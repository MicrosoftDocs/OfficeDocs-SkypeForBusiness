---
title: "Get-CsLisPort"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c755aa8c-e842-4bb8-bdbf-d61a364eb0bc
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsLisPort
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Retrieves one or more ports from the location configuration database. Each port can be associated with a location, in which case this cmdlet will also retrieve the location information of the ports. This location association is used in an Enhanced 9-1-1 (E9-1-1) Enterprise Voice implementation to notify an emergency services operator of the caller's location. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsLisPort
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

Example 1 retrieves all Location Information Server (LIS) ports and any associated locations that have been defined in the Lync Server deployment.
  
```
Get-CsLisPort
```

### EXAMPLE 2

This example retrieves all information for all ports that have been associated with a location in the city of Redmond. The command begins by calling the **Get-CsLisPort** cmdlet to retrieve all port location associations. This collection of port locations is piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet checks the City property of each item in the collection to determine whether the value is equal to (-eq) Redmond. 
  
```
Get-CsLisPort | Where-Object {$_.City -eq "Redmond"}
```

## Detailed Description
<a name="sectionSection1"> </a>

Enhanced 9-1-1 allows an emergency operator to identify the location of a caller without having to ask the caller for that information. In the case where a caller is calling from a Voice over Internet Protocol (VoIP) connection, that information must be extracted based on various connection factors. The VoIP administrator must configure a location map (called a wiremap) that will determine a caller's location. This cmdlet retrieves information on associations between physical locations and the port through which the client is connected.
  
This cmdlet does not take any parameters (other than the Windows PowerShell common parameters). The cmdlet will retrieve all instances of port to location mappings. To narrow down the information retrieved, you must pipe the output from this cmdlet to another Windows PowerShell cmdlet such as the **Where-Object** cmdlet or the **Select-Object** cmdlet. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsLisPort** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsLisPort"}
  
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

This cmdlet retrieves one or more objects of type System.Management.Automation.PSCustomObject.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Remove-CsLisPort](remove-cslisport.md)
  
[Set-CsLisPort](set-cslisport.md)

