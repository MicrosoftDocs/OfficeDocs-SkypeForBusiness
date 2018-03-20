---
title: "Repair-CsInterPoolConfDataRecovery"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 4/27/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 590bb9c6-9d03-4516-9335-8965c843d871
description: "Use the Repair-CsInterPoolConfDataRecovery cmdlet to repair conference data in the target pool of a partial fail-over. The cmdlet compares conference data between the failed-over pool and the target pool and synchronizes the discrepancies."
---

# Repair-CsInterPoolConfDataRecovery
 
Use the **Repair-CsInterPoolConfDataRecovery** cmdlet to repair conference data in the target pool of a partial fail-over. The cmdlet compares conference data between the failed-over pool and the target pool and synchronizes the discrepancies.
  
```
Repair-CsInterPoolConfDataRecovery -PoolFqdn <Fqdn> [-Confirm [<SwitchParameter>]] [-NumberOfDaysToRecoverChanges <Int32>] [-RecoverConferencesData <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

This example will return a summary of the inconsistencies in conference data between the fail-over target pool, MainPool.Contoso.com, and its failed-over counterpart.
  
```
Repair-CsInterpoolConfDataRecovery -PoolFqdn MainPool.Contoso.com
```

### Example 2

This example uses the  _RecoverConferencesData_ switch to enable the repair of the missing conference data in the fail-over target pool.
  
```
Repair-CsInterpoolConfDataRecovery -PoolFqdn MainPool.Contoso.com -RecoverConferencesData
```

### Example 3

This example will repair the conference data that was created or updated 10 days ago.
  
```
Repair-CsInterpoolConfDataRecovery -PoolFqdn MainPool.Contoso.com -NumberOfDaysToRecoverChanges 10 -RecoverConferencesData
```

## Detailed Description
<a name="DetailedDescription"> </a>

The use of this cmdlet can be required when a pool is failed-over, but is shut down before all the conference data is migrated.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _PoolFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the fail-over target pool in which to repair the conference data. For example:  <br/>  `-PoolFqdn "MainPool.Contoso.com"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _NumberOfDaysToRecoverChanges_ <br/> |Optional  <br/> |System.Int32  <br/> |Specifies the number of days for which conference recovery data will be repaired. If not specified, the cmdlet will review and repair all the available data.  <br/> |
| _RecoverConferencesData_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, the  _RecoverConferencesData_ switch causes the cmdlet to perform the data repairs. If not specified, the cmdlet will return a summary of the discrepancies found in the conference data without making any repairs. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None
  

