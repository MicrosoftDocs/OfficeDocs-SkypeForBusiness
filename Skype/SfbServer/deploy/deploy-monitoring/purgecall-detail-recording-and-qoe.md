---
ms.date: 03/17/2018
title: "Manually purge the call detail recording and Quality of Experience databases in Skype for Business Server"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 3a3a965b-b861-41a4-b9a8-27184d622c17
description: "Summary: Learn how to manually purge records from the CDR and the QoE databases used by Skype for Business Server."
---

# Manually purge the call detail recording and Quality of Experience databases in Skype for Business Server
 
**Summary:** Learn how to manually purge records from the CDR and the QoE databases used by Skype for Business Server.
  
The CDR and QoE databases can be manually or automatically purged of records. Purging records can be important so that data doesn't become stale or when needing to reset reports from a starting baseline.
  
## Manually purge records from CDR and QoE databases

Administrators can configure the Call Detail Recording (CDR) and/or the Quality of Experience (QoE) databases to automatically purge old records from the database; this occurs if purging is enabled for the specified database (CDR or QoE) and if there are any records that are in the database longer than the specified amount of time. For example, every day at 1:00 AM administrators might configure the system so that QoE records more than 60 days old are deleted from the QoE database.
  
In addition to that automatic purging, two new cmdlets &#x2014; Invoke-CsCdrDatabasePurge and Invoke-CsQoEDatbasePurge &#x2014; are added to Skype for Business Server; these cmdlets allow administrators to manually purge records from the CDR and the QoE databases at any time. For example, to manually purge all the records more than 10 days old from the CDR database you can use a command similar to this:
  
```powershell
Invoke-CsCdrDatabasePurge -Identity service:MonitoringDatabase:atl-sql-001.litwareinc.com -PurgeCallDetailDataOlderThanDays 10 -PurgeDiagnosticDataOlderThanDays 10
```

In the preceding command, both call detail records and diagnostic data records, older than 10 days are deleted from the monitoring database on atl-sql-001.litwareinc.com. (Call detail records are user/session reports. Diagnostic data records are diagnostic logs uploaded by client applications such as Skype for Business Server.)
  
As shown above, when you run the Invoke-CsCdrDatabasePurge cmdlet you must include both the PurgeCallDetaiDataOlderThanDays and the PurgeDiagnosticDataOlderThanDays parameters. However, these parameters don't have to be set to the same value. For example, it's possible to purge call detail records more than 10 days old and yet, at the same time, leave all the diagnostic data records in the database. To do that, set PurgeCallDetailDataOlderThanDays to 10 and PurgeDiagnosticDataOlderThanDays to 0. For example:
  
```powershell
Invoke-CsCdrDatabasePurge -Identity service:MonitoringDatabase:atl-sql-001.litwareinc.com -PurgeCallDetailDataOlderThanDays 10 -PurgeDiagnosticDataOlderThanDays 0
```

By default, anytime you run Invoke-CsCdrDatabasePurge you see a prompt similar to this one for each database table that must be purged:
  
<pre>
Confirm
Are you sure you want to perform this action?
Performing operation "Stored procedure: RtcCleanupDiag" on Target "Target SQL Server:atl-sql-001.litwareinc.com\archinst Database: lcscdr".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All [S] Suspend  [?] Help (default is "Y"):
</pre>

You must type either Y (for Yes) or A (for Yes to All) before the database purging takes place. If you would prefer to suppress these confirmation prompts, add the following parameter to the end of your call to Invoke-CsCdrDatabasePurge:
  
```powershell
-Confirm:$False
```

For example:
  
```powershell
Invoke-CsCdrDatabasePurge -Identity service:MonitoringDatabase:atl-sql-001.litwareinc.com -PurgeCallDetailDataOlderThanDays 10 -PurgeDiagnosticDataOlderThanDays 10 -Confirm:$False
```

If you do that, confirmation prompts won't be displayed, and database purging is performed.
  
To purge the QoE database, use the Invoke-CsQoEDatabasePurge cmdlet and specify the age (in days) of the records to be deleted:
  
```powershell
Invoke-CsQoEDatabasePurge -Identity service:MonitoringDatabase:atl-sql-001.litwareinc.com -PurgeQoEDataOlderThanDays 10
```



