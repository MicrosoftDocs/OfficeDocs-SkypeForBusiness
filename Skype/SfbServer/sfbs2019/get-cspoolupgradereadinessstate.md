---
title: "Get-CsPoolUpgradeReadinessState"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 127c718e-8949-4bcd-b954-5182b8730820
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Get-CsPoolUpgradeReadinessState
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Returns information indicating whether or not your Skype for Business Online Registrar pools are ready to be upgraded. The upgrade readiness state for a pool is based on the upgrade domains that have been configured for that pool. This cmdlet was introduced in Lync Server 2013.
  
```
Get-CsPoolUpgradeReadinessState [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns the upgrade readiness state for the local Registrar pool. Note that this command must be executed on a Front End server located within the pool.
  
```
Get-CsPoolUpgradeReadinessState
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Get-CsPoolUpgradeReadinessState** cmdlet returns information about the upgrade readiness for a Lync Server 2013 pool. The returned information includes the number of Front End servers assigned to the pool; the number of currently active Front End servers; the name of the upgrade domain; and a True/False value that indicates whether the current state of the pool allows it to be upgraded. Note that this cmdlet must be run locally on a Front End server in the pool being checked. There are no options enabling you to run the **Get-CsPoolUpgradeReadinessState** cmdlet remotely. 
  
 **Lync Server Control Panel:** The functions carried out by the **Get-CsPoolUpgradeReadinessState** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsPoolUpgradeReadinessState** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsPoolUpgradeReadinessState** cmdlet returns an instance of the Microsoft.Rtc.Management.Hadr.PoolUpgradeState object. 
  

