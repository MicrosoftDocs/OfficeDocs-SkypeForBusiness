---
title: "PurgeSettings table (QoE)"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/1/2018
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 31b85d1c-3f32-4f67-94bf-9389cdd282c5
description: "The PurgeSettings table contains information that specifies if (and when) outdated Quality of Experience records will automatically be deleted from the QoE database. Note that purging-related information can also be obtained from within the Skype for Business Server Management Shell by running the following command:"
---

# PurgeSettings table (QoE)
 
The PurgeSettings table contains information that specifies if (and when) outdated Quality of Experience records will automatically be deleted from the QoE database. Note that purging-related information can also be obtained from within the Skype for Business Server Management Shell by running the following command:
  
```
Get-CsQoEConfiguration
```

This table was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**ID** <br/> |int  <br/> |Primary  <br/> |Unique identifier for the collection of QoE purge settings.  <br/> |
|**EnablePurge** <br/> |bit  <br/> ||When set to True (1) Microsoft Lync Server 2013 will periodically purge outdated records from the QoE database. Purging will take place each day at the tome specified by the PurgeHour setting. If set to False (0) then records will not be automatically purged from the database. The default value is True.  <br/> |
|**KeepQoEDataForDays** <br/> |int  <br/> ||Specifies the age of QoE records (in days) that will be purged from the database: if purging is enabled, QoE records older than this value will be removed from the database. The default value is 60 days.  <br/> |
|**PurgeHour** <br/> |int  <br/> ||Specifies the local time of day when database purging will take place. The time of day is specified using a 24-hour clock, with 0 representing midnight (12:00 AM) and 23 representing 11:00 PM. Note that you can only specify the hour of the day: a value of 10 (indicating 10:00 AM) is allowed, but a value of 10:30 of 10.5 (indicating 10:30 AM) is not allowed. The default value is 1 (1:00 AM). Specifies the local time of day when database purging will take place. The time of day is specified using a 24-hour clock, with 0 representing midnight (12:00 AM) and 23 representing 11:00 PM. Note that you can only specify the hour of the day: a value of 10 (indicating 10:00 AM) is allowed, but a value of 10:30 of 10.5 (indicating 10:30 AM) is not allowed. The default value is 1 (1:00 AM).  <br/> |
   

