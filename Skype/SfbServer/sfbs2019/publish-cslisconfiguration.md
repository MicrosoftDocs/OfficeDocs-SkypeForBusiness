---
title: "Publish-CsLisConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 54f9d653-075d-4533-b508-231f53b54db4
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Publish-CsLisConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Publishes the Location Information Server (LIS) configuration to the Central Management store. This cmdlet was introduced in Lync Server 2010.
  
```
Publish-CsLisConfiguration [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

This command commits the LIS configuration to the Central Management store.
  
```
Publish-CsLisConfiguration
```

## Detailed Description
<a name="sectionSection1"> </a>

In order to implement Enhanced 9-1-1 (E9-1-1) in Lync Server, you must create a location mapping (called a wiremap). This mapping includes matching physical addresses to ports, subnets, switches, and wireless access points so any calls made over an Enterprise Voice connection will reach the nearest emergency operator and provide that operator with the correct location of the caller. This mapping configuration, created by calling cmdlets such as the **Set-CsLisPort** cmdlet and the **Set-CsLisSubnet** cmdlet, is stored in a central location database. This cmdlet commits any changes in the central location database to the Central Management store, allowing the information to be replicated to the Location Information servers so that the locations can be rendered to clients. The configuration can be removed from the Central Management store by calling the **Unpublish-CsLisConfiguration** cmdlet. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Publish-CsLisConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Publish-CsLisConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None.
  
## Return Types
<a name="sectionSection3"> </a>

This cmdlet does not return a value.
  
## See also
<a name="sectionSection3"> </a>

#### 

[Debug-CsLisConfiguration](debug-cslisconfiguration.md)
  
[Unpublish-CsLisConfiguration](unpublish-cslisconfiguration.md)
  
[Import-CsLisConfiguration](import-cslisconfiguration.md)
  
[Export-CsLisConfiguration](export-cslisconfiguration.md)
  
[Test-CsLisConfiguration](test-cslisconfiguration.md)

