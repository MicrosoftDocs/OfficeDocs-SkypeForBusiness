---
title: "Install-CsDatabase"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e91c1800-35f6-40ef-840d-7a518bddcae6
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Install-CsDatabase
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Installs one or more Lync Server databases. This cmdlet was introduced in Lync Server 2010.
  
```
Install-CsDatabase -LocalDatabases <SwitchParameter> [-ForDefaultInstance <SwitchParameter>] [-ForInstance <String>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

In Example 1, the **Install-CsDatabase** cmdlet reads in the Lync Server topology, and then installs any required databases on the pool atl-sql-001.litwareinc.com. 
  
```
Install-CsDatabase -ConfiguredDatabases -SqlServerFqdn atl-sql-001.litwareinc.com -DatabasePaths "E:\CSLog","F:\CSLog","G:\CSDB"
```

### EXAMPLE 2

The command shown in Example 2 installs the Central Management store on the pool atl-sql-001.litwareinc.com. The database will be installed in the rtc instance, and make use of the folder G:\CSDB.
  
```
Install-CsDatabase -CentralManagementDatabase -SqlServerFqdn atl-sql-001.litwareinc.com -SqlInstanceName rtc -DatabasePaths "G:\CSDB"
```

## Detailed Description
<a name="sectionSection1"> </a>

Lync Server makes extensive use of SQL Server databases, ranging from the Central Management store to the Archiving database. As a general rule, these databases are set up at the same time you install Lync Server or at the same time you install a Lync Server role (such as Monitoring Server) that requires a database back end. After installation has taken place these databases typically will not need to be reinstalled or moved to new locations.
  
On rare occasions, however, you might need to manually install a Lync Server database; this could be because you need to move a database to another server, or because a setup-related problem failed to install the database for you. The **Install-CsDatabase** cmdlet provides a way for you to install any of the SQL Server databases used by Lync Server. 
  
When running the **Install-CsDatabase** cmdlet there are basically three different ways to handle the configuration of the database being installed: 
  
Option 1 -- Run the cmdlet without including a parameter that specifies the database paths. When the **Install-CsDatabase** cmdlet is run without the DatabasePath or the UseDefaultSqlPath parameter the cmdlet uses a built-on algorithm to choose the storage location for the database logs and data files. Note that this built-in algorithm works with a stand-alone SQL Server, it will not work with a SQL Server cluster. To install a database on a SQL Server cluster your command must include either the DatabasePath or the UseDefaultSqlPath parameter 
  
Option 2 -- Run the cmdlet along with the DatabasePath parameter. When the **Install-CsDatabase** is cmdlet run with the DatabasePath parameter the built-in algorithm is not used to choose the storage location for the database logs and data files. Instead, administrators can select the location for these logs and data files. To install both data files and SQL Server logs in the same location, simply specify the path to the folder where this data should be stored. For example: 
  
-DatabasePath C:\SqlData
  
To store data files in one location and log files in a second location, specify the path to each folder, separating the two locations by using a comma (be careful not to put a blank space before or after the comma):
  
-DatabasePath C:\SqlLogs,D:\SqlData
  
The log files will always be stored on the first location specified, while data files will be stored in the second location.
  
In a pool backend, certain log files might be stored on a drive all by themselves. If you have a pool backend with a single drive, files will be distributed like this:
  
Drive 1 - Rtcdyn log; Rtc log; other logs; other data.
  
If you have two drives, files will be distributed like this:
  
Drive 1 - Rtcdyn log; Rtc log.
  
Drive 2 - Other logs; other data.
  
With three drives:
  
Drive 1 - Rtcdyn log.
  
Drive 2 - Rtc log.
  
Drive 3 - Other logs; other data.
  
And with four drives:
  
Drive 1 - Rtcdyn log.
  
Drive 2 - Rtc log.
  
Drive 3 - Other logs.
  
Drive 4 - Other data.
  
Option 3 -- Run the cmdlet along with the UseDefaultSqlPaths parameter. When the **Install-CsDatabase** cmdlet is run using the UseDefaultSqlPaths parameter, the built-in algorithm is not used to choose the storage locations for the database logs and data files. Instead, log and data files are stored in the locations specified by the SQL Server defaults path (these paths must be configured in advanced by a SQL Server administrator). Data files will be stored in the default SQL Server data file location while log files will be stored in the default SQL Server log file location. 
  
Before running the **Install-CsDatabase** cmdlet you should make sure that the RTCUniversalServerAdmins groups has not been assigned as the database owner. If that group is listed as the owner the group could possibly be deleted when you call the **Install-CsDatabase** cmdlet. 
  
Who can run this cmdlet: You must be a member of the domain, a member of the RTCUniversalReadOnlyAdmins group, a SQL Server administrator, and a local administrator on the computer where SQL Server is installed in order to run the **Install-CsDatabase** cmdlet locally. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Install-CsDatabase"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _CentralManagementDatabase_ <br/> |Required  <br/> |System.Management.Automation.SwitchParameter  <br/> |If this parameter is included, the **Install-CsDatabase** cmdlet will use the SqlServerFqdn parameter to install the Central Management store on the specified computer. This parameter is typically used only by Topology Builder, and is generally called just once, during initial setup.  <br/> |
| _ConfiguredDatabases_ <br/> |Required  <br/> |System.Management.Automation.SwitchParameter  <br/> |Reads information from the Lync Server topology, and installs the required databases on the specified SQL Server computer or SQL Server cluster. Administrators who need to call the **Install-CsDatabase** cmdlet will almost always use this parameter when specifying the databases to be installed.  <br/> |
| _DatabaseType_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deployment.DatabaseNameType  <br/> |Enables you to install a specific database on a specific SQL Server computer or SQL Server cluster. As a general rule, administrators should not run the **Install-CsDatabase** cmdlet with the DatabaseType parameter unless instructed otherwise by Microsoft support personnel. Instead, administrators should typically use the ConfiguredDatabases parameter. The DatabaseType parameter requires you to know the exact type and location for every database used in your topology, and is only required if the **Install-CsDatabase** cmdlet command fails to run using the ConfiguredDatabases parameter.  <br/> Valid values for DatabaseType are:  <br/> Application  <br/> Archiving  <br/> CentralAdmin  <br/> CentralMgmt  <br/> Edge  <br/> Lyss  <br/> Monitoring  <br/> PersistentChat  <br/> PersistentChatCompliance  <br/> Provision  <br/> Registrar  <br/> User  <br/> |
| _LocalDatabases_ <br/> |Required  <br/> |System.Management.Automation.SwitchParameter  <br/> |If this parameter is included, the **Install-CsDatabase** cmdlet will read in the Lync Server topology and install databases and stores as needed on the local computer.  <br/> |
| _SqlServerFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of the computer where the database is to be installed. For example: -SqlServerFqdn atl-sql-001.litwareinc.com.  <br/> |
| _Backup_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When used, backs up the existing Central Management server database to the specified SQL Server instance.  <br/> |
| _Clean_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If this parameter is included, the **Install-CsDatabase** cmdlet will delete and reinstall databases as needed. If this parameter is not included, the **Install-CsDatabase** cmdlet will not overwrite any existing databases. You cannot use both Clean and Update in the same command.  <br/> |
| _Collocated_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If present, additional database roles will be collocated with the Central Management store.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DatabasePathMap_ <br/> |Optional  <br/> |System.Collections.Hashtable  <br/> |Enables you to specify custom folder paths for data files and log files; multiple paths should be separated by using a semicolon (;). For example:  <br/> -DatabasePathMap @{"Archiving:DbPath"="\\atl-sql-001.litwareinc.com\db";"Archiving:LogPath"="\\atl-sql-002.litwareinc.com\logs"}  <br/> |
| _DatabasePaths_ <br/> |Optional  <br/> |System.String[]  <br/> |Specifies the drives and folders where data and log files can be stored; for example: -DatabasePaths "D:\Logs","E:\Data".  <br/> |
| _ExcludeCollocatedStores_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, suppresses a warning message telling you that any collocated database stores must be installed on the local computer.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, forces the installation of the new database even if an existing database of that type is currently in use.  <br/> |
| _ForDefaultInstance_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, instructs the **Install-CsDatabase** cmdlet to only act against the default SQL Server instance. You cannot use both ForDefaultInstance and ForInstance in the same command.  <br/> |
| _ForInstance_ <br/> |Optional  <br/> |System.String  <br/> |When specified, instructs the **Install-CsDatabase** cmdlet to only act against the specified SQL Server instance. You cannot use both ForInstance and ForDefaultInstance in the same command.  <br/> |
| _GlobalCatalog_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of a global catalog server in your domain. This parameter is not required if you are running the **Install-CsDatabase** cmdlet on a computer with an account in your domain.  <br/> |
| _GlobalSettingsDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of a domain controller where global settings are stored. If global settings are stored in the System container in Active Directory Domain Services, then this parameter must point to the root domain controller. If global settings are stored in the Configuration container, then any domain controller can be used and this parameter can be omitted.  <br/> |
| _NoReindex_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prevents the index files from being rebuilt when a database is being updated. This parameter can only be used along with the Update parameter.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\Logs\InstallDatabases.html"  <br/> |
| _SkipPrepareCheck_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, causes the **Install-CsDatabase** cmdlet to forego its initial preparation checks.  <br/> |
| _SqlInstanceName_ <br/> |Optional  <br/> |System.String  <br/> |Name of the database instance where the database is to be installed. A database instance is simply a set of running processes that provides access to database files. If this parameter is omitted, the **Install-CsDatabase** cmdlet will use the default SQL Server instance.  <br/> |
| _Update_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When present, updates the existing database. You cannot use Update and Clean in the same command.  <br/> Note that the Update parameter cannot be used against mirrored databases; the command will fail because the mirror databases cannot be dropped and recreated. To use the Update parameter with mirrored databases you must first use the [Uninstall-CsMirrorDatabase](uninstall-csmirrordatabase.md) cmdlet to disassociate the mirrored databases. At that point you can then run Install-CsDatabase and the Update parameter.  <br/> |
| _UseDefaultSqlPaths_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |When specified, instructs SQL Server to select the drive where data and log files will be stored.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Install-CsDatabase** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Install-CsDatabase** cmdlet does not return any values or objects. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Uninstall-CsDatabase](uninstall-csdatabase.md)

