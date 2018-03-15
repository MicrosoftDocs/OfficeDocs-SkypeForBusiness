---
title: "Remove-CsTelemetryConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b7bf54a1-93ce-45d9-bb5f-5c988f4a7547

description: "Use the Remove-CsTelemetryConfiguration cmdlet to remove an existing telemetry configuration. UNRESOLVED_TOKEN_VAL(PS_TelemetryDataStatement)"
---

# Remove-CsTelemetryConfiguration
 
Use the **Remove-CsTelemetryConfiguration** cmdlet to remove an existing telemetry configuration. UNRESOLVED_TOKEN_VAL(PS_TelemetryDataStatement)
  
```
Remove-CsTelemetryConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

This example removes the telemetry configuration for the Redmond site.
  
```
Remove-CsTelemetryConfiguration -Identity Site:Redmond
```

### Example 2

This example uses the **Get-CsTelemetryConfiguration** cmdlet in combination with the _Filter_ parameter to select the telemetry configurations that are configured at the site level and then pipelines them to the **Remove-CsTelemetryConfiguration** cmdlet for removal. The result is that all "Site" scoped telemetry configurations are removed.
  
```
Get-CsTelemetryConfiguration -Filter "Site:*" | Remove-CsTelemetryConfiguration
```

## Detailed Description
<a name="DetailedDescription"> </a>

> [!NOTE]
> For privacy information, see the [Skype for Business Privacy Statement](http://go.microsoft.com/fwlink/?LinkID=517480&amp;clcid=0x409). 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |A unique identifier that includes the scope of the telemetry configuration. Telemetry configurations can be scoped at the Global, Site, or Service level. For example, "site:Redmond" (for site). The format of the service scope is "Service:\<Identity\>", where identity is derived from the topology. You can use the following commandss to identify the relevant services.  <br/> ```Get-CsService -WebServer | fl IdentityGet-CsService -PoolFqdn <pool> | fl Identity```The first command will give you all of the WebServices in the topology, regardless of the pool. The second will give you all of the services on the pool, regardless of their role. You can combine the two commands to zero in on a single role in a single pool.  <br/> > [!NOTE]> The Global configuration can't be deleted. Specifying the Global configuration will return it to the default Global settings.           |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

This cmdlet takes pipeline input of the **Get-CsTelemetryConfiguration** cmdlet as shown in Example 2.
  
## Return Types
<a name="ReturnTypes"> </a>

None.
  

