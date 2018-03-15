---
title: "Get-CsPoolFabricState"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9fe6cce5-4142-47b3-94ac-4cb8b94ec215
description: "Returns the Windows Fabric state for a Skype for Business Server 2015 pool. Windows Fabric is a Microsoft technology used for creating highly reliable, distributable, and scalable applications. This cmdlet was introduced in Lync Server 2013."
---

# Get-CsPoolFabricState
 
Returns the Windows Fabric state for a Skype for Business Server 2015 pool. Windows Fabric is a Microsoft technology used for creating highly reliable, distributable, and scalable applications. This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsPoolFabricState -RoutingGroup <String> <COMMON PARAMETERS>

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

The **Get-CsPoolFabricState** cmdlet returns the Windows Fabric state for a Skype for Business Server 2015 pool. This includes information about Windows Fabric replica instances for any (or all) of the following services: MCU factory; Conference Directory; Routing; Skype for Business Server 2015 Storage Service.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Get-CsPoolFabricState** cmdlet are not available in Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _PoolFqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name of the pool being checked. You must supply the FQDN of a pool when calling this cmdlet; for example:  <br/>  `-PoolFqdn "atl-cs-001.litwareinc.com"` <br/> |
| _RoutingGroup_ <br/> |Required  <br/> |System.String  <br/> |Globally unique identifier (GUID) of the Windows Fabric routing group to be returned. Routing groups are used to specify the servers that users log onto.  <br/> |
| _Tenant_ <br/> |Required  <br/> |System.Guid  <br/> |Globally unique identifier (GUID) of the Skype for Business Online tenant account whose Windows Fabric pool state is being returned. For example:  <br/>  `-Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"` <br/> You can return the tenant ID for each of your Skype for Business Online tenants by running this command:  <br/>  `Get-CsTenant | Select-Object DisplayName, TenantID` <br/> |
| _UserUri_ <br/> |Required  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |Enables you to check the Windows fabric state for the pool used by a specific user. For example, to check the Windows fabric state for the user Ken Myer use this syntax:  <br/>  `-UserUri "sip:kenmyer@litwareinc.com"` <br/> Note that you can only specify one user URI per command.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _HealthState_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _OutputCsvFile_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _ServiceName_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _ShowAll_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |PARAMVALUE: SwitchParameter  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _ReplicaBuildProgress_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |PARAMVALUE: SwitchParameter  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsPoolFabricState** cmdlet does not support pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

String value representing the fabric state. The **Get-CsPoolFabricState** cmdlet does not return objects.
  

