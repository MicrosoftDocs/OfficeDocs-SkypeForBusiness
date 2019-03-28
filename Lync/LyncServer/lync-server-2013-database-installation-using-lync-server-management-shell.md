---
title: 'Lync Server 2013: Database installation using Lync Server Management Shell'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Database installation using Lync Server Management Shell
ms:assetid: c90a6449-4dd5-4b18-b21c-ea2c2a64dc3c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398832(v=OCS.15)
ms:contentKeyID: 48185401
ms.date: 06/16/2016
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Database installation using Lync Server Management Shell in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-06-16_

Separation of roles and responsibilities between server administrators and SQL Server administrators can result in delays in implementation. Lync Server 2013 uses role-based access control (RBAC) to mitigate these difficulties. In some instances, the SQL Server administrator must manage the installation of databases on the SQL Server-based server outside RBAC. The Lync Server 2013 Management Shell provides a way for the SQL Server administrator to run Windows PowerShell cmdlets designed to configure the databases with the correct data and log files. For details, see [Deployment permissions for SQL Server in Lync Server 2013](lync-server-2013-deployment-permissions-for-sql-server.md).

<div class=" ">


> [!IMPORTANT]  
> The following procedure assumes that at a minimum the Lync Server 2013 OCSCore.msi, SQL Server Native Client (sqlncli.msi) Microsoft SQL Server 2012 Management Objects, CLR Types for Microsoft SQL Server 2012 and Microsoft SQL Server 2012 ADOMD.NET are installed. The OCSCore.msi is located on the installation media in the \Setup\AMD64\Setup directory. The remaining components are located in \Setup\amd64. Additionally, Active Directory preparation for Lync Server 2013 has been successfully completed.



</div>

**Install-CsDatabase** is the Windows PowerShell cmdlet you use to install the databases. The **Install-CsDatabase** cmdlet has a large number of parameters, only a few of which are discussed here. For details about the possible parameters, see the Lync Server 2013 Management Shell documentation.

<div class=" ">


> [!WARNING]  
> To avoid performance and possible time-out issues, always use fully qualified domain names (FQDNs) when referring to SQL Server-based servers. Avoid using host name-only references. For example, use sqlbe01.contoso.net, but avoid using SQLBE01.



</div>

For installing databases, **Install-CsDatabase** uses three primary methods for placing the databases onto the prepared SQL Server-based server:

  - Run **Install-CsDatabase** without DatabasePaths or UseDefaultSqlPath. The cmdlet uses a built in algorithm to determine the best placement for the log and data files. The algorithm only works for stand-alone SQL Server implementations.

  - Run **Install-CsDatabase** with the DatabasePaths parameter. The built-in algorithm to optimize log and data file locations is not used if the DatabasePaths parameter is defined. Using this parameter allows you to define the locations where log and data files will be deployed.

  - Run **Install-CsDatabase** with UseDefaultSqlPaths. This option does not use the built-in algorithm to optimize the log and data file locations. Log and data file are deployed according to the defaults set by the SQL Server administrator. These paths are typically set for the purpose of automatic administration of log and data files on the SQL Server in advance, and are not associated with the setup of Lync Server 2013.

  - The DatabasePathMap parameter can also be used to explicitly specify a location for each database and its respective log file.

<div>

## To use Windows PowerShell cmdlets to configure the SQL Server Central Management store

1.  On any computer, log on with administrative credentials for creating the databases on the SQL Server-based server. For details, see [Deployment permissions for SQL Server in Lync Server 2013](lync-server-2013-deployment-permissions-for-sql-server.md).

