---
title: "Invoke-CsDatabaseFailover"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 24b73e8e-948c-4e9c-bf4e-04ec0a229ffa
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Invoke-CsDatabaseFailover
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Invokes the process in which a Lync Server 2013 database fails over to its mirror database. After failover has been completed, the mirror database will become the principal database and will handle all new database requests. This cmdlet was introduced in Lync Server 2013.
  
```
Invoke-CsDatabaseFailover -DatabaseType <Application | Archiving | Monitoring | User | Provision | CentralAdmin | Lyss | Registrar | Edge | PersistentChat | PersistentChatCompliance | CentralMgmt> -NewPrincipal <Primary | Mirror> -PoolFqdn <Fqdn> [-Confirm [<SwitchParameter>]] [-ExcludeDatabaseList <String[]>] [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 invokes failover for the User database found on the pool atl-cs-001.litwareinc.com. The command causes the User database to failover to a previously-assigned mirror database.
  
```
Invoke-CsDatabaseFailover -PoolFqdn atl-cs-001.litwareinc.com -DatabaseType "User" -NewPrincipal "Mirror"
```

### Example 2

In Example 2, all databases on the pool atl-cs-001.litwareinc.com are failed over except for the LcsCDR and LcsLog databases. These databases are exempted from failover by using the ExcludeDatabaseList parameter.
  
```
Invoke-CsDatabaseFailover -PoolFqdn atl-cs-001.litwareinc.com -ExcludeDatabase -NewPrincipal "Mirror" -ExcludeDatabaseList "LcsCDR", "LcsLog"
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Invoke-CsDatabaseFailover** cmdlet provides a way for administrators to "failover" one or more Lync Server 2013 databases. For example, suppose you need to temporarily take down the primary database, perhaps to perform a hardware upgrade. In that case, you can use the **Invoke-CsDatabaseFailover** cmdlet to failover from the primary database to the mirror database; when you do that, all requests for the database in question will be routed to the mirror database. Later, when the hardware upgrade is complete, you can use this same cmdlet to failback to the primary database. 
  
Note that any commands using the **Invoke-CsDatabaseFailover** cmdlet will fail if you have not configured both a primary database and a mirror database for the database in question. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Invoke-CsDatabaseFailover"}
  
 **Lync Server Control Panel:** The functions carried out by the **Invoke-CsDatabaseFailover** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _DatabaseType_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deployment.DatabaseNameType  <br/> |Type of database being failed over. Valid values are:  <br/> Application  <br/> Archiving  <br/> CentralAdmin  <br/> CentralMgmt  <br/> Cls  <br/> Edge  <br/> Lyss  <br/> Monitoring  <br/> PersistentChat  <br/> PersistentChatCompliance  <br/> Provision  <br/> Registrar  <br/> User  <br/> |
| _NewPrincipal_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deployment.MirrorRole  <br/> |Specifies whether failover will be to the primary database or to the mirror database. Valid values are:  <br/> \* \* Mirror  <br/> Primary  <br/> |
| _PoolFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the pool containing the database to be failed over.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _ExcludeDatabaseList_ <br/> |Optional  <br/> |System.String[]  <br/> |List of databases that should not be failed over. For example:  <br/> -ExcludeDatabaseList "LcsCDR"  <br/> To prevent multiple databases from being failed over, separate the database names using commas:  <br/> -ExcludeDatabaseList "LcsCDR", "LcsLog"  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command. The Force parameter is also used if the current database is not accessible.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves topology information from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report "C:\Logs\DatabaseFailover.html"  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **Invoke-CsDatabaseFailover** cmdlet does not accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

None.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsDatabaseMirrorState](get-csdatabasemirrorstate.md)
  
[Install-CsMirrorDatabase](install-csmirrordatabase.md)

