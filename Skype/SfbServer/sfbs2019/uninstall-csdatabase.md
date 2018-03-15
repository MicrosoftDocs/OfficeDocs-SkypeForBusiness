---
title: "Uninstall-CsDatabase"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: bd08ac1c-cfcd-4cf8-b082-7d2e83a2837e
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Uninstall-CsDatabase
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Deletes the specified Lync Server database. This cmdlet was introduced in Lync Server 2010.
  
```
Uninstall-CsDatabase -DatabaseType <Application | Archiving | Monitoring | User | Provision | CentralAdmin | Lyss | Registrar | Edge | PersistentChat | PersistentChatCompliance | CentralMgmt> [-SqlInstanceName <String>] [-SqlServerFqdn <Fqdn>] <COMMON PARAMETERS>
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

The command shown in Example 1 deletes the Central Management store from the computer atl-sql-001.litwareinc.com.
  
```
Uninstall-CsDatabase -CentralManagementDatabase -SqlServerFqdn atl-sql-001.litwareinc.com 
```

### EXAMPLE 2

In Example 2, the User database is deleted from the computer atl-sql-001.litwareinc.com. When you use the DatabaseType parameter, all stores related to the specified database are deleted.
  
```
Uninstall-CsDatabase -DatabaseType User -SqlServerFqdn atl-sql-001.litwareinc.com 
```

## Detailed Description
<a name="sectionSection1"> </a>

Lync Server makes extensive use of SQL Server databases such as the Central Management store and the Archiving database. These databases are set up at the same time you install Lync Server or at the same time you install a Lync Server role that requires a database back end. After the databases have been installed, you will rarely need to uninstall them.
  
However, it is possible that you might need to uninstall a Lync Server database at some point; for example, a hardware failure or an issue with network connectivity might make an existing database unusable. Regardless of the reason, the **Uninstall-CsDatabase** cmdlet provides a way for you to remove or detach any of the SQL Server databases used by Lync Server. 
  
Who can run this cmdlet: You must be a member of the domain, a SQL Server administrator, and a local administrator on the computer where SQL Server is installed in order to run the **Uninstall-CsDatabase** cmdlet locally. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Uninstall-CsDatabase"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _CentralManagementDatabase_ <br/> |Required  <br/> |System.Management.Automation.SwitchParameter  <br/> |If present, uninstalls the Central Management store. You cannot use both CentralManagementDatabase and DatabaseType in the same command.  <br/> |
| _DatabaseType_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deployment.DatabaseNameType  <br/> |Database to be deleted. Valid values are:  <br/> Application  <br/> Archiving  <br/> CentralAdmin  <br/> CentralMgmt  <br/> Edge  <br/> Lyss  <br/> Monitoring  <br/> PersistentChat  <br/> PersistentChatCompliance  <br/> Provision  <br/> Registrar  <br/> User  <br/> To delete the Central Management store, use the CentralManagementDatabase parameter.  <br/> |
| _SqlServerFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of the computer or SQL Server cluster where the database is located. For example: -SqlServer atl-sql-001.litwareinc.com.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Detach_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If present, detaches the specified database. When a database is detached, all the file locks imposed by SQL Server are removed. This enables you to directly access the database files in order to do such things as copy those files to another computer.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If present, forces removal of the database even if that database is currently in use.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\Logs\UninstallDatabase.html"  <br/> |
| _SqlInstanceName_ <br/> |Optional  <br/> |System.String  <br/> |Name of the database instance containing the database to be removed. A database instance is a set of running processes that provides access to database files.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

None. The **Uninstall-CsDatabase** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Uninstall-CsDatabase** cmdlet does not return any values or objects. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Install-CsDatabase](install-csdatabase.md)

