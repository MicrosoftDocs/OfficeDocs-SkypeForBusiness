---
title: "Invoke-CsQoEDatabasePurge"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c4cae63a-b9dd-485b-8d53-2d81d353b7c3
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Invoke-CsQoEDatabasePurge
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Manually purges records from the Quality of Experience (QoE) database. This cmdlet was introduced in Lync Server 2013.
  
```
Invoke-CsQoEDatabasePurge -Identity <XdsIdentity> <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 purges all the QoE records more than 10 days old from the monitoring database on atl-sql-001.litwareinc.com.
  
```
Invoke-CsQoEDatabasePurge -Identity "service:MonitoringDatabase:atl-sql-001.litwareinc.com" -PurgeQoEDataOlderThanDays 10
```

### Example 2

The command shown in Example 2 is a variation of the command shown in Example 1; in this case, however, the Confirm parameter is added using this syntax:
  
-Confirm:$False
  
That syntax suppresses the confirmation prompts that would otherwise appear when purging QoE records.
  
```
Invoke-CsQoEDatabasePurge -Identity "service:MonitoringDatabase:atl-sql-001.litwareinc.com" -PurgeQoEDataOlderThanDays 10 -Confirm:$False
```

### Example 3

Example 3 purges all the QoE records more than 10 days old from all monitoring QoE databases in use in the organization. To do this, the first command in the example uses the **Get-CsService** cmdlet and the MonitoringDatabase parameter to return a collection of all the monitoring databases. This collection is then piped to the **ForEach-Object** cmdlet. In turn, the **ForEach-Object** cmdlet takes each database in the collection and then runs the **Invoke-CsQoEDatabasePurge** cmdlet against that database, purging all the Quality of Experience records more than 10 days old. 
  
```
Get-CsService -MonitoringDatabase | Invoke-CsQoEDatabasePurge -PurgeQoEDataOlderThanDays 10 -Confirm:$False
```

## Detailed Description
<a name="DetailedDescription"> </a>

Quality of Experience (QoE) metrics track the quality of audio and video calls made in your organization, including such things as the number of network packets lost, background noise, and the amount of "jitter" (differences in packet delay). These metrics are stored in a database apart from other data (such as call detail records), which allows you to enable and disable QoE independent of other data recording.
  
Quality of Experience records are stored in the SQL Server database LcsQoEMetrics. Over time, this database has the potential to grow extremely large. Because of that, Lync Server provides two ways for administrators to purge older records from the database: 1) you can configure Lync Server to automatically delete older QoE records each day; and/or, 2) you can use the **Invoke-CsQoEDatabasePurge** cmdlet at any time to delete Quality of Experience records from the LcsQoEMetrics database. (The **Invoke-CsQoEDatabasePurge** cmdlet does this by calling the SQL Server stored procedure QoePurgeOutdatedReports.) 
  
When you call the **Invoke-CsQoEDatabasePurge** cmdlet you must specify the service location of the monitoring database where the QoE records are stored (for example, MonitoringDatabase:atl-sql-001.litwareinc.com); you must also indicate the minimum age (in days) of the records to be deleted. For example, if you specify a minimum age of 10 days then all QoE records older than 10 days will be deleted from the database. 
  
Note that these records will be deleted even if the purging has been disabled for the specified database. (That is, the EnablePurging property in the QoE configuration settings has been set to False.) The EnablePurging property only controls the automated purging of archiving records; it has no effect on the **Invoke-CsQoEDatabasePurge** cmdlet. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Invoke-CsQoEDatabasePurge"}
  
 **Lync Server Control Panel:** The functions carried out by the **Invoke-CsQoEDatabasePurge** cmdlet are not available in the Lync Server Control Panel. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Service Identity of the monitoring database to be purged. You can retrieve the Identities for your monitoring databases by running this command:  <br/> Get-CsService -MonitoringDatabase  <br/> Note that you cannot use the Identity parameter and the SqlServerFqdn parameter in the same command.  <br/> |
| _PurgeQoEDataOlderThanDays_ <br/> |Required  <br/> |System.Int32  <br/> |Specifies the age (in days) of the QoE records to be purged from the database; any records older than this value will be deleted.  <br/> PurgeQoEDataOlderThanHours can be set to any integer value between 1 and 2147483647, inclusive.  <br/> |
| _SqlServerFqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name of the computer where the QoE database is located. For example:  <br/> -SqlServerFqdn "atl-sql-001.litwareinc.com"  <br/> Note that you cannot use the Identity parameter and the SqlServerFqdn parameter in the same command.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _SqlInstanceName_ <br/> |Optional  <br/> |System.String  <br/> |SQL Server instance name for the QoE database. For example:  <br/> -SqlInstanceName "archinst"  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Invoke-CsQoEDatabasePurge** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.Xds.DisplayMonitoringDatabase#Decorated class. 
  
## Return Types
<a name="ReturnTypes"> </a>

The **Invoke-CsQoEDatabasePurge** cmdlet returns instances of the Microsoft.Rtc.Management.Purge.QoEDataPurgeStatistics class. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[New-CsQoEConfiguration](new-csqoeconfiguration.md)
  
[Set-CsQoEConfiguration](set-csqoeconfiguration.md)

