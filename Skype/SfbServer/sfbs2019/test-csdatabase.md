---
title: "Test-CsDatabase"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4165f1e1-fe64-45e7-a13f-f23c0205f386
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Test-CsDatabase
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Tests the configuration of the Lync Server 2013 databases. This cmdlet was introduced in Lync Server 2013.
  
```
Test-CsDatabase -LocalService <SwitchParameter> <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 verifies the configuration of the Central Management database.
  
```
Test-CsDatabase -CentralManagementDatabase
```

### Example 2

Example 2 verifies all the Lync Server databases installed on the computer atl-sql-001.litwareinc.com.
  
```
Test-CsDatabase -ConfiguredDatabases -SqlServerFqdn "atl-sql-001.litwareinc.com"
```

### Example 3

In Example 3, verification is performed only for the Archiving database installed on the computer atl-sql-001.litwareinc.com. Note that the SqlInstanceName parameter is included to specify the SQL Server instance (Archinst) where the Archiving database is located.
  
```
Test-CsDatabase -DatabaseType "Archiving" -SqlServerFqdn "atl-sql-001.litwareinc.com" -SqlInstanceName "archinst"
```

### Example 4

The command shown in Example 4 verifies the databases installed on the local computer.
  
```
Test-CsDatabase -LocalService
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Test-CsDatabase** cmdlet verifies connectivity to one or more Lync Server 2013 databases. When run, the **Test-CsDatabase** cmdlet reads the Lync Server topology, attempts to connect each of the relevant databases, and then reports back the success or failure of each attempt. If a connection can be made, the cmdlet will also report back such information as the database name, SQL Server version information, and the location of any installed mirror databases. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsDatabase"}
  
 **Lync Server Control Panel:** The functions carried out by the **Test-CsDatabase** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _CentralManagementDatabase_ <br/> |Required  <br/> |System.Management.Automation.SwitchParameter  <br/> |Tests the configuration of the Central Management database. This parameter cannot be used in conjunction with the ConfiguredDatabases parameter or the DatabaseType parameter.  <br/> |
| _ConfiguredDatabases_ <br/> |Required  <br/> |System.Management.Automation.SwitchParameter  <br/> |Tests the configuration of all the Lync Server databases installed on the specified computer. You must include the SqlServerFqdn parameter when using the ConfiguredDatabases parameter. In addition, this parameter cannot be used in the same command as the CentralManagementDatabase or the DatabaseType parameters.  <br/> |
| _DatabaseType_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deployment.DatabaseNameType  <br/> |Type of database to be validated. Allowed values are:  <br/> Valid values for DatabaseType are:  <br/> Application  <br/> Archiving  <br/> CentralAdmin  <br/> CentralMgmt  <br/> Edge  <br/> Lyss  <br/> Monitoring  <br/> PersistentChat  <br/> PersistentChatCompliance  <br/> Provision  <br/> Registrar  <br/> User  <br/> |
| _LocalService_ <br/> |Required  <br/> |System.Management.Automation.SwitchParameter  <br/> |Validates all the databases used by any of the Lync Server services that are installed on the local computer. This includes not only locally-installed databases but also databases installed on remote computers, provided those databases are used by one or more local services.  <br/> |
| _SqlServerFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the computer whether the databases to be validated are installed.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  <br/> -Report "C:\Logs\TestDatabases.html"  <br/> |
| _SqlInstanceName_ <br/> |Optional  <br/> |System.String  <br/> |SQL Server instance where the databases to be validated are installed. For example:  <br/> -SqlInstanceName "rtc"  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Test-CsDatabase** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

The **Test-CsDatabase** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsDatabaseMirrorState](get-csdatabasemirrorstate.md)
  
[Get-CsService](get-csservice.md)
  
[Get-CsUserDatabaseState](get-csuserdatabasestate.md)

