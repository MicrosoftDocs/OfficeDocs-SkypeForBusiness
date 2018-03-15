---
title: "Invoke-CsManagementServerFailover"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 060ab02a-1267-4b35-bc2b-6a4a35616be0
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Invoke-CsManagementServerFailover
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Invokes the process by which the Lync Server 2013 Central Management store is failed over. When the Central Management store is failed over the primary database will be replaced by either a pre-assigned mirror database or a specified backup database. This cmdlet was introduced in Lync Server 2013.
  
```
Invoke-CsManagementServerFailover -BackupSqlServerFqdn <Fqdn> -Force <SwitchParameter> [-BackupMirrorSqlInstanceName <String>] [-BackupMirrorSqlServerFqdn <Fqdn>] [-BackupSqlInstanceName <String>] <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 fails over the Central Management store for Lync Server 2013. In this case, the existing management store will be replaced by the RTC database instance found on the computer redmond-cs-001.litwareinc.com.
  
```
Invoke-CsManagementServerFailover -BackupSqlServerFqdn "redmond-cs-001.litwareinc.com" - BackupSqlInstanceName "RTC" -Force
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Invoke-CsManagementServerFailover** cmdlet enables administrators to "failover" the Central Managament Server (CMS). The **Invoke-CsManagementServerFailover** cmdlet provides two different methods for failing over the CMS: 1) you can failover to a specified backup instance of SQL Server, or, 2) you can failover to a preassigned mirror database. To failover to a specified backup instance, use the BackupSqlServerFqdn and BackupSqlInstanceName parameters. To failover to the mirror database, use the BackupMirrorSqlServerFqdn and BackupMirrorSqlInstanceName parameters. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Invoke-CsManagementServerFailover"}
  
 **Lync Server Control Panel:** The functions carried out by the **Invoke-CsManagementServerFailover** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _BackupSqlServerFqdn_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the computer hosting the SQL Server backup database. This parameter is required if you are running the **Invoke-CsManagementServerFailover** cmdlet in disaster recovery mode.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command. This parameter is required if you are running the **Invoke-CsManagementServerFailover** cmdlet in disaster recovery mode.  <br/> |
| _BackupMirrorSqlInstanceName_ <br/> |Optional  <br/> |System.String  <br/> |SQL Server instance for the mirror database.  <br/> |
| _BackupMirrorSqlServerFqdn_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the computer hosting the SQL Server mirror database.  <br/> |
| _BackupSqlInstanceName_ <br/> |Optional  <br/> |System.String  <br/> |SQL Server instance for the backup database.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\Logs\CMSFailover.html"  <br/> |
| _Restore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, restores the existing Central Management Server database.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Invoke-CsManagementServerFailover** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

None.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Invoke-CsDatabaseFailover](invoke-csdatabasefailover.md)

