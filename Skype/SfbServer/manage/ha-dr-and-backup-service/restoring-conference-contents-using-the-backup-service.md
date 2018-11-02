---
title: 'Restoring conference contents using the Backup Service'
author: heidip
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "If the conference information stored in the file store of a Front End pool becomes unavailable, you must restore this information so that users homed on the pool retain their conference data."
---


# Restoring conference contents using the Backup Service in Skype for Business Server

If the conference information stored in the file store of a Front End pool becomes unavailable, you must restore this information so that users homed on the pool retain their conference data. If the Front End pool which has lost conference data is paired with another Front End pool, you can use the Backup Service to restore the data.

You must also perform this task if an entire pool has failed and you have to fail over its users to a backup pool. When these users are failed back over to their original pool, you must use this procedure to copy their conference content back to their original pool as well.

Assume that Pool1 is paired with Pool2, and the conference data in Pool1 is lost. You can use the following cmdlet to invoke the Backup Service to restore the contents:

    Invoke-CsBackupServiceSync -PoolFqdn <Pool2 FQDN> -BackupModule ConfServices.DataConf

Restoring the conference contents may take some time, depending on their size. You can use the following cmdlet to check the process status:

    Get-CsBackupServiceStatus -PoolFqdn <Pool2 FQDN> -BackupModule ConfServices.DataConf

The process is done when this cmdlet returns a value of Steady State for the data conference module.