---
title: "Install-CsMirrorDatabase"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6e3acdfb-39da-4aa4-b125-1ea542971da3
description: "Associates a mirror database with a Skype for Business Server 2015 database. A database mirror enables you to simultaneously maintain two copies of a database, each copy residing on a different server. This cmdlet was introduced in Lync Server 2013."
---

# Install-CsMirrorDatabase
 
Associates a mirror database with a Skype for Business Server 2015 database. A database mirror enables you to simultaneously maintain two copies of a database, each copy residing on a different server. This cmdlet was introduced in Lync Server 2013.
  
```
Install-CsMirrorDatabase -ConfiguredDatabases <SwitchParameter> -SqlServerFqdn <Fqdn> [-ForDefaultInstance <SwitchParameter>] [-ForInstance <String>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 installs any predefined database. The ConfiguredDatabases parameter causes the **Install-CsMirrorDatabase** cmdlet to use the current topology to determine which databases should be.
  
```
Install-CsMirrorDatabase -ConfiguredDatabases -FileShare "\\atl-fs-001\DbBackup" -SqlServerFqdn "atl-primary-001.litwareinc.com" -DropExisitingDatabasesOnMirror
```

## Detailed Description
<a name="DetailedDescription"> </a>

Mirror databases enable you to simultaneously maintain two copies of a database: when data is written to Database A, a copy of that data is also written to its mirror database. This provides the ability to instantly replace Database A should that database become unavailable: you can "failover" to the mirror database with minimal disruption to your users and with minimal data loss. After you have installed your primary databases you can then install and configure mirror databases by using the **Install-CsMirrorDatabase** cmdlet.
  
By default, the **Install-CsMirrorDatabase** cmdlet installs and configures mirror databases for all the Skype for Business Server 2015 databases housed on the specified server. However, you can use the DatabaseType or the ExcludeDatabaseList parameters to specify exactly which mirror databases should or should not be installed. DatabaseType enables you to specify only the databases that should be installed; ExcludeDatabaseList lets you specify the databases that should not be installed.
  
Skype for Business Server Control Panel: The functions carried out by the **Install-CsMirrorDatabase** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ConfiguredDatabases_ <br/> |Required  <br/> |System.Management.Automation.SwitchParameter  <br/> |Reads information from the Skype for Business Server 2015 topology, and installs the required mirror databases on the specified SQL Server computer or SQL Server cluster.  <br/> |
| _DatabaseType_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deployment.DatabaseNameType  <br/> |Type of mirror database to be installed. Allowed values are:  <br/> ActiveMonitoring  <br/> Application  <br/> Archiving  <br/> CentralMgmt  <br/> Edge  <br/> Lyss  <br/> Monitoring  <br/> PersistentChat  <br/> PersistentChatCompliance  <br/> Provision  <br/> Registrar  <br/> SigninTelemetry  <br/> User  <br/> |
| _FileShare_ <br/> |Required  <br/> |System.String  <br/> |UNC path to the database shared folder. The file share is used to export of databases from the primary SQL Server and import those databases onto the mirror.  <br/> The shared folder and its contents can be deleted after mirroring is established. The folder should also be deleted if you decide to disable mirroring.  <br/> |
| _SqlServerFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of the primary SQL Server computer. For example:  <br/>  `-SqlServerFqdn atl-sql-001.litwareinc.com` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DatabasePathMap_ <br/> |Optional  <br/> |System.Collections.Hashtable  <br/> |Enables you to specify custom folder paths for data files and log files; multiple paths should be separated by using a semicolon (;). For example:  <br/>  `-DatabasePathMap @{"Archiving:DbPath"="\\atl-sql-001.litwareinc.com\db";"Archiving:LogPath"="\\atl-sql-002.litwareinc.com\logs"}` <br/> |
| _DropExistingDatabasesOnMirror_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, deletes any existing copies of the mirrored databases from the server acting as the mirror before new data is copied to that server.  <br/> |
| _ExcludeDatabaseList_ <br/> |Optional  <br/> |System.String   <br/> |List of databases that should not be included in the mirror database; multiple databases can be specified by separating those databases using commas. For example:  <br/>  `-ExcludeDatabaseList "RTCCAB","RTCPROV"` <br/> |
| _ForDefaultInstance_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, instructs the **Install-CsMirrorDatabase** cmdlet to only act against the default SQL Server instance. You cannot use both ForDefaultInstance and ForInstance in the same command. <br/> |
| _ForInstance_ <br/> |Optional  <br/> |System.String  <br/> |When specified, instructs the **Install-CsMirrorDatabase** cmdlet to only act against the specified SQL Server instance. You cannot use both ForInstance and ForDefaultInstance in the same command. <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  <br/>  `-Report "C:\Logs\InstallDatabaseMirror.html"` <br/> |
| _SqlInstanceName_ <br/> |Optional  <br/> |System.String  <br/> |Name of the database instance where the database is to be installed. A database instance is simply a set of running processes that provides access to database files. If this parameter is omitted, the **Install-CsMirrorDatabase** cmdlet will use the default SQL Server instance. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Install-CsMirrorDatabase** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsDatabaseMirrorState](get-csdatabasemirrorstate.md)
  
[Uninstall-CsMirrorDatabase](uninstall-csmirrordatabase.md)

