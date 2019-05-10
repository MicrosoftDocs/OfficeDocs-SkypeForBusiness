---
title: "PurgeSettings table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 10/20/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 9ff2c8fc-4ae8-4f22-96a8-1f4d5eecbf2d
description: "The PurgeSettings table contains information that specifies if (and when) outdated call detail records will automatically be deleted from the CDR database. Note that purging-related information can also be obtained from within the Skype for Business Server 2015 by running the following command:"
---

# PurgeSettings table
 
The PurgeSettings table contains information that specifies if (and when) outdated call detail records will automatically be deleted from the CDR database. Note that purging-related information can also be obtained from within the Skype for Business Server 2015 by running the following command:
  
```
Get-CsCdrConfiguration
```

Administrators should treat the PurgeSettings table as read-only: changes to the call detail purge settings should only be made using the [New-CsCdrConfiguration](https://docs.microsoft.com/powershell/module/skype/new-cscdrconfiguration?view=skype-ps) or [Set-CsCdrConfiguration](https://docs.microsoft.com/powershell/module/skype/set-cscdrconfiguration?view=skype-ps) cmdlets.
  
This table was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**Id** <br/> |int  <br/> |Primary  <br/> |Unique identifier for the collection of CDR purge settings.  <br/> |
|**EnablePurge** <br/> |bit  <br/> ||When set to True (1) Skype for Business Server 2015 will periodically purge outdated records from the CDR database. Purging will take place each day at the tome specified by the PurgeHour setting. If set to False (0) then records will not be automatically purged from the database. The default value is True.  <br/> |
|**KeepCallDetailForDays** <br/> |int  <br/> ||Specifies the age of CDR records (in days) that will be purged from the database: if purging is enabled, CDR records older than this value will be removed from the database. The default value is 60 days.  <br/> |
|**KeepErrorReportForDays** <br/> |int  <br/> ||Specifies the age of error report records (in days) that will be purged from the database: if purging is enabled, error report records older than this value will be removed from the database. The default value is 60 days.  <br/> |
|**PurgeHour** <br/> |int  <br/> ||Specifies the local time of day when database purging will take place. The time of day is specified using a 24-hour clock, with 0 representing midnight (12:00 AM) and 23 representing 11:00 PM. Note that you can only specify the hour of the day: a value of 10 (indicating 10:00 AM) is allowed, but a value of 10:30 of 10.5 (indicating 10:30 AM) is not allowed. The default value is 2 (2:00 AM).  <br/> |
   

