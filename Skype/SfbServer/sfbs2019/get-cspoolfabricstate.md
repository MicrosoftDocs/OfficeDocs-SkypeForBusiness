---
title: "Get-CsPoolFabricState"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9fe6cce5-4142-47b3-94ac-4cb8b94ec215
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsPoolFabricState
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Returns the Windows Fabric state for a Lync Server 2013 pool. Windows Fabric is a Microsoft technology used for creating highly reliable, distributable, and scalable applications. This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsPoolFabricState -PoolFqdn <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Type <All | MCUFactory | ConferenceDirectory | Routing | LYSS>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns the fabric state for the pool atl-cs-001.litwareinc.com. Because the Type parameter was not included, state information for all the services on the pool will be returned.
  
```
Get-CsPoolFabricState -PoolFqdn "atl-cs-001.litwareinc.com"
```

### Example 2

Example 2 returns the fabric state for a single service on the pool atl-cs-001.litwareinc.com: the MCU factory service. This is done by including the Type parameter and the parameter value "MCU".
  
```
Get-CsPoolFabricState -PoolFqdn "atl-cs-001.litwareinc.com" -Type MCU
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Get-CsPoolFabricState** cmdlet returns the Windows Fabric state for a Lync Server 2013 pool. This includes information about Windows Fabric replica instances for any (or all) of the following services: MCU factory; Conference Directory; Routing; Lync Server Storage Service. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsPoolFabricState"}
  
 **Lync Server Control Panel:** The functions carried out by the **Get-CsPoolFabricState** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _PoolFqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name of the pool being checked. You must supply the FQDN of a pool when calling this cmdlet; for example:  <br/> -PoolFqdn "atl-cs-001.litwareinc.com"  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Type_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.HADR.GetOcsPoolFabricStateCmdlet+FabricEnumerationType  <br/> |Specifies the service type to be returned. Allowed values are:  <br/> \* All (returns information for all services)  <br/> \* MCUFactory (returns information for the MCU factory service)  <br/> \* ConferenceDirectory (returns information for the Conference Directory service)  <br/> LYSS (returns information for the Lync Server Storage service)  <br/> You can only specify a single type per command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsPoolFabricState** cmdlet does not support pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

String value representing the fabric state. The **Get-CsPoolFabricState** cmdlet does not return objects. 
  

