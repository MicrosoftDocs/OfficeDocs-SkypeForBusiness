---
title: "Remove-CsTrustedApplicationEndpoint"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c9b96690-d8c2-47f7-bff3-706dbf68d75a
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsTrustedApplicationEndpoint
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes a trusted application endpoint. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsTrustedApplicationEndpoint -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This example removes the endpoint contact with the Identity (in this case the display name) Endpoint 1. Because identities must be unique, this command will remove, at most, one endpoint.
  
```
Remove-CsTrustedApplicationEndpoint -Identity "Endpoint 1"
```

### EXAMPLE 2

This example removes all trusted application endpoints associated with the application tapp2. This is accomplished by first calling the **Get-CsTrustedApplicationEndpoint** cmdlet and passing the ID tapp2 to the ApplicationId parameter. This will return a collection of endpoints that are associated with the tapp2 trusted application. This collection is then piped to the **Remove-CsTrustedApplicationEndpoint** cmdlet, which removes each endpoint in the collection. Keep in mind that this call to the **Get-CsTrustedApplicationEndpoint** cmdlet could retrieve endpoints with the application ID tapp2 from multiple pools, which would result in this command removing trusted application endpoints from multiple pools. 
  
```
Get-CsTrustedApplicationEndpoint -ApplicationId tapp2 | Remove-CsTrustedApplicationEndpoint
```

## Detailed Description
<a name="sectionSection1"> </a>

A trusted application endpoint is an Active Directory contact object that enables routing of calls to a trusted application. This cmdlet removes an existing endpoint contact object from Active Directory Domain Services.
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsTrustedApplicationEndpoint** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsTrustedApplicationEndpoint"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |The Identity (the distinguished name of the contact), SIP address, or display name of the application endpoint to be removed.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact object. Accepts pipelined input of trusted application endpoint objects.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact.
  
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsTrustedApplicationEndpoint](new-cstrustedapplicationendpoint.md)
  
[Set-CsTrustedApplicationEndpoint](set-cstrustedapplicationendpoint.md)
  
[Get-CsTrustedApplicationEndpoint](get-cstrustedapplicationendpoint.md)

