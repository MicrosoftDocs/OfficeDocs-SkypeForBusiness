---
title: "Set-CsTelemetryConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 69ef190e-427e-4583-9efc-bfac64e062ca

description: "Use the Set-CsTelemetryConfiguration cmdlet to change the settings on existing telemetry configurations. UNRESOLVED_TOKEN_VAL(PS_TelemetryDataStatement)"
---

# Set-CsTelemetryConfiguration
 
Use the **Set-CsTelemetryConfiguration** cmdlet to change the settings on existing telemetry configurations. UNRESOLVED_TOKEN_VAL(PS_TelemetryDataStatement)
  
```
Set-CsTelemetryConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

This example enables client telemetry on the configuration scoped to the Redmond site.
  
```
Set-CsTelemetryConfiguration -Identity site:Redmond -EnableClientTelemetry $True
```

## Detailed Description
<a name="DetailedDescription"> </a>

> [!NOTE]
> For privacy information, see the [Skype for Business Privacy Statement](http://go.microsoft.com/fwlink/?LinkID=517480&amp;clcid=0x409). 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableClientTelemetry_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to true, client telemetry will be enabled. The default is false.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |A unique identifier that includes the scope of the telemetry configuration. Telemetry configurations can be scoped at the Global, Site, or Service level. For example, "site:Redmond" (for site). The format of the service scope is "Service:\<Identity\>", where identity is derived from the topology. You can use the following commands to identify the relevant services.  <br/> ```Get-CsService -WebServer | fl IdentityGet-CsService -PoolFqdn <pool> | fl Identity```The first command will give you all of the WebServices in the topology, regardless of the pool. The second will give you all of the services on the pool, regardless of their role. You can combine the two commands to zero in on a single role in a single pool.  <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

This cmdlet takes pipeline input of the **Get-CsTelemetryConfiguration** cmdlet.
  
## Return Types
<a name="ReturnTypes"> </a>

None
  

