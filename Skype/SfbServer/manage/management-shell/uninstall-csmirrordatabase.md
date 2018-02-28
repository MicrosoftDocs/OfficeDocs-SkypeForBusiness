---
title: "Uninstall-CsMirrorDatabase"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a5b14259-6cf6-46b5-ae8d-3b5e4428dfaf
description: "Uninstalls a Skype for Business Server 2015 mirror database. A database mirror enables you to simultaneously maintain two copies of a database, each copy residing on a different server. This cmdlet was introduced in Lync Server 2013."
---

# Uninstall-CsMirrorDatabase
[]
Uninstalls a Skype for Business Server 2015 mirror database. A database mirror enables you to simultaneously maintain two copies of a database, each copy residing on a different server. This cmdlet was introduced in Lync Server 2013.
  
```
Uninstall-CsMirrorDatabase -DatabaseType <Application | Archiving | Monitoring | User | Provision | Lyss | Registrar | Edge | PersistentChat | PersistentChatCompliance | CentralMgmt | SigninTelemetry | ActiveMonitoring> -SqlServerFqdn <Fqdn> [-SqlInstanceName <String>] [-Confirm [<SwitchParameter>]] [-DropExistingDatabasesOnMirror <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 uninstalls the user database from the SQL Server instance RTC on the computer atl-mirror-001.litwareinc.com. Because the DropExistingDatabaseOnMirror parameter was included, the command will also delete the actual User database mirror.
  
```
Uninstall-CsMirrorDatabase -SqlServerFqdn "atl-mirror-001.litwareinc.com" -SqlInstanceName "RTC" -DatabaseType "User" -DropExistingDatabasesOnMirror
```

## Detailed Description
<a name="DetailedDescription"> </a>

Mirror databases enable you to simultaneously maintain two copies of a database: when data is written to Database A, a copy of that data is also written to its mirror database. This provides the ability to instantly replace Database A should that database become unavailable: you can "failover" to the mirror database with minimal disruption to your users and with minimal data loss. 
  
Mirror databases can be installed and configured by using the [Install-CsMirrorDatabase](install-csmirrordatabase.md) cmdlet. If you ever need to remove a mirror database, you can do so by using the **Uninstall-CsMirrorDatabase** cmdlet.
  
Skype for Business Server Control Panel: The functions carried out by the **Uninstall-CsMirrorDatabase** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _DatabaseType_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deployment.DatabaseNameType  <br/> |Type of mirror database to be installed. Allowed values are:  <br/> ActiveMonitoring  <br/> Application  <br/> Archiving  <br/> CentralMgmt  <br/> Edge  <br/> Lyss  <br/> Monitoring  <br/> PersistentChat  <br/> PersistentChatCompliance  <br/> Provision  <br/> Registrar  <br/> SigninTelemetry  <br/> User  <br/> |
| _SqlServerFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of the computer containing the database is to be uninstalled. For example:  <br/>  `-SqlServerFqdn atl-sql-001.litwareinc.com` <br/> This should be the FQDN of the primary SQL Server computer.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DropExistingDatabasesOnMirror_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, deletes any existing copies of the mirrored databases from the mirror server.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  <br/>  `-Report "C:\Logs\UnInstallDatabaseMirror.html"` <br/> |
| _SqlInstanceName_ <br/> |Optional  <br/> |System.String  <br/> |Name of the database instance where the database is to be installed. A database instance is simply a set of running processes that provides access to database files. If this parameter is omitted, the **Uninstall-CsMirrorDatabase** cmdlet will use the default SQL Server instance. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Uninstall-CsMirrorDatabase** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsDatabaseMirrorState](get-csdatabasemirrorstate.md)
  
[Install-CsMirrorDatabase](install-csmirrordatabase.md)

