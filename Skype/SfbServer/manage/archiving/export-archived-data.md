---
title: "Export archived data in Skype for Business Server 2015"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 3/28/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8214bb0a-baa7-414f-9eee-313b65223fa3
description: "Summary: Learn how to export archived data for Skype for Business Server 2015."
---

# Export archived data in Skype for Business Server 2015

 **Summary:** Learn how to export archived data for Skype for Business Server 2015.
  
Data archived in Archiving databases is not searchable or in a readable format, but you can use the **Export-CsArchivingData** cmdlet to extract records from the database and save them as an Outlook Electronic Mail (EML) file.
  
If you enable Microsoft Exchange integration, data is archived in Exchange stores. Data archived in Exchange is searchable and discoverable. For details about accessing data that is archived in Exchange, see the Exchange documentation.
  
## Exporting Archiving Data by Using Windows PowerShell Cmdlets

You can export archived data by using the Export-CSArchivingData cmdlet. 
  
The following command exports all the archiving data written to the archiving database atl-sql-001.contoso.com since June 1, 2012. The resulting output file will be stored in the folder C:\ArchivingExports.
  
```
Export-CsArchivingData -Identity "ArchivingDatabase:atl-sql-001.contoso.com" -StartDate 6/1/2012 -OutputFolder "C:\ArchivingExports"
```

The following command exports archiving data for a single user: kenmyer@contoso.com. This is done by including the UserUri parameter followed by the user's SIP address. For example: 
  
```
Export-CsArchivingData -Identity "ArchivingDatabase:atl-sql-001.contoso.com" -StartDate 6/1/2012 -OutputFolder "C:\ArchivingExports" -UserUri "sip:kenmyer@contoso.com"
```

For more information, see the help topic for the [Export-CsArchivingData](../../manage/management-shell/export-csarchivingdata.md) cmdlet.
  

