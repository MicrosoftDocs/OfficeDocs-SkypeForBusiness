---
title: "Remove-CsLisServiceProvider"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d26302bf-7794-4125-af80-ba7c92096b6d
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsLisServiceProvider
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes an object containing information about the web service provided by the Enhanced 9-1-1 (E9-1-1) Network Routing Provider to verify locations. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsLisServiceProvider [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example removes the service provider web service from the E9-1-1 implementation. There will only be, at most, one service provider defined, which will be removed by this cmdlet.
  
```
Remove-CsLisServiceProvider
```

## Detailed Description
<a name="sectionSection1"> </a>

In an Enterprise Voice implementation with E9-1-1, emergency calls must first be routed through an E9-1-1 Network Routing Provider to ensure that the calls are routed to the appropriate Public Safety Answering Point (PSAP). (A PSAP is the agency in the United States that directs the calls to the nearest emergency services, such as police, fire, and ambulance services.) In order to do this, the provider must have a list of locations from the organization that it can then match against the Master Street Address Guide to ensure all locations are valid. This cmdlet removes an entry for a provider; after running this cmdlet there will be no web service access to the provider.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsLisServiceProvider** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsLisServiceProvider"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Accepts pipelined input of a Location Information Server (LIS) service provider object.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet does not return an object or a value. It removes an object of type System.Management.Automation.PSCustomObject.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Set-CsLisServiceProvider](set-cslisserviceprovider.md)
  
[Get-CsLisServiceProvider](get-cslisserviceprovider.md)

