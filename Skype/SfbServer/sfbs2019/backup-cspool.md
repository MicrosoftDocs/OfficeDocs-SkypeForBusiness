---
title: "Backup-CsPool"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 66ec46de-e1e7-4e33-961d-7ef785059c48
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Backup-CsPool
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Creates a backup copy of the specified Lync Server 2013 pool. This cmdlet was introduced in Lync Server 2013.
  
```
Backup-CsPool -PoolFqdn <Fqdn> [-Category <UserData | CMS>] [-Confirm [<SwitchParameter>]] [-FailedOverPoolOnly <SwitchParameter>] [-Force <SwitchParameter>] [-FullBackup <SwitchParameter>] [-LocalStore <SwitchParameter>] [-Report <String>] [-RetryCount <Int32>] [-SteadyState <SwitchParameter>] [-WaitTime <TimeSpan>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 backs up the pool atl-cs-001.litwareinc.com.
  
```
Backup-CsPool -PoolFqdn "atl-cs-001.litwareinc.com"
```

### Example 2

In Example 2, a "steady state" backup is done for the pool atl-cs-001.litwareinc.com.
  
```
Backup-CsPool -PoolFqdn "atl-cs-001.litwareinc.com" -SteadyState
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Backup-CsPool** cmdlet enables administrators to copy user data and conference data for a Registrar pool to a specified backup pool. If the primary pool should fail or otherwise become unavailable, users homed on that primary pool can then be "failed over" to the backup pool. Those users can then log on to Lync Server via the backup pool, and continue to use that pool until their home pool has been restored. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Backup-CsPool"}
  
 **Lync Server Control Panel**: The functions carried out by the **Backup-CsPool** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _PoolFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the pool being backed up. For example:  <br/> -SourcePoolFqdn "atl-cs-001.litwareinc.com"  <br/> |
| _Category_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Hadr.BackupService.BackupCategory  <br/> |Enables you to select the Lync Server modules that will be backed up; if this parameter is not present then all the modules will be backed up. Allowed values are:  <br/> \* CMS  <br/> \* UserData  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _FailedOverPoolOnly_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, backup will take place only if the pool is in a failed over state. If you use this parameter then you must also use the FullBackup parameter.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _FullBackup_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, backup will not begin until the backup service has reached its final state. You cannot use both the FullBackup parameter and the SteadyState parameter in the same command.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the topology information from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |File path for the log file created when the cmdlet runs. For example:  <br/> -Report "C:\Logs\BackupPool.html"  <br/> If this file already exists, it will be overwritten when you run the cmdlet.  <br/> By default, reports are written to the AppData\Local\Temp folder in your user profile.  <br/> |
| _RetryCount_ <br/> |Optional  <br/> |System.Int32  <br/> |Maximum number of times Backup-CsPool will try to call the backup service before failing.  <br/> |
| _SteadyState_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, backup will not begin until the backup service has reached a steady state. A "steady state" occurs when the pool switches to read-only or failover/failback mode, and no longer produces any new data that needs to be backed up.  <br/> |
| _WaitTime_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |Amount of time (in seconds) that the cmdlet will wait before checking to see if the backup service is in either the full state or the steady state.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Backup-CsPool** cmdlet does not accept pipelined data. 
  
## Return Types
<a name="ReturnTypes"> </a>

None.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsBackupServiceConfiguration](get-csbackupserviceconfiguration.md)
  
[Get-CsBackupServiceStatus](get-csbackupservicestatus.md)
  
[Get-CsPoolBackupRelationship](get-cspoolbackuprelationship.md)

