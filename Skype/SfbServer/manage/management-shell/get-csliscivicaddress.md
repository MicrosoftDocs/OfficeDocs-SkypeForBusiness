---
title: "Get-CsLisCivicAddress"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6538b811-6b74-4c57-95f7-e1496df62e7f
description: "Retrieves only the address portion of one or more locations in the location configuration database for Enhanced 9-1-1 (E9-1-1). This cmdlet was introduced in Lync Server 2010."
---

# Get-CsLisCivicAddress
 
Retrieves only the address portion of one or more locations in the location configuration database for Enhanced 9-1-1 (E9-1-1). This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsLisCivicAddress

```

## Examples

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

E9-1-1 enables those who answer emergency calls to determine the caller's geographic location without having to ask the caller for that information. In Skype for Business Server 2015, the location is determined based on mapping the caller's port, subnet, switch, or wireless access point to a specific location. This cmdlet retrieves one or more of the addresses associated with these locations.
  
This cmdlet differs from the **Get-CsLisLocation** cmdlet in that it returns only unique addresses. It does not return the company name or a location name, it returns only address information. It also returns a flag (MSAGValid) that specifies whether the address has been validated against the Master Street Address Guide. This flag can be automatically updated by running the **Test-CsLisCivicAddress** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|||||
|This cmdlet provides only common Windows PowerShell parameters.  <br/> ||||
   
## Input Types

None.
  
## Return Types

This cmdlet retrieves one or more objects of type System.Management.Automation.PSCustomObject.
  
## See also

#### 

[Test-CsLisCivicAddress](test-csliscivicaddress.md)
  
[Get-CsLisLocation](get-cslislocation.md)

