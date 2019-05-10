---
title: 'Configuring and monitoring the Backup Service'
ms.reviewer: 
author: lanachin
ms.author: v-lanac
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "You can use Skype for Business Server Management Shell commands to configure and monitor the Backup Service."
---

# Configuring and monitoring the Backup Service in Skype for Business Server

You can use the following Skype for Business Server Management Shell commands to configure and monitor the Backup Service. To restore conference information stored in the file store of a Front End pool, see [Restore conference contents using the Backup Service](#restore-conference-contents-using-the-backup-service), below.

> [!NOTE]  
> The RTCUniversalServerAdmins group is the only group that has permissions to run **Get-CsBackupServiceStatus** by default. To use this cmdlet, log on as a member of this group. Or, you can grant access to this command to other groups (for example, CSAdministrator) by using the **Set-CsBackupServiceConfiguration** cmdlet.

## To see the Backup Service configuration

Run the following cmdlet:

    Get-CsBackupServiceConfiguration

The default for SyncInterval is two minutes.

## To set the Backup Service sync interval

Run the following cmdlet:

    Set-CsBackupServiceConfiguration -SyncInterval interval

For example, the following sets the interval to three minutes.

    Set-CsBackupServiceConfiguration -SyncInterval 00:03:00


> [!IMPORTANT]  
> Although you can use this cmdlet to change the default sync interval for the Backup Service, you should not do so unless it is absolutely necessary, as the sync interval has a great impact on the Backup Service performance and the recovery point objective (RPO).

## To get the Backup Service status for a particular pool

Run the following cmdlet:

    Get-CsBackupServiceStatus -PoolFqdn <pool-FQDN>

> [!NOTE]  
> The Backup Service sync status is defined unidirectionally from a pool (P1) to its backup pool (P2). The sync status from P1 to P2 can be different than the one from P2 to P1. For P1 to P2, Backup Service is in a “steady” state if all the changes made in P1 are completely replicated over to P2 within the sync interval. It is in the “final” state if there are no more changes to be synchronized from P1 to P2. Both states indicate a snapshot of the Backup Service at the time the cmdlet is executed. It does not imply that the state returned will stay as is afterwards. In particular, the “final” state will continue to hold only if P1 does not generate any changes after the cmdlet is executed. This is true in the case of failing P1 over to P2 after P1 is placed into the read-only mode as part of the **Invoke-CsPoolfailover** execution logic.

## To get information about the backup relationship for a particular pool

Run the following cmdlet:

    Get-CsPoolBackupRelationship -PoolFQDN <poolFQDN>

## To force a Backup Service sync

Run the following cmdlet:

    Invoke-CsBackupServiceSync -PoolFqdn <poolFqdn> [-BackupModule  {All|PresenceFocus|DataConf|CMSMaster}]

## Restore conference contents using the Backup Service 

If the conference information stored in the file store of a Front End pool becomes unavailable, you must restore this information so that users homed on the pool retain their conference data. If the Front End pool which has lost conference data is paired with another Front End pool, you can use the Backup Service to restore the data.

You must also perform this task if an entire pool has failed and you have to fail over its users to a backup pool. When these users are failed back over to their original pool, you must use this procedure to copy their conference content back to their original pool as well.

Assume that Pool1 is paired with Pool2, and the conference data in Pool1 is lost. You can use the following cmdlet to invoke the Backup Service to restore the contents:

    Invoke-CsBackupServiceSync -PoolFqdn <Pool2 FQDN> -BackupModule ConfServices.DataConf

Restoring the conference contents may take some time, depending on their size. You can use the following cmdlet to check the process status:

    Get-CsBackupServiceStatus -PoolFqdn <Pool2 FQDN> -BackupModule ConfServices.DataConf

The process is done when this cmdlet returns a value of Steady State for the data conference module.
