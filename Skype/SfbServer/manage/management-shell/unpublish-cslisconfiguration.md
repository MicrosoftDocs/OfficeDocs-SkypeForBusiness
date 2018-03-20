---
title: "Unpublish-CsLisConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 7fcba482-e1cc-46fa-8b39-fba549eb0fec
description: "Removes the Location Information Server (LIS) configuration from the Central Management store. This cmdlet was introduced in Lync Server 2010."
---

# Unpublish-CsLisConfiguration
 
Removes the Location Information Server (LIS) configuration from the Central Management store. This cmdlet was introduced in Lync Server 2010.
  
```
Unpublish-CsLisConfiguration [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

This command removes the LIS configuration from the Central Management store.
  
```
Unpublish-CsLisConfiguration
```

## Detailed Description

In order to implement Enhanced 9-1-1 (E9-1-1) in Skype for Business Server 2015, you must create a location mapping (called a wiremap). This mapping includes matching physical addresses to ports, subnets, switches, and wireless access points so emergency calls made over an Enterprise Voice connection will reach the nearest emergency operator and provide that operator with the correct location of the caller. This mapping configuration, created by calling cmdlets such as the **Set-CsLisPort** cmdlet and the **Set-CsLisSubnet** cmdlet, is stored in the location configuration database. A configuration can be committed from the location configuration database to the Central Management store by calling the **Publish-CsLisConfiguration** cmdlet, which allows for replication of the data to the Location Information Server. The **Unpublish-CsLisConfiguration** cmdlet removes the LIS configuration from the Central Management store.
  
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
  
[Publish-CsLisConfiguration](publish-cslisconfiguration.md)
  
[Import-CsLisConfiguration](import-cslisconfiguration.md)
  
[Export-CsLisConfiguration](export-cslisconfiguration.md)
  
[Test-CsLisConfiguration](test-cslisconfiguration.md)

