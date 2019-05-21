---
title: "Deploy SQL mirroring for Back End Server high availability in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 70224520-b5c8-4940-a08e-7fb9b1adde8d
description: "To be able to deploy SQL mirroring, your servers must run a minimum of SQL Server 2008 R2. This version must run on all the involved servers: the primary, mirror, and the witness. For details, see Cumulative update package 9 for SQL Server 2008 Service Pack 1 ."
---

# Deploy SQL mirroring for Back End Server high availability in Skype for Business server 2015


To be able to deploy SQL mirroring, your servers must run a minimum of SQL Server 2008 R2. This version must run on all the involved servers: the primary, mirror, and the witness. For details, see [Cumulative update package 9 for SQL Server 2008 Service Pack 1 ](https://go.microsoft.com/fwlink/p/?linkid=3052&amp;kbid=2083921).

In general, setting up SQL mirroring between the two Back End Servers with a witness requires the following:

- The primary server's version of SQL Server must support SQL mirroring.

- The primary, mirror, and the witness (if deployed) must have the same version of SQL Server.

- The primary and the mirror must have the same edition of SQL Server. The witness may have a different edition.

For SQL best practices in terms of what SQL versions are supported for a Witness role, see [Database Mirroring Witness](https://go.microsoft.com/fwlink/p/?LinkId=247345).

You use Topology Builder to deploy SQL mirroring. You select an option in Topology Builder to mirror the databases, and Topology Builder sets up the mirroring (including setting up a witness, if you want) when you publish the topology. Note that you set up or remove the witness at the same time you set up or remove the mirror. There is no separate command to deploy or remove only a witness.

To configure server mirroring, you must first set up SQL database permissions correctly. For details, see [Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=268454).

With SQL mirroring, database recovery mode is always set to **Full**, which means you must closely monitor transaction log size and back up transaction logs on a regular basis to avoid running out of disk space on the Back End Servers. The frequency of transaction log backups depends on the log growth rate, which in turn depends on database transactions incurred by user activities on the Front End pool. We recommend that you determine how much transaction log growth is expected for your deployment workload so that you can do the planning accordingly. The following articles provide additional information on SQL backup and log management:

- [Database recovery models](https://go.microsoft.com/fwlink/p/?LinkId=268446)

- [Backup overview](https://go.microsoft.com/fwlink/p/?LinkId=268449)

- [Backup transaction log](https://go.microsoft.com/fwlink/p/?LinkId=268452)

With SQL mirroring, you can either configure the topology for mirroring when you create the pools, or after the pools are already created.

> [!IMPORTANT]
> Using Topology Builder or cmdlets to set up and remove SQL mirroring is supported only when the primary, mirror, and witness (if desired) servers all belong to the same domain. If you want to set up SQL mirroring among servers in different domains, see your SQL Server documentation.

> [!IMPORTANT]
> Whenever you make a change to a Back End Database mirroring relationship, you must restart all the Front End Servers in the pool. > For a change in mirroring, (such as changing the location of a mirror), you must use Topology Builder to perform these three steps:

1. Remove mirroring from the old mirror server.

2. Add mirroring to the new mirror server.

3. Publish the topology.

> [!NOTE]
> A file share has to be created for the mirror files to be written to, and the service that SQL Server and SQL Agent are running under needs read/write access. If the SQL Server service is running under the context of Network Service, you can add \<Domain\>\\<SQLSERVERNAME\>$ of both the Principal and Mirror SQL Servers to the share permissions. The $ is important to identify that this is a computer account.

## To configure SQL mirroring while creating a pool in Topology Builder

1. On the **Define the SQL Store** page, click **New** next to the **SQL store** box.

2. On the **Define new SQL Store** page, specify the primary store, select **This SQL instance is in mirroring relation**, specify the SQL mirroring port number (the default is 5022), and then click **OK**.

3. Back on the **Define the SQL store** page, select **Enable SQL Store mirroring**.

4. In the **Define new SQL Store** page, specify the SQL store to be used as the mirror. Select **This SQL instance is in mirroring relation**, specify the port number (the default is 5022), and then click **OK**.

5. If you want a witness for this mirror, do the following:

    a. Select **Use SQL mirroring witness to enable automatic failover**.

    b. In the **Define the SQL Store** page, select **Use SQL mirroring witness to enable automatic failover**, and specify the SQL store to be used as the witness.

    c. Specify the port number (the default is 7022) and click **OK**.

6. After you are done defining your Front End pool and all other roles in your topology, use Topology Builder to publish the topology. When the topology is published, if the Front End pool that hosts Central Management store has SQL mirroring enabled, you will see an option to create both primary and mirror SQL store databases.

    Click **Settings**, and type the path to use as the file share for the mirroring backup.

    Click **OK** and then **Next** to create the databases and publish the topology. The mirroring and the witness (if specified) will be deployed.

You can use Topology Builder to edit the properties of an already existing pool to enable SQL mirroring.

## To add SQL mirroring to an existing Front End pool in Topology Builder

1. In Topology Builder, right-click the pool and then click **Edit Properties**.

2. Select **Enable SQL Store Mirroring**, and then click **New** next to **Mirroring SQL Store**.

3. Specify the SQL store that you want to use as the mirror.

4. Select **This SQL instance is in mirroring relation**, specify the SQL mirroring port number the default port is 5022), and then click **OK**.

5. If you want to configure a witness, select **Use SQL mirroring witness to enable automatic failover**, and click **New**.

6. Specify the SQL store that you want to use as the witness.

7. Select **This SQL instance is in mirroring relation**, specify the SQL mirroring port number (the default port is 7022), and then click **OK**.

8. Click **OK**.

9. Publish the topology. When you do so, you will be prompted to install the database.

    During the topology publishing process, you will be asked to define a file share path. The SQL Servers that participate in the mirroring must have read/write access to this file share for the mirror to be established.

You must then install the database before going on to the next procedure.

You should keep the following in mind when setting up SQL mirroring:

- If a mirroring endpoint already exists, it will be reused using the ports defined there, and will ignore the ones you specify in the topology.

- Any port already allocated for other applications on the same server, including those for other SQL instances, should not be used for the installed SQL instances at hand. This implies that if you have more than one SQL instance installed on the same server, they must not use the same port for mirroring. For details, see the following articles:

  - [Specify a Server Network Address (Database Mirroring)](https://go.microsoft.com/fwlink/p/?LinkId=247346)

  - [The Database Mirroring Endpoint (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=247347)

## Using Skype for Business Server 2015 Management Shell Cmdlets to Set Up SQL Mirroring

The easiest way to set up mirroring is by using Topology Builder, but you can also do so using cmdlets.

1. Open a Skype for Business Server 2015 Management Shell window and run the following cmdlet:

   ```
   Install-CsMirrorDatabase [-ConfiguredDatabases] [-ForInstance] [-ForDefaultInstance] [-DatabaseType <Application | Archiving | CentralMgmt | Monitoring | User | BIStaging | PersistentChat | PersistentChatCompliance >] -FileShare <fileshare> -SqlServerFqdn <primarySqlserverFqdn> [-SqlInstanceName] [-DatabasePathMap] [-ExcludeDatabaseList] [-DropExistingDatabasesOnMirror] -Verbose
   ```

    For example:

   ```
   Install-CsMirrorDatabase -ConfiguredDatabases -FileShare \\PRIMARYBE\csdatabackup -SqlServerFqdn primaryBE.contoso.com -DropExistingDatabasesOnMirror -Verbose
   ```

    You will see the following:

   <pre>
   Database Name:rtcxds
        Data File:D:\CsData\BackendStore\rtc\DbPath\rtcxds.mdf
         Log File:D:\CsData\BackendStore\rtc\LogPath\rtcxds.ldf
      Primary SQL: e04-ocs.los_a.lsipt.local\rtc
          Account: LOS_A\e04-ocs$
       Mirror SQL: K16-ocs.los_a.lsipt.local\rtc
          Account: LOS_A\K16-ocs$
     Witness SQL : AB14-lct.los_a.lsipt.local\rtc
          Account: LOS_A\AB14-lct$
    Database Name:rtcshared
        Data File:D:\CsData\BackendStore\rtc\DbPath\rtcshared.mdf
         Log File:D:\CsData\BackendStore\rtc\LogPath\rtcshared.ldf
      Primary SQL: e04-ocs.los_a.lsipt.local\rtc
          Account: LOS_A\e04-ocs$
       Mirror SQL: K16-ocs.los_a.lsipt.local\rtc
          Account: LOS_A\K16-ocs$
     Witness SQL : AB14-lct.los_a.lsipt.local\rtc
          Account: LOS_A\AB14-lct$
    Database Name:rtcab
        Data File:D:\CsData\ABSStore\rtc\DbPath\rtcab.mdf
         Log File:D:\CsData\ABSStore\rtc\LogPath\rtcab.ldf
      Primary SQL: e04-ocs.los_a.lsipt.local\rtc
          Account: LOS_A\e04-ocs$
       Mirror SQL: K16-ocs.los_a.lsipt.local\rtc
          Account: LOS_A\K16-ocs$
     Witness SQL : AB14-lct.los_a.lsipt.local\rtc
          Account: LOS_A\AB14-lct$
    Database Name:rgsconfig
        Data File:D:\CsData\ApplicationStore\rtc\DbPath\rgsconfig.mdf
         Log File:D:\CsData\ApplicationStore\rtc\LogPath\rgsconfig.ldf
      Primary SQL: e04-ocs.los_a.lsipt.local\rtc
          Account: LOS_A\e04-ocs$
       Mirror SQL: K16-ocs.los_a.lsipt.local\rtc
          Account: LOS_A\K16-ocs$
     Witness SQL : AB14-lct.los_a.lsipt.local\rtc
          Account: LOS_A\AB14-lct$
    Database Name:rgsdyn
        Data File:D:\CsData\ApplicationStore\rtc\DbPath\rgsdyn.mdf
         Log File:D:\CsData\ApplicationStore\rtc\LogPath\rgsdyn.ldf
      Primary SQL: e04-ocs.los_a.lsipt.local\rtc
          Account: LOS_A\e04-ocs$
       Mirror SQL: K16-ocs.los_a.lsipt.local\rtc
          Account: LOS_A\K16-ocs$
     Witness SQL : AB14-lct.los_a.lsipt.local\rtc
          Account: LOS_A\AB14-lct$
    Database Name:cpsdyn
        Data File:D:\CsData\ApplicationStore\rtc\DbPath\cpsdyn.mdf
         Log File:D:\CsData\ApplicationStore\rtc\LogPath\cpsdyn.ldf
      Primary SQL: e04-ocs.los_a.lsipt.local\rtc
          Account: LOS_A\e04-ocs$
       Mirror SQL: K16-ocs.los_a.lsipt.local\rtc
          Account: LOS_A\K16-ocs$
     Witness SQL : AB14-lct.los_a.lsipt.local\rtc
          Account: LOS_A\AB14-lct$
    Database Name:xds
        Data File:D:\CsData\CentralMgmtStore\rtc\DbPath\xds.mdf
         Log File:D:\CsData\CentralMgmtStore\rtc\LogPath\xds.ldf
      Primary SQL: e04-ocs.los_a.lsipt.local\rtc
          Account: LOS_A\e04-ocs$
       Mirror SQL: K16-ocs.los_a.lsipt.local\rtc
          Account: LOS_A\K16-ocs$
     Witness SQL : AB14-lct.los_a.lsipt.local\rtc
          Account: LOS_A\AB14-lct$
    Database Name:lis
        Data File:D:\CsData\CentralMgmtStore\rtc\DbPath\lis.mdf
         Log File:D:\CsData\CentralMgmtStore\rtc\LogPath\lis.ldf
      Primary SQL: e04-ocs.los_a.lsipt.local\rtc
          Account: LOS_A\e04-ocs$
       Mirror SQL: K16-ocs.los_a.lsipt.local\rtc
          Account: LOS_A\K16-ocs$
     Witness SQL : AB14-lct.los_a.lsipt.local\rtc
          Account: LOS_A\AB14-lct$
   [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
   </pre>

2. Verify the following:

    - Port 5022 is accessible through the firewall if Windows Firewall is enabled in the primary SQL Server e04-ocs.los_a.lsipt.local\rtc.

    - Port 5022 is accessible through the firewall if Windows Firewall is enabled in the mirror SQL Server K16-ocs.los_a.lsipt.local\rtc.

    - Port 7022 is accessible through the firewall if Windows Firewall is enabled in the witness SQL Server AB14-lct.los_a.lsipt.local\rtc.

   - Accounts running the SQL Servers on all primary and mirror SQL servers have read/write permission to the file share \\E04-OCS\csdatabackup

   - Verify that the Windows Management Instrumentation (WMI) provider is running on all these servers. The cmdlet uses this provider to find the account information for SQL Server services running on all primary, mirror and witness servers.

   - Verify that the account running this cmdlet has permission to create the folders for the data and log files for all the mirror servers.

   - Note that the user account that the SQL instance uses to run must have read/write permission to the file share. If the file share is on a different server, and the SQL instance runs a local system account, you must grant file share permissions to the server that hosts the SQL instance.

3. Type A and press ENTER.

    The mirroring will be configured.

    **Install-CsMirrorDatabase** installs the mirror and configures mirroring for all the databases that are present on the primary SQL store. If you want to configure mirroring for only specific databases, you can use the -DatabaseType option, or if you want to configure mirroring for all databases except for a few, you can use the -ExcludeDatabaseList option, along with a comma-separated list of database names to exclude.

    For example, if you add the following option to **Install-CsMirrorDatabase**, all databases except rtcab and rtcxds will be mirrored.

    `-ExcludeDatabaseList rtcab,rtcxds`

   For example, if you add the following option to **Install-CsMirrorDatabase**, only the rtcab, rtcshared, and rtcxds databases will be mirrored.

    `-DatabaseType User`

## Removing or Changing SQL Mirroring

To remove the SQL mirroring of a pool in Topology Builder, you must first use a cmdlet to remove the mirror in SQL Server. You can then use Topology Builder to remove the mirror from the topology. To remove the mirror in SQL Server, use the following cmdlet:

```
Uninstall-CsMirrorDatabase -SqlServerFqdn <SQLServer FQDN> [-SqlInstanceName <SQLServer instance name>] -DatabaseType <Application | Archiving | CentralMgmt | Monitoring | User | BIStaging | PersistentChat | PersistentChatCompliance> [-DropExistingDatabasesOnMirror] [-Verbose]
```

For example, to remove mirroring and drop the databases for the User databases, type the following:

```
Uninstall-CsMirrorDatabase -SqlServerFqdn primaryBE.contoso.com -SqlInstanceName rtc -Verbose -DatabaseType User -DropExistingDatabasesOnMirror
```

The  `-DropExistingDatabasesOnMirror` option causes the affected databases to be deleted from the mirror.

Then, to remove the mirror from the topology, do the following:

1. In Topology Builder, right-click the pool and click **Edit Properties**.

2. Uncheck **Enable SQL Store Mirroring** and click **OK**.

3. Publish the topology.

## Removing a Mirroring Witness

Use this procedure if you need to remove the witness from a Back End Server mirroring configuration.

1. In Topology Builder, right-click the pool and click **Edit Properties**.

2. Uncheck **Use SQL Server mirroring witness to enable automatic failover** and click **OK**.

3. Publish the topology.

    After publishing the topology, Topology Builder you will see a message that includes the following

   ```
   Run the Uninstall-CsMirrorDatabase cmdlet to remove databases that are paired with following primary databases.
   ```

    However, do not follow that step, and do not type  `Uninstall-CsMirrorDatabase` as that would uninstall the entire mirroring configuration.

4. To remove just the witness from the SQL Server configuration, follow the instructions in [Remove the Witness from a Database Mirroring Session (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=268456).