2.  Open the Lync Server 2013 Management Shell. If you have not adjusted the execution policy for Windows PowerShell, you must adjust the policy to allow Windows PowerShell scripts to run. For details, see “Examining the Execution Policy” at [http://go.microsoft.com/fwlink/p/?linkId=203093](http://go.microsoft.com/fwlink/p/?linkid=203093).

3.  Use the **Install-CsDatabase** cmdlet to install the Central Management store.
    
       ```
        Install-CsDatabase -CentralManagementDatabase -SqlServerFqdn <fully qualified domain name of SQL Server> 
        -SqlInstanceName <named instance> -DatabasePaths <logfile path>,<database file path> 
        -Report <path to report file>
       ```
    
       ```
        Install-CsDatabase -CentralManagementDatabase -SqlServerFqdn sqlbe.contoso.net -SqlInstanceName rtc -DatabasePaths "C:\CSDB-Logs","C:\CSDB-CMS" -Report "C:\Logs\InstallDatabases.html"
       ```
    
    <div class=" ">
    

    > [!TIP]  
    > The Report parameter is optional but is useful if you are documenting the installation process.

    
    </div>

4.  **Install-CsDatabase –DatabasePaths** can use up to six path parameters, each defining the paths for the drives as defined in SQL Server Data and Log File Placement. By the logical rules of the database configuration in Lync Server 2013, drives are parsed out into buckets of two, four, or six. Depending on your SQL Server configuration and the number of buckets, you will supply two paths, four paths, or six paths.
    
    If you have three drives, the log gets priority and the data files are distributed after. An example for a SQL Server-based server configured with six drives:
    
        Install-CsDatabase -ConfiguredDatases -SqlServerFqdn sqlbe.contoso.net -DatabasePaths "D:\CSDynLogs","E:\CSRtcLogs","F:\MonCdrArcLogs","G:\MonCdrArchData","H:\AbsAppLog","I:\DynRtcAbsAppData" -Report "C:\Logs\InstallDatabases.html"

5.  When the database installation completes, you can close Lync Server 2013 Management Shell or proceed to the installation of the Lync Server 2013 configured databases defined in Topology Builder.

</div>

<div>

## To use Windows PowerShell cmdlets to configure the SQL Server topology configured databases

1.  To install the Topology Builder configured databases for Lync Server 2013, the Lync Server 2013 administrator must publish the topology. For details, see [Publish the topology in Lync Server 2013](lync-server-2013-publish-the-topology.md) in the Deployment documentation.

2.  On any computer, log on with administrative credentials for creating the databases on the SQL Server-based server. See the topic, [Deployment permissions for SQL Server in Lync Server 2013](lync-server-2013-deployment-permissions-for-sql-server.md).
    
    <div class=" ">
    

    > [!IMPORTANT]  
    > To be able to configure the SQL Server-based databases, make sure the SQL Server administrator account used to run the steps described here is also a member of the sysadmins group (or equivalent) on the server running SQL Server and holding the Central Management Server role. This is especially important to check for any additional Lync Server 2013 pools which require SQL Server database installation or configuration. For example, if you are deploying a second pool (pool02) but the Central Management Server role is held by pool01. The SQL Server sysadmin group (or equivalent) must have permissions on both SQL Server-based databases.

    
    </div>

3.  Open Lync Server 2013 Management Shell, if it’s not already open.

4.  Use the **Install-CsDatabase** cmdlet to install the Topology Builder configured databases.
    
       ```
        Install-CsDatabase -ConfiguredDatabases -SqlServerFqdn <fully qualified domain name of SQL Server> 
         -DatabasePaths <logfile path>,<database file path> -Report <path to report file>
       ```
    
       ```
        Install-CsDatabase -ConfiguredDatabases -SqlServerFqdn sqlbe.contoso.net 
        -Report "C:\Logs\InstallDatabases.html"
       ```
    
    <div class=" ">
    

    > [!TIP]  
    > The Report parameter is optional but is useful if you are documenting the installation process.

    
    </div>

5.  When the database installation completes, close Lync Server 2013 Management Shell.

</div>

<div>

## To use Windows PowerShell cmdlets to configure the SQL Server topology using the DatabasePathMap parameter

1.  To install databases for Lync Server 2013, the Lync Server administrator must create the paths and deploy the databases files and log files according to a predefined set of rules.

2.  On any computer, log on with administrative credentials for creating the databases on the SQL Server-based server. See the topic, [Deployment permissions for SQL Server in Lync Server 2013](lync-server-2013-deployment-permissions-for-sql-server.md).
    
    <div class=" ">
    

    > [!IMPORTANT]  
    > To be able to configure the SQL Server-based databases, make sure the SQL Server administrator account used to run the steps described here is also a member of the sysadmins group (or equivalent) on the server running SQL Server and holding the Central Management Server role. This is especially important to check for any additional Lync Server pools which require SQL Server database installation or configuration. For example, if you are deploying a second pool (pool02) but the Central Management Server role is held by pool01. The SQL Server sysadmin group (or equivalent) must have permissions on both SQL Server-based databases.

    
    </div>

3.  Open Lync Server Management Shell, if it’s not already open.

4.  Use the **Install-CsDatabase** cmdlet with the DatabasePathMap parameter and a PowerShell hash table to install the Topology Builder configured databases.

5.  In the example code, the paths defined for the databases can be determined in a granular manner by using the –DatabasePathMap parameter and a defined hash table as follows (the example uses “C:\\CSData” for all database (.mdf) files, and “C:\\CSLogFiles” for all log (.ldf) files. Folder will be created as needed by Install-CsDatabase):
    
        $pathmap = @{
        "BackendStore:BlobStore:DbPath"="C:\CsData";"BackendStore:BlobStore:LogPath"="C:\CsLogFiles"
        "BackendStore:RtcSharedDatabase:DbPath"="C:\CsData";"BackendStore:RtcSharedDatabase:LogPath"="C:\CsLogFiles"
        "ABSStore:AbsDatabase:DbPath"="C:\CsData";"ABSStore:AbsDatabase:LogPath"="C:\CsLogFiles"
        "ApplicationStore:RgsConfigDatabase:DbPath"="C:\CsData";"ApplicationStore:RgsConfigDatabase:LogPath"="C:\CsLogFiles"
        "ApplicationStore:RgsDynDatabase:DbPath"="C:\CsData";"ApplicationStore:RgsDynDatabase:LogPath"="C:\CsLogFiles"
        "ApplicationStore:CpsDynDatabase:DbPath"="C:\CsData";"ApplicationStore:CpsDynDatabase:LogPath"="C:\CsLogFiles"
        "ArchivingStore:ArchivingDatabase:DbPath"="C:\CsData";"ArchivingStore:ArchivingDatabase:LogPath"="C:\CsLogFiles"
        "MonitoringStore:MonitoringDatabase:DbPath"="C:\CsData";"MonitoringStore:MonitoringDatabase:LogPath"="C:\CsLogFiles"
        "MonitoringStore:QoEMetricsDatabase:DbPath"="C:\CsData";"MonitoringStore:QoEMetricsDatabase:LogPath"="C:\CsLogFiles"
        }
        Install-CsDatabase -ConfigureDatabases -SqlServerFqdn sqlbe01.contoso.net -DatabasePathMap $pathmap

6.  Because the database and log files are explicitly named with their location on the destination database server, you can define specific locations for each service type’s actual database and log location. The following example puts databases for each specific service type on separate disks, and associated log files on another. For example:
    
      - All RTC databases to “D:\\RTCDatabase”
    
      - All RTC log files to “E:\\RTCLogs”
    
      - All application store databases to “F:\\CPSDatabases”
    
      - All application store logs to “G:\\CPSLogs”
    
      - All response group store databases to “H:\\RGSDatabases”
    
      - All response group store logs to “I:\\RGSLogs”
    
      - All address book store databases to “J:\\ABSDatabases”
    
      - All address book store log files to “K:\\ABSLogs”
    
      - All archiving store databases to “L:\\ArchivingDatabases”
    
      - All archiving store logs to “M:\\ArchivingLogs”
    
      - All monitoring store databases to “N:\\MonitoringDatabases”
    
      - All monitoring store log files to “O:\\MonitoringLogfiles”
    
    <!-- end list -->
    
    ``` 
    
    $pathmap = @{
    "BackendStore:BlobStore:DbPath"="D:\RTCDatabase";"BackendStore:BlobStore:LogPath"="E:\RTCLogs"
    "BackendStore:RtcSharedDatabase:DbPath"="D:\RTCDatabase";"BackendStore:RtcSharedDatabase:LogPath"="E:\RTCLogs"
    "ABSStore:AbsDatabase:DbPath"="J:\ABSDatabases";"ABSStore:AbsDatabase:LogPath"="K:\ABSLogs"
    "ApplicationStore:RgsConfigDatabase:DbPath"="H:\RGSDatabases";"ApplicationStore:RgsConfigDatabase:LogPath"="G:\CPSLogs"
    "ApplicationStore:RgsDynDatabase:DbPath"="H:\RGSDatabases";"ApplicationStore:RgsDynDatabase:LogPath"="I:\RGSLogs"
    "ApplicationStore:CpsDynDatabase:DbPath"="F:\CPSDatabases";"ApplicationStore:CpsDynDatabase:LogPath"="G:\CsLogFiles"
    "ArchivingStore:ArchivingDatabase:DbPath"="M:\ArchivingLogs";"ArchivingStore:ArchivingDatabase:LogPath"="N:\MonitoringDatabases"
    "MonitoringStore:MonitoringDatabase:DbPath"="N:\MonitoringDatabases";"MonitoringStore:MonitoringDatabase:LogPath"="O:\MonitoringLogfiles"
    "MonitoringStore:QoEMetricsDatabase:DbPath"="N:\MonitoringDatabases";"MonitoringStore:QoEMetricsDatabase:LogPath"="O:\MonitoringLogfiles"
    }
    
    Install-CsDatabase -ConfiguredDatabases -SqlServerFqdn sqlbe01.contoso.net -DatabasePathMap $pathmap
    ```
    
    Using the –DatabasePathMap parameter, you can define any logical drive letter mapping combination that provides the best solution for your SQL Server performance and placement requirements.

If you configure your database data files and log files by using the **DatabasePathMap** method, you will need to make a slight change to your normal process when using Topology Builder. Typically, you would define your topology choices, publish the topology, and choose to deploy the database selections.

If you have used **DatabasePathMap** you have already accomplished the third part of the Topology Builder process. In the case of having a completely configured database server in advance of running Topology Builder, you would still define all of your server roles and options, but deselect the option to create the databases.

</div>

</div>

<span> </span>

</div>

</div>

</div>

