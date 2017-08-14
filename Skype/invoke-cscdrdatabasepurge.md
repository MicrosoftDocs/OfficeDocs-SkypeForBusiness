---
title: Invoke-CsCdrDatabasePurge
ms.prod: SKYPEFORBUSINESS
ms.assetid: 95eb0faf-49dc-4afb-b98c-15735a4cab13
---


# Invoke-CsCdrDatabasePurge
[]
Manually purges records from the Call Detail records (CDR) database. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Invoke-CsCdrDatabasePurge -Identity <XdsIdentity> <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 deletes all the records (both call detail and diagnostic records) from the monitoring database atl-sql-001.litwareinc.com that are more than 10 days old.
  
    
    

```

Invoke-CsCdrDatabasePurge -Identity "service:MonitoringDatabase:atl-sql-001.litwareinc.com" -PurgeCallDetailDataOlderThanDays 10 -PurgeDiagnosticDataOlderThanDays 10
```


### Example 2

The command shown in Example 2 is a variation of the command shown in Example 1; in this case, however, the Confirm parameter is added using this syntax:
  
    
    

```
-Confirm:$False

```

That syntax suppresses the confirmation prompts that would otherwise appear when purging CDR records.
  
    
    



```

Invoke-CsCdrDatabasePurge -Identity "service:MonitoringDatabase:atl-sql-001.litwareinc.com" -PurgeCallDetailDataOlderThanDays 10 -PurgeDiagnosticDataOlderThanDays 10 -Confirm:$False
```


### Example 3

Example 3 purges all the records more than 10 days old from all the CDR databases in use in the organization. To do this, the first command in the example uses the **Get-CsService** cmdlet and the MonitoringDatabase parameter to return a collection of all the monitoring databases. This collection is then piped to the **ForEach-Object** cmdlet. In turn, the **ForEach-Object** cmdlet takes each database in the collection and then runs the **Invoke-CsCdrDatabasePurge** cmdlet against that database, purging all the call detail records more than 10 days old.
  
    
    

```
Get-CsService -MonitoringDatabase | ForEach-Object {Invoke-CsCdrDatabasePurge -Identity $_.Identity -PurgeCallDetailDataOlderThanDays 10 -PurgeDiagnosticDataOlderThanDays 10 -Confirm:$False}
```


## Detailed Description
<a name="DetailedDescription"> </a>

Call detail recording (CDR) provides a way for you to track usage of Skype for Business Server 2015 capabilities such as Voice over IP (VoIP) phone calls; instant messaging (IM); file transfers; audio/video (A/V) conferencing; and application sharing sessions. CDR keeps usage information: it logs information such as the parties involved in the call; the length of the call; and whether or not any files were transferred. However, CDR does not make a recording of the call itself.
  
    
    
CDR also keeps track of call error information: detailed diagnostic data for both peer-to-peer sessions and for conferencing calls.
  
    
    
Call detail records are stored in the SQL Server database LcsCDR. Over time, this database has the potential to grow extremely large. Because of that, Skype for Business Server 2015 provides two ways for administrators to purge older records from the database: 1) you can configure Skype for Business Server 2015 to automatically delete older CDR records each day; and/or, 2) you can use the **Invoke-CsCdrDatabasePurge** cmdlet at any time to delete CDR records from the LcsCDR database. (The **Invoke-CsCdrDatabasePurge** cmdlet does this by calling the SQL Server stored procedure RtcCleanupDB.)
  
    
    
When you call the **Invoke-CsCdrDatabasePurge** cmdlet you must specify the service location of the monitoring database where the CDR records are stored (for example, MonitoringDatabase:atl-sql-001.litwareinc.com); you must also indicate the minimum age (in days) of the call detail and diagnostic data records to be deleted. For example, if you specify a minimum age of 10 days for call detail records, then all call detail records older than 10 days will be deleted from the database.
  
    
    
Note that these records will be deleted even if the purging has been disabled for the specified database. (That is, the EnablePurging property in the CDR configuration settings has been set to False.) The EnablePurging property only controls the automated purging of CDR records; it has no effect on the **Invoke-CsCdrDatabasePurge** cmdlet.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the **Invoke-CsCdrDatabasePurge** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Service Identity of the monitoring database to be purged. You can retrieve the Identities for your monitoring databases by running this command:  <br/>  `Get-CsService -MonitoringDatabase` <br/> Note that you cannot use the Identity parameter and the SqlServerFqdn parameter in the same command.  <br/> |
| _PurgeCallDetailDataOlderThanDays_ <br/> |Required  <br/> |System.Int32  <br/> |Specifies the age (in days) of the call detail records to be purged from the database; any records older than this value will be deleted. Call detail records represent user/session reports. They differ from diagnostic data reports, which are diagnostic logs uploaded by client applications such as Skype for Business.  <br/> PurgeCallDetailDataOlderThanDays can be set to any integer value between 1 and 2147483647, inclusive.  <br/> |
| _PurgeDiagnosticDataOlderThanDays_ <br/> |Required  <br/> |System.Int32  <br/> |Specifies the age (in days) of the diagnostic data records to be purged from the database; any records older than this value will be deleted. Diagnostic data reports are diagnostic logs uploaded by client applications such as Skype for Business.  <br/> PurgeDiagnosticDataOlderThanHours can be set to any integer value between 1 and 2147483647, inclusive.  <br/> |
| _SqlServerFqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name of the computer where the CDR database is located. For example:  <br/>  `-SqlServerFqdn "atl-sql-001.litwareinc.com"` <br/> Note that you cannot use the Identity parameter and the SqlServerFqdn parameter in the same command.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _SqlInstanceName_ <br/> |Optional  <br/> |System.String  <br/> |SQL Server instance name for the CDR database. For example:  <br/>  `-SqlInstanceName "archinst"` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

The **Invoke-CsCdrDatabasePurge** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.Xds.DisplayMonitoringDatabase#Decorated class.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

The **Invoke-CsCdrDatabasePurge** cmdlet returns instances of the Microsoft.Rtc.Management.Purge.CdrDataPurgeStatistics class.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [New-CsCdrConfiguration](new-cscdrconfiguration.md)
  
    
    
 [Set-CsCdrConfiguration](set-cscdrconfiguration.md)
