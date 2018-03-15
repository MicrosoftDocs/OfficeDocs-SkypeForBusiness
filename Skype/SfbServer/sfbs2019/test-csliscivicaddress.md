---
title: "Test-CsLisCivicAddress"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4079e767-3339-40c9-b7cd-08ec6c9d2c25
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Test-CsLisCivicAddress
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Tests one or more civic addresses against the Master Street Address Guide. This cmdlet was introduced in Lync Server 2010.
  
```
Test-CsLisCivicAddress [-City <String>] [-Confirm [<SwitchParameter>]] [-Country <String>] [-HouseNumber <String>] [-HouseNumberSuffix <String>] [-PostalCode <String>] [-PostDirectional <String>] [-PreDirectional <String>] [-State <String>] [-StreetName <String>] [-StreetSuffix <String>] [-UpdateValidationStatus <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This command validates the address with the properties matching the values specified in these parameters against the Master Street Address Guide. Notice the inclusion of the UpdateValidationStatus parameter at the end: this will update the MSAGValid property of the address.
  
```
Test-CsLisCivicAddress -HouseNumber 1234 -HouseNumberSuffix "" -PreDirectional "" -StreetName Main -StreetSuffix St -PostDirectional "" -City Redmond -State WA -PostalCode 99999 -Country US -UpdateValidationStatus
```

### EXAMPLE 2

This example shows how to test all LIS civic addresses. The example begins with a call to the **Get-CsLisCivicAddress** cmdlet to retrieve all civic addresses defined in the location database. These addresses are piped to the **Test-CsLisCivicAddress** cmdlet, which uses the E9-1-1 Network Routing Provider web service to validate each address. 
  
```
Get-CsLisCivicAddress | Test-CsLisCivicAddress -UpdateValidationStatus
```

## Detailed Description
<a name="sectionSection1"> </a>

In an Enterprise Voice implementation with Enhanced 9-1-1 (E9-1-1), user locations are determined based on location maps that map a subnet, port, switch, or wireless access point to a location. (In the absence of a connection to a mapped location, the user may be asked to input their location manually.) The addresses of these locations must be validated against the Master Street Address Guide (MSAG) by the E9-1-1 Network Routing Provider. This cmdlet uses the web service of that provider to validate mapped addresses. You can set up a service provider by calling the **Set-CsLisServiceProvider** cmdlet. 
  
If you want to update the MSAGValid property of the civic address, be sure to include the UpdateValidationStatus parameter in your call to the **Test-CsLisCivicAddress** cmdlet. Use the **Get-CsLisCivicAddress** cmdlet to retrieve civic addresses. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Test-CsLisCivicAddress** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsLisCivicAddress"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _City_ <br/> |Optional  <br/> |System.String  <br/> |The location city.  <br/> Maximum length: 64 characters.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Country_ <br/> |Optional  <br/> |System.String  <br/> |The country/region this location is in.  <br/> Maximum length: 2 characters  <br/> |
| _HouseNumber_ <br/> |Optional  <br/> |System.String  <br/> |The house number of the location. For a company, this is the number on the street where the company is located.  <br/> Maximum length: 10 characters  <br/> |
| _HouseNumberSuffix_ <br/> |Optional  <br/> |System.String  <br/> |Additional information for the house number, such as 1/2 or A. For example, 1234 1/2 Oak Street or 1234 A Elm Street.  <br/> Maximum length: 5 characters  <br/> |
| _PostalCode_ <br/> |Optional  <br/> |System.String  <br/> |The postal code associated with this location.  <br/> Maximum length: 10 characters  <br/> |
| _PostDirectional_ <br/> |Optional  <br/> |System.String  <br/> |The directional designation of a street name. For example, NE or NW for Main Street NE or 7th Avenue NW.  <br/> Maximum length: 2 characters  <br/> |
| _PreDirectional_ <br/> |Optional  <br/> |System.String  <br/> |The directional designation for a street name that precedes the name of the street. For example, NE or NW for NE Main Street or NW 7th Avenue.  <br/> Maximum length: 2 characters  <br/> |
| _State_ <br/> |Optional  <br/> |System.String  <br/> |The state or province associated with this location.  <br/> Maximum length: 2 characters  <br/> |
| _StreetName_ <br/> |Optional  <br/> |System.String  <br/> |The name of the street for this location.  <br/> Maximum length: 60 characters  <br/> |
| _StreetSuffix_ <br/> |Optional  <br/> |System.String  <br/> |The type of street designated in a street name, such as Street, Avenue, or Court.  <br/> Maximum length: 10 characters  <br/> |
| _UpdateValidationStatus_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Including this parameter will change the MSAGValid property of the civic address depending on whether the address is validated through this cmdlet. If the address is valid, MSAGValid will be set to True. Omitting this parameter will leave the MSAGValid value unchanged.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Accepts pipelined input containing a Location Information Server (LIS) civic address object.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet does not return a value.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsLisCivicAddress](get-csliscivicaddress.md)

