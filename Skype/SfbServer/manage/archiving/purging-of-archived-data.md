---
title: "Manage purging of archived data in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 14c2b4fd-f612-4909-808d-09c655fc9f8a
description: "Summary: Learn how to manage purging of archived data for Skype for Business Server."
---

# Manage purging of archived data in Skype for Business Server

**Summary:** Learn how to manage purging of archived data for Skype for Business Server.
  
The Archiving database is not intended for long-term retention, and Skype for Business Server does not provide an e-discovery (search) solution for archived data, so data needs to be moved to other storage. Skype for Business Server provides a session export tool that you can use to export archived data into searchable transcripts. You need to define when to purge archived and exported data. 
  
For more information about exporting data by using the **Export-CsArchivingData** cmdlet, see [Export archived data in Skype for Business Server](export-archived-data.md).
  
## Manage purging of data by using the Control Panel

To manage purging of archived data by using the Control Panel:
  
1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment. 
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Configuration**.
    
4. Click the name of the appropriate global, site, or pool configuration in the list of archiving configurations, click **Edit**, click **Show details**, and then do the following:
    
   - To enable purging, select the **Enable purging of archiving data** check box and then do one of the following:
    
     - To purge all records, click the **Purge exported archiving data and stored archiving data after maximum duration (days)**, and then specify the number of days.
    
     - To purge only the data that has been exported, click **Purge exported archiving data only**.
    
   - To disable purging, clear the **Enable purging of archiving data** check box.
    
5. Click **Commit**.
    
## Manage purging of data by using Windows PowerShell

You can manage purging of archived data by using the following Windows PowerShell cmdlets:
  
- **Set-CsArchivingConfiguration** cmdlet with the EnablePurging parameter lets you enable or disable purging of archived data.
    
- **Invoke-CsArchivingDatabasePurge** lets you manually purge records from the Archiving database.
    
For example, the following command enables the purging of all archived data. After this command is run, Skype for Business Server will purge all archiving records older than the value specified for the KeepArchivingDataForDays parameter. 
  
```
Set-CsArchivingConfiguration -Identity "site:Redmond" -EnablePurging $True
```

The following command limits purging to archived records that have been exported to a data file (by using the **Export-CSArchivingData** cmdlet). You must also set the PurgeExportedArchivesOnly parameter to True ($True):
  
```
Set-CsArchivingConfiguration -Identity "site:Redmond" -EnablePurging $True -PurgeExportedArchivesOnly $True
```

After this command is run, Skype for Business Server will only purge archiving records that meet two criteria: 1) they are older than the value specified for the KeepArchivingDataForDays parameter; and, 2) they have been exported by using the **Export-CsArchivingData** cmdlet.
  
To disable the automated purging of archiving records, set the EnablePurging parameter to False ($False):
  
```
Set-CsArchivingConfiguration -Identity "site:Redmond" -EnablePurging $False
```

The following example uses the **Invoke-CsArchivingDatabasePurge** cmdlet to purge all the records more than 24 hours old from the archiving database on atl-sql-001.contoso.com. To ensure that all the records are deleted, including records that have not been exported, the PurgeExportedArchivesOnly parameter is set to False ($False):
  
```
Invoke-CsArchivingDatabasePurge -Identity "service:ArchivingDatabase:atl-sql-001.contoso.com" -PurgeArchivingDataOlderThanHours 24 -PurgeExportedArchivesOnly $False
```
