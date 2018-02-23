---
title: "Debug-CsInterPoolReplication"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 945bfd1c-1759-4869-9316-b3260fcc633d
description: "Verifies that replication is working between a Registrar pool and its assigned backup pool. This cmdlet was introduced in Lync Server 2013."
---

# Debug-CsInterPoolReplication
[]
Verifies that replication is working between a Registrar pool and its assigned backup pool. This cmdlet was introduced in Lync Server 2013.
  
```
Debug-CsInterPoolReplication -PoolFqdn <Fqdn> [-BackupModule <All | CentralMgmt | PresenceFocus | DataConf>] [-Confirm [<SwitchParameter>]] [-DatabaseCommandTimeoutInSeconds <Int32>] [-Force <SwitchParameter>] [-ResyncSignatureMismatchItems <SwitchParameter>] [-SuppressMultiMasterDetection <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 verifies the full replication status between the pool atl-cs-001.litwareinc.com and its previously-assigned backup pool.
  
```
Debug-CsInterPoolReplication -PoolFqdn "atl-cs-001.litwareinc.com"
```

### Example 2

In Example 2, only the replication of data conferencing data is verified between the pool atl-cs-001.litwareinc.com and its previously-assigned backup pool.
  
```
Debug-CsInterPoolReplication -PoolFqdn "atl-cs-001.litwareinc.com" -BackupModule DataConf
```

## Detailed Description
<a name="DetailedDescription"> </a>

In Skype for Business Server 2015 each Registrar pool can be associated with a backup pool. The backup pool maintains a copy of all the data stored on the primary pool. Should the primary pool become unavailable then users of that pool can automatically be "failed over" to the backup pool. This enables those users to continue to use Skype for Business Server 2015 even though their home pool is not available. The Debug-CsInterPoolReplication cmdlet is used to compare the data stores on a primary pool and its backup pool, and thus verify that replication between the two pools is working as expected.
  
Note that this command will fail if the pool being tested has not been assigned a backup pool.
  
 **Skype for Business Server Control Panel:** The functions carried out by the Debug-CsInterPoolReplication cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _PoolFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the primary pool being tested. For example:  <br/>  `-PoolFqdn "atl-cs-001.litwareinc.com"` <br/> |
| _BackupModule_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Hadr.InterPoolReplication.BackupModules  <br/> |Enables administrators to specify the data store to be verified. Allowed values are:  <br/> All  <br/> CentralMgmt  <br/> PresenceFocus  <br/> DataConf  <br/> The default value is All.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DatabaseCommandTimeoutInSeconds_ <br/> |Optional  <br/> |System.Int32  <br/> |PARAMVALUE: Int32  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _ResyncSignatureMismatchItems_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |PARAMVALUE: SwitchParameter  <br/> |
| _SuppressMultiMasterDetection_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When included in the command, Debug-CsInterPoolReplication will not verify whether or not the pool is part of a multi-master replication configuration before beginning its verification checks.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. Debug-CsInterPoolReplication does not accept pipelined data.
  
## Return Types
<a name="ReturnTypes"> </a>

String value.
  

