---
title: "Get-CsLisServiceProvider"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 060b0b32-5787-487b-b1d9-7a0c7dd44d80
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsLisServiceProvider
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Retrieves information about the web service provided by the Enhanced 9-1-1 (E9-1-1) Network Routing Provider to validate locations. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsLisServiceProvider
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The **Get-CsLisServiceProvider** cmdlet does not have any parameters (other than the Windows PowerShell common parameters, such as Verbose). There will never be more than one service provider for an E9-1-1 implementation, so this cmdlet will retrieve information about the web service provided by that service provider. 
  
```
Get-CsLisServiceProvider
```

## Detailed Description
<a name="sectionSection1"> </a>

In an Enterprise Voice implementation with E9-1-1, emergency calls must first be routed through an E9-1-1 Network Routing Provider to ensure that the calls are routed to the appropriate Public Safety Answering Point (PSAP). (A PSAP is the agency in the United States that directs the calls to the nearest emergency services, such as police, fire, and ambulance services.) In order to do this, the provider must have a list of locations from the organization that it can then match against the Master Street Address Guide to ensure all locations are valid. This cmdlet retrieves information about a provider, including the name of the provider and a URL for the web service that the organization will use to send the locations.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsLisServiceProvider** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsLisServiceProvider"}
  
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

[Remove-CsLisServiceProvider](remove-cslisserviceprovider.md)
  
[Set-CsLisServiceProvider](set-cslisserviceprovider.md)

