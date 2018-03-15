---
title: "Get-CsLisCivicAddress"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6538b811-6b74-4c57-95f7-e1496df62e7f
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsLisCivicAddress
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Retrieves only the address portion of one or more locations in the location configuration database for Enhanced 9-1-1 (E9-1-1). This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsLisCivicAddress
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example retrieves all civic addresses from the location database. The **Get-CsLisCivicAddress** cmdlet does not accept any parameters (other than the common Windows PowerShell parameters such as Verbose). Therefore any call to the **Get-CsLisCivicAddress** cmdlet will always return all civic addresses. See Example 2 for a command that will allow you to retrieve more specific results. 
  
```
Get-CsLisCivicAddress
```

### EXAMPLE 2

In this example, all the civic addresses in the city of Redmond are retrieved. The example begins with a call to the **Get-CsLisCivicAddress** cmdlet, which retrieves a collection of all civic addresses in the location database. This collection is then piped to the **Where-Object** cmdlet, which will return only those items in the collection with a City property value equal to (-eq) Redmond. 
  
```
Get-CsLisCivicAddress | Where-Object {$_.City -eq "Redmond"}
```

### EXAMPLE 3

Example 3 retrieves all Location Information Server (LIS) civic addresses that have been validated against the Master Street Address Guide (MSAG).
  
```
Get-CsLisCivicAddress | Where-Object {$_.MSAGValid -eq $true}
```

## Detailed Description
<a name="sectionSection1"> </a>

E9-1-1 enables those who answer emergency calls to determine the caller's geographic location without having to ask the caller for that information. In Lync Server, the location is determined based on mapping the caller's port, subnet, switch, or wireless access point to a specific location. This cmdlet retrieves one or more of the addresses associated with these locations.
  
This cmdlet differs from the **Get-CsLisLocation** cmdlet in that it returns only unique addresses. It does not return the company name or a location name, it returns only address information. It also returns a flag (MSAGValid) that specifies whether the address has been validated against the Master Street Address Guide. This flag can be automatically updated by running the **Test-CsLisCivicAddress** cmdlet. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsLisCivicAddress** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsLisCivicAddress"}
  
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

[Test-CsLisCivicAddress](test-csliscivicaddress.md)
  
[Get-CsLisLocation](get-cslislocation.md)

