---
title: "Publish-CsLisConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 54f9d653-075d-4533-b508-231f53b54db4
description: "Publishes the Location Information Server (LIS) configuration to the Central Management store. This cmdlet was introduced in Lync Server 2010."
---

# Publish-CsLisConfiguration
[]
Publishes the Location Information Server (LIS) configuration to the Central Management store. This cmdlet was introduced in Lync Server 2010.
  
```
Publish-CsLisConfiguration [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

This command commits the LIS configuration to the Central Management store.
  
```
Publish-CsLisConfiguration
```

## Detailed Description

In order to implement Enhanced 9-1-1 (E9-1-1) in Skype for Business Server 2015, you must create a location mapping (called a wiremap). This mapping includes matching physical addresses to ports, subnets, switches, and wireless access points so any calls made over an Enterprise Voice connection will reach the nearest emergency operator and provide that operator with the correct location of the caller. This mapping configuration, created by calling cmdlets such as the **Set-CsLisPort** cmdlet and the **Set-CsLisSubnet** cmdlet, is stored in a central location database. This cmdlet commits any changes in the central location database to the Central Management store, allowing the information to be replicated to the Location Information servers so that the locations can be rendered to clients. The configuration can be removed from the Central Management store by calling the **Unpublish-CsLisConfiguration** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

This cmdlet does not return a value.
  
## See also

#### 

[Debug-CsLisConfiguration](debug-cslisconfiguration.md)
  
[Unpublish-CsLisConfiguration](unpublish-cslisconfiguration.md)
  
[Import-CsLisConfiguration](import-cslisconfiguration.md)
  
[Export-CsLisConfiguration](export-cslisconfiguration.md)
  
[Test-CsLisConfiguration](test-cslisconfiguration.md)

