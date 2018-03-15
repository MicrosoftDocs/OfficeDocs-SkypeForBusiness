---
title: "Restoring conference contents using the Backup Service in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3e0f18ec-7319-4c07-a59b-2938e7787bc9
description: "If the conference information stored in the file store of a Front End pool becomes unavailable. you must restore this information so that users homed on the pool retain their conference data. If the Front End pool which has lost conference data is paired with another Front End pool, you can use the Backup Service to restore the data."
---

# Restoring conference contents using the Backup Service in Lync Server 2013
[]
If the conference information stored in the file store of a Front End pool becomes unavailable. you must restore this information so that users homed on the pool retain their conference data. If the Front End pool which has lost conference data is paired with another Front End pool, you can use the Backup Service to restore the data.
  
You must also perform this task if an entire pool has failed and you have to fail over its users to a backup pool. When these users are failed back over to their original pool, you must use this procedure to copy their conference content back to their original pool as well.
  
Assume that Pool1 is paired with Pool2, and the conference data in Pool1 is lost. You can use the following cmdlet to invoke the Backup Service to restore the contents:
  
```
Invoke-CsBackupServiceSync -PoolFqdn <Pool2 FQDN> -BackupModule ConfServices.DataConf
```

Restoring the conference contents may take some time, depending on their size. You can use the following cmdlet to check the process status:
  
```
Get-CsBackupServiceStatus -PoolFqdn <Pool2 FQDN> -BackupModule ConfServices.DataConf
```

The process is done when this cmdlet returns a value of Steady State for the data conference module.
  

