---
title: "Antivirus scanning exclusions for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/2/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 71e1f1cc-2d16-4111-9864-9276bf24dfe0
description: "To ensure that the antivirus scanner does not interfere with the operation of Lync Server 2013, you must exclude specific processes and directories for each Lync Server 2013 server or server role on which you run an antivirus scanner. The following processes and directories should be excluded:"
---

# Antivirus scanning exclusions for Lync Server 2013
[]
To ensure that the antivirus scanner does not interfere with the operation of Lync Server 2013, you must exclude specific processes and directories for each Lync Server 2013 server or server role on which you run an antivirus scanner. The following processes and directories should be excluded:
  
> [!NOTE]
> Folder and file locations listed below are the default locations for Lync Server 2013. For any locations for which you did not use the default, exclude the locations you specified for your organization instead of the default locations specified in this topic. 
  
> [!IMPORTANT]
> Please note that some antivirus programs may need absolute, not relative paths, for their exclusion list. 
  
- Lync Server 2013 processes:
    
  - ABServer.exe
    
  - AcpMcuSvc.exe
    
  - ASMCUSvc.exe
    
  - AVMCUSvc.exe
    
  - ChannelService.exe
    
  - ClsAgent.exe
    
  - ComplianceService.exe
    
  - DataMCUSvc.exe
    
  - DataProxy.exe
    
  - FileTransferAgent.exe
    
  - IMMCUSvc.exe
    
  - LysSvc.exe
    
  - MasterReplicatorAgent.exe
    
  - MediaRelaySvc.exe
    
  - MediationServerSvc.exe
    
  - MRASSvc.exe
    
  - OcsAppServerHost.exe
    
  - ReplicaReplicatorAgent.exe
    
  - ReplicationApp.exe
    
  - RtcHost.exe
    
  - RTCSrv.exe
    
  - XmppProxy.exe
    
  - XmppTGW.exe
    
- Windows Fabric Host Service processes:
    
  - Fabric.exe
    
  - FabricDCA.exe
    
  - FabricHost.exe
    
- IIS processes:
    
  - %systemroot%\system32\inetsrv\w3wp.exe
    
  - %systemroot%\SysWOW64\inetsrv\w3wp.exe
    
- SQL Server Back-End processes:
    
  - %ProgramFiles%\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Binn\SQLServr.exe
    
  - %ProgramFiles%\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer\Bin\ReportingServicesService.exe
    
  - %ProgramFiles%\Microsoft SQL Server\MSAS11.MSSQLSERVER\OLAP\Bin\MSMDSrv.exe
    
- SQL Server Front-End processes:
    
  - %ProgramFiles%\Microsoft SQL Server\MSSQL11.LYNCLOCAL\MSSQL\Binn\SQLServr.exe
    
  - %ProgramFiles%\Microsoft SQL Server\MSSQL11.RTCLOCAL\MSSQL\Binn\SQLServr.exe
    
- Directories and files:
    
  - %systemroot%\System32\LogFiles
    
  - %systemroot%\SysWow64\LogFiles
    
  - %systemroot%\Microsoft.NET\assembly\GAC_MSIL
    
  - %programfiles%\Microsoft Lync Server 2013
    
  - %programfiles%\Common Files\Microsoft Lync Server 2013\Watcher Node
    
  - %programfiles%\Common Files\Microsoft Lync Server 2013
    
  - %SystemDrive%\RtcReplicaRoot
    
  - File share store (specified in Topology Builder). File stores are specified in Topology Builder.
    
  - SQL Server data and log files, including those for the back-end database, user store, archiving store, monitoring store, and application store. Database and log files can be specified in Topology Builder. For details about the data and log files for each database, including default names, see [SQL Server data and log file placement for Lync Server 2013](sql-server-data-and-log-file-placement.md) in the Deployment documentation. 
    
  - SQL Server data and log files, including those for the Front-end database, Lync store, and RtcDatabase store. They are normally under %localdrive%\CSData.
    

