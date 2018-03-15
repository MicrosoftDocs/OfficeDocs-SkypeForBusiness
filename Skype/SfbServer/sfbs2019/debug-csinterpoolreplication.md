---
title: "Debug-CsInterPoolReplication"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 945bfd1c-1759-4869-9316-b3260fcc633d
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Debug-CsInterPoolReplication
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Verifies that replication is working between a Registrar pool and its assigned backup pool. This cmdlet was introduced in Lync Server 2013.
  
```
Debug-CsInterPoolReplication -PoolFqdn <Fqdn> [-BackupModule <All | CentralMgmt | PresenceFocus | DataConf>] [-Force <SwitchParameter>]

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

In Lync Server 2013 each Registrar pool can be associated with a backup pool. The backup pool maintains a copy of all the data stored on the primary pool. Should the primary pool become unavailable then users of that pool can automatically be "failed over" to the backup pool. This enables those users to continue to use Lync Server even though their home pool is not available. The Debug-CsInterPoolReplication cmdlet is used to compare the data stores on a primary pool and its backup pool, and thus verify that replication between the two pools is working as expected.
  
Note that this command will fail if the pool being tested has not been assigned a backup pool.
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Debug-CsInterPoolReplication"}
  
 **Lync Server Control Panel:** The functions carried out by the Debug-CsInterPoolReplication cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _PoolFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the primary pool being tested. For example:  <br/> -PoolFqdn "atl-cs-001.litwareinc.com"  <br/> |
| _BackupModule_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Hadr.BackupService.BackupModules  <br/> |Enables administrators to specify the data store to be verified. Allowed values are:  <br/> \* All  <br/> \* CentralMgmt  <br/> \* PresenceFocus  <br/> \* DataConf  <br/> The default value is All.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. Debug-CsInterPoolReplication does not accept pipelined data.
  
## Return Types
<a name="ReturnTypes"> </a>

String value.
  

