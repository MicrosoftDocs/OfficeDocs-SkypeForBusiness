---
title: "Invoke-CsManagementServerFailover"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 060ab02a-1267-4b35-bc2b-6a4a35616be0
description: "Invokes the process by which the Skype for Business Server 2015 Central Management Store (CMS) is failed over to another pool. When the Central Management store is failed over the primary database will be replaced by either a preassigned database or a specified backup database. To run this cmdlet, you need to use an account that is a member of the RTCUniversalServerAdmins group. This cmdlet should be run on a server in the pool to which you want to failerover the CMS. This cmdlet was introduced in Lync Server 2013."
---

# Invoke-CsManagementServerFailover
 
Invokes the process by which the Skype for Business Server 2015 Central Management Store (CMS) is failed over to another pool. When the Central Management store is failed over the primary database will be replaced by either a preassigned database or a specified backup database. To run this cmdlet, you need to use an account that is a member of the RTCUniversalServerAdmins group. This cmdlet should be run on a server in the pool to which you want to failerover the CMS. This cmdlet was introduced in Lync Server 2013.
  
```
Invoke-CsManagementServerFailover [-Restore <SwitchParameter>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 fails over the Central Management store for Skype for Business Server 2015. In this case, the existing management store will be replaced by the preassigned database specified in the topology.
  
```
Invoke-CsManagementServerFailover 
```

### Example 2

The command shown in Example 2 fails over the Central Management store for Skype for Business Server 2015. In this case, the existing management store will be replaced by the RTC database instance found on the computer redmond-cs-001.litwareinc.com.
  
```
Invoke-CsManagementServerFailover -BackupSqlServerFqdn "redmond-cs-001.litwareinc.com" - BackupSqlInstanceName "RTC" -Force
```

## Detailed Description
<a name="DetailedDescription"> </a>

The **Invoke-CsManagementServerFailover** cmdlet enables administrators to "failover" the Central Management Server (CMS). You can only invoke the failover to the database defined in the Topology Builder. The **Invoke-CsManagementServerFailover** cmdlet provides two methods for failing over the CMS:
  
- Failover when the CMS is available by running the cmdlet without any target database parameters as in Example 1.
    
- Failover when the CMS is unavailable (in disaster recovery mode) by specifying the  _BackupSqlServerFqdn_ parameter and the corresponding _BackupSqlInstanceName_ parameter as in Example 2. If the database defined in the Topology Builder is mirrored, add the _BackupMirrorSqlServerFqdn_ and _BackupMirrorSqlInstanceName_ parameters.
    
 **Skype for Business Server Control Panel:** The functions carried out by the **Invoke-CsManagementServerFailover** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _BackupSqlServerFqdn_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the computer hosting the SQL Server backup database. This parameter is required if you are running the **Invoke-CsManagementServerFailover** cmdlet in disaster recovery mode. <br/> |
| _Force_ <br/> |Required  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command. This parameter is required if you are running the **Invoke-CsManagementServerFailover** cmdlet in disaster recovery mode. <br/> You should not use the Force parameter if you are running the cmdlet for purposes other than disaster recovery, as it will not account for replication during the failover. When the parameter is not used, the cmdlet will first make sure all replications are done, then set the source DB to read-only mode.  <br/> |
| _BackupMirrorSqlInstanceName_ <br/> |Optional  <br/> |System.String  <br/> |SQL Server instance for the mirror database.  <br/> |
| _BackupMirrorSqlServerFqdn_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name of the computer hosting the SQL Server mirror database.  <br/> |
| _BackupSqlInstanceName_ <br/> |Optional  <br/> |System.String  <br/> |SQL Server instance for the backup database.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  `-Report "C:\Logs\CMSFailover.html"` <br/> |
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

