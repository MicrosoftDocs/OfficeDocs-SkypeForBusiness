---
title: "Backing up Response Group Service (RGS) data in Skype for Business Server 2019"
ms.reviewer: 
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.date: 07/17/2019
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
description: "Summary: Learn how to back up Response Group Service (RGS) data in Skype for Business Server 2019."
---

# Back up Response Group Service (RGS) data

With the Skype for Business Server 2019 July cumulative update, we’ve included the ability to include RGS data as part of the standard backup.

## RGS data replication

To try RGS data replication functionality, please follow the steps below:
1. Install the Jully cumulative update on all front-ends (FEs) of your paired pool.
1. Install the RGS database on both members of the paired pool:
    - `Install-CsDatabase -ConfiguredDatabases -SqlServerFqdn <Pool1 BackendDatabase FQDN>`
    - `Install-CsDatabase -ConfiguredDatabases -SqlServerFqdn <Pool2 BackendDatabase FQDN>`
1. Run the following cmdlet on both pools to replicate existing RGS Data to the backup tables so that the data can be picked up by RGSBackupService:
    - `Invoke-CsRGSStoreReplicateData -PoolFqdn <Pool1 FQDN>`
    - `Invoke-CsRGSStoreReplicateData -PoolFqdn <Pool2 FQDN>`
1. Enable RGSBackupService (This will enable RGSBackupService globally. If this parameter is set to true , RGSBackupService will start syncing RGS data on paired pools (both pools needs to be CU1). Wait for a few minutes to get it started. Initially, RGS BackupService status will be NotInitialized.):
    - `Set-CsBackupServiceConfiguration -EnableRgsBackupService 1`
1. To check BackupServiceStatus:
    - `Get-CsBackupServiceStatus -Category RGS -PoolFqdn <Pool1 FQDN>`
1. To check DataReplication across pools, use these cmdlets (These cmdlets show only owner pool data):
    - `Get-csRGSWorkflow`
    - `Get-csRGSQueue`
    - `Get-csRGSAgentGroup`
    - `Get-csRGSHourOfBusiness`
    - `Get-csRGSHolidaySet`
1. To check Owner pool RGS data and its backup data:
    - `Get-csRGSWorkflow -showAll`
    - `Get-csRGSQueue  -showAll`
    - `Get-csRGSAgentGroup -showAll`
    - `Get-csRGSHourOfBusiness -showAll`
    - `Get-csRGSHolidaySet -showAll`
1. Verify workflow functionality by making an audio call to Workflow.
1. Failover your RGS Owner pool.
1. Verify workflow functionality by making an audio call to Workflow.
1. Failback the pool.
1. Update RGS Data on source pool and perform another failover to check that changes are reflected on backup pool. RGS should behave in same way as it was behaving before failover.
> [!TIP]
> It is recommended you perform these steps on a bulk of data and do frequent failover and failbacks. Any new RGS created after this CU update should also be replicated.


## RGS cmdlets
- To check BackupServiceStatus (The export status should be in the Final or Steady state. The import status should be in the Normal state. RGSBackupservice should be enabled.):
    - `Get-CsBackupServiceStatus -Category RGS -PoolFqdn <Pool1 FQDN>`
- To Fully Sync RGS Data on the backup pool (This will sync the full RGS data on the backup pool.):
    - `Invoke-CsBackupServiceSync -PoolFqdn <Pool1 FQDN> -BackupModule ApplicationServer.RGSDataStore`
- To Fully Sync the RGS filestore on the backup pool (This will sync the full RGS data on the backup pool.):
    - `Invoke-CsBackupServiceSync -PoolFqdn <Pool1 FQDN> -BackupModule ApplicationServer.RGSFileStore`
- To Sync RGS delta data on the backup pool (This will sync delta data on backup pool for RGS only.):
    - `Backup-CsPool -PoolFqdn <Pool FQDN> -Category RGS`
- To sync all module data including RGS:
    - `Backup-CsPool -PoolFqdn <Pool FQDN>`
- To disable RGSBackupService (This will disable RGSBackupService globally. If this parameter is set to true , RGSBackupService will be disabled on all paired pools.):
    - `Set-CsBackupServiceConfiguration -EnableRgsBackupService 0`

