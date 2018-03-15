---
title: "Infrastructure and deployment cmdlets in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0a6e872a-9f70-4f23-a4a5-8820dbf55370
description: "The infrastructure and deployment cmdlets included in Microsoft Lync Server 2013 can be useful in the initial setup and deployment of the product; after Lync Server has been deployed these cmdlets can then be used to do such things as verify that components are working as expected; manage replication settings; and backup and restore the Lync Server topology, policies, and configuration settings."
---

# Infrastructure and deployment cmdlets in Lync Server 2013
[]
The infrastructure and deployment cmdlets included in Microsoft Lync Server 2013 can be useful in the initial setup and deployment of the product; after Lync Server has been deployed these cmdlets can then be used to do such things as verify that components are working as expected; manage replication settings; and backup and restore the Lync Server topology, policies, and configuration settings.
  
## Infrastructure and Deployment Cmdlets

Administrators will rarely need to directly call many of the infrastructure and deployment. That is because these cmdlets are automatically invoked when you run Setup or the Topology Builder. (One major exception might be the **Export-CsConfiguration** cmdlet, which enables you to make a backup copy of your Lync Server topology, policies, and configuration settings.) However, and when needed, the infrastructure and deployment cmdlets can also be run from the Lync Server Management Shell or from within a script; using a script enables you to automate certain tasks. The following is a list of cmdlets that relate directly to infrastructure and deployment: 
  
 **[Active Directory cmdlets in Lync Server 2013](active-directory-cmdlets.md)**
  
> [Disable-CsAdDomain](disable-csaddomain.md)
    
> [Enable-CsAdDomain](enable-csaddomain.md)
    
> [Get-CsAdDomain](get-csaddomain.md)
    
> [Disable-CsAdForest](disable-csadforest.md)
    
> [Enable-CsAdForest](enable-csadforest.md)
    
> [Get-CsAdForest](get-csadforest.md)
    
> [Get-CsAdServerSchema](get-csadserverschema.md)
    
> [Install-CsAdServerSchema](install-csadserverschema.md)
    
 **[Replication cmdlets in Lync Server 2013](replication-cmdlets.md)**
  
> [Debug-CsInterPoolReplication](debug-csinterpoolreplication.md)
    
> [Invoke-CsManagementStoreReplication](invoke-csmanagementstorereplication.md)
    
> [Get-CsManagementStoreReplicationStatus](get-csmanagementstorereplicationstatus.md)
    
> [Enable-CsReplica](enable-csreplica.md)
    
> [Test-CsReplica](test-csreplica.md)
    
> [Get-CsUserReplicatorConfiguration](get-csuserreplicatorconfiguration.md)
    
> [New-CsUserReplicatorConfiguration](new-csuserreplicatorconfiguration.md)
    
> [Remove-CsUserReplicatorConfiguration](remove-csuserreplicatorconfiguration.md)
    
> [Set-CsUserReplicatorConfiguration](set-csuserreplicatorconfiguration.md)
    
 **[Topology cmdlets jn Lync Server 2013](topology-cmdlets.md)**
  
> [Get-CsPool](get-cspool.md)
    
> [Get-CsSite](get-cssite.md)
    
> [Set-CsSite](set-cssite.md)
    
> [Enable-CsTopology](enable-cstopology.md)
    
> [Get-CsTopology](get-cstopology.md)
    
> [Publish-CsTopology](publish-cstopology.md)
    
> [Test-CsTopology](test-cstopology.md)
    
> [Export-CsConfiguration](export-csconfiguration.md)
    
> [Import-CsConfiguration](import-csconfiguration.md)
    
> [Get-CsServerVersion](get-csserverversion.md)
    
> [Disable-CsComputer](disable-cscomputer.md)
    
> [Enable-CsComputer](enable-cscomputer.md)
    
> [Get-CsComputer](get-cscomputer.md)
    
> [Test-CsComputer](test-cscomputer.md)
    
> [Get-CsNetworkInterface](get-csnetworkinterface.md)
    
 **[Backup and high availability cmdlets in Lync Server 2013](backup-and-high-availability-cmdlets.md)**
  
- [Get-CsBackupServiceConfiguration](get-csbackupserviceconfiguration.md)
    
- [Remove-CsBackupServiceConfiguration](remove-csbackupserviceconfiguration.md)
    
- [Set-CsBackupServiceConfiguration](set-csbackupserviceconfiguration.md)
    
- [Get-CsBackupServiceStatus](get-csbackupservicestatus.md)
    
- [Invoke-CsBackupServiceSync](invoke-csbackupservicesync.md)
    
- [Debug-CsIntraPoolReplication](debug-csintrapoolreplication.md)
    
- [Backup-CsPool](backup-cspool.md)
    
- [Get-CsPoolBackupRelationship](get-cspoolbackuprelationship.md)
    
- [Get-CsPoolFabricState](get-cspoolfabricstate.md)
    
- [Invoke-CsPoolFailBack](invoke-cspoolfailback.md)
    
- [Invoke-CsPoolFailOver](invoke-cspoolfailover.md)
    
- [Get-CsPoolUpgradeReadinessState](get-cspoolupgradereadinessstate.md)
    
- [Invoke-CsStorageServiceFlush](invoke-csstorageserviceflush.md)
    
- [Sync-CsUserData](sync-csuserdata.md)
    
- [Remove-CsUserStoreBackupData](remove-csuserstorebackupdata.md)
    
## See also

#### 

[Lync Server PowerShell Blog](https://go.microsoft.com/fwlink/p/?linkId=203150)

