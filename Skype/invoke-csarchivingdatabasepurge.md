---
title: Invoke-CsArchivingDatabasePurge
ms.prod: SKYPEFORBUSINESS
ms.assetid: 02310b08-736d-4ce9-91d8-5a6c8f323d7c
---


# Invoke-CsArchivingDatabasePurge
[]
Manually purges records from the Archiving database. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Invoke-CsArchivingDatabasePurge -Identity <XdsIdentity> <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

The command shown in Example 1 purges all the records more than 24 hours old from the archiving database on atl-sql-001.litwareinc.com. To ensure that all the records are deleted, including records that have not been exported, the PurgeExportedArchivesOnly parameter is set to False ($False).
  
    
    

```

Invoke-CsArchivingDatabasePurge -Identity "service:ArchivingDatabase:atl-sql-001.litwareinc.com" -PurgeArchivingDataOlderThanHours 24 -PurgeExportedArchivesOnly $False
```


### Example 2

The command shown in Example 2 is a variation of the command shown in Example 1; in this case, however, the Confirm parameter is added using this syntax:
  
    
    

```
-Confirm:$False

```

That syntax suppresses the confirmation prompts that would otherwise appear when purging archiving records.
  
    
    



```

Invoke-CsArchivingDatabasePurge -Identity "service:ArchivingDatabase:atl-sql-001.litwareinc.com" -PurgeArchivingDataOlderThanHours 24 -PurgeExportedArchivesOnly $False -Confirm:$False
```


### Example 3

Example 3 purges all the records more than 24 hours old from all the Archiving databases in use in the organization. To do this, the first command in the example uses the **Get-CsService** cmdlet and the ArchivingDatabase parameter to return a collection of all the archiving databases. This collection is then piped to the **ForEach-Object** cmdlet. In turn, the ForEach-Object cmdlet takes each database in the collection and then runs the **Invoke-CsArchivingDatabasePurge** cmdlet against that database, purging all the records more than 24 hours old.
  
    
    

```
Get-CsService -ArchivingDatabase | ForEach-Object {Invoke-CsArchivingDatabasePurge -Identity $_.Identity -PurgeArchivingDataOlderThanHours 24 -PurgeExportedArchivesOnly $False -Confirm:$False}
```


## Detailed Description
<a name="DetailedDescription"> </a>

Many organizations find it useful to keep a transcript of all the IM sessions carried out by their users (or a selected subset of users). For other organizations, it's mandatory to keep such transcripts. For example, many organizations in the financial world are required by law to keep copies of all their electronic communications.
  
    
    
If you have enabled archiving in your organization and if you have chosen to use Skype for Business Server 2015 as your archiving backend, then your archiving records will be stored in the SQL Server database LcsLog. (Alternatively, archiving records can be stored using Microsoft Exchange instead. See the help topic for the **New-CsArchivingConfiguration** cmdlet for more information.) Over time, the archiving database has the potential to grow extremely large. Because of that, Skype for Business Server 2015 provides two ways for administrators to purge older records from the database: 1) you can configure Skype for Business Server 2015 to automatically delete older archiving records each day; and/or, 2) you can use the **Invoke-CsArchivingDatabasePurge** cmdlet at any time to delete archiving records from the LcsLog database. (The **Invoke-CsArchivingDatabasePurge** cmdlet does this by calling the SQL Server stored procedures RtcCleanupTempConference and RtcCleanupDB as well as deleted stored meeting content.)
  
    
    
When you call the **Invoke-CsArchivingDatabasePurge** cmdlet you must specify the service location of the archiving database where the archiving records are stored (for example, ArchivingDatabase:atl-sql-001.litwareinc.com); you must also indicate the minimum age (in hours) of the archiving records to be deleted. For example, if you specify a minimum age of 24 hours then all archiving records older than 24 hours will be deleted from the database.
  
    
    
Note that these records will be deleted even if the purging has been disabled for the specified database. (That is, the EnablePurging property in the archiving configuration settings has been set to False.) The EnablePurging property only controls the automated purging of archiving records; it has no effect on the **Invoke-CsArchivingDatabasePurge** cmdlet.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the **Invoke-CsArchivingDatabasePurge** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Service Identity of the archiving database to be purged. You can retrieve the Identities for your archiving databases by running this command:  <br/>  `Get-CsService -ArchivingDatabase` <br/> Note that you cannot use the Identity parameter and the SqlServerFqdn parameter in the same command.  <br/> |
| _PurgeArchivingDataOlderThanHours_ <br/> |Required  <br/> |System.Int32  <br/> |Specifies the age (in hours) of the archiving records to be purged from the database; any records older than this value will be deleted. PurgeArchivingDataOlderThanHours can be set to any integer value between 1 and 2147483647, inclusive.  <br/> |
| _PurgeExportedArchivesOnly_ <br/> |Required  <br/> |System.Boolean  <br/> |When present, records will be removed for the archiving database only if those records have been exported (and, as a result, have been marked for deletion). Records that have not been exported will remain in the database, even if those records are older than the value specified by the PurgeArchivingDataOlderThanHours property.  <br/> |
| _SqlServerFqdn_ <br/> |Required  <br/> |System.String  <br/> |Fully qualified domain name of the computer where the archiving database is located. For example:  <br/>  `-SqlServerFqdn "atl-sql-001.litwareinc.com"` <br/> Note that you cannot use the Identity parameter and the SqlServerFqdn parameter in the same command.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _MaxArchivingRecordsToDelete_ <br/> |Optional  <br/> |System.Int32  <br/> |Specifies the maximum number of archiving records to be purged from the database; if you set this value to 99 and you have 100 records in the database that meet the PurgeArchivingDataOlderThanHours criterion, only the 99 oldest records will be deleted.  <br/> MaxArchivingRecordsToDelete can be set to any integer value between 1 and 2147483647, inclusive.  <br/> |
| _SqlInstanceName_ <br/> |Optional  <br/> |System.String  <br/> |SQL Server instance name for the archiving database. For example:  <br/>  `-SqlInstanceName "archinst"` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

The **Invoke-CsArchivingDatabasePurge** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.Xds.DisplayArchivingDatabase#Decorated class.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

The Invoke-CsArchivingDatabasePurge cmdlet returns instances of the Microsoft.Rtc.Management.Purge.ArchDataPurgeStatistics class.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [New-CsArchivingConfiguration](new-csarchivingconfiguration.md)
  
    
    
 [Set-CsArchivingConfiguration](set-csarchivingconfiguration.md)
