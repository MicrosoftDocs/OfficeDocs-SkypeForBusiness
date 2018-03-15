---
title: "Configure SQL Server clustering for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d7b52ef1-573c-48ed-bb94-34e37b49645c
description: "Microsoft Lync Server 2013 supports clustering for SQL Server 2012 and SQL Server 2008 R2. For details about what is supported, see Database software support in Lync Server 2013."
---

# Configure SQL Server clustering for Lync Server 2013
[]
Microsoft Lync Server 2013 supports clustering for SQL Server 2012 and SQL Server 2008 R2. For details about what is supported, see [Database software support in Lync Server 2013](database-software-support.md).
  
You should set up and configure the SQL Server cluster before you install and deploy the Enterprise Edition Front End Server and back-end database. For best practices and setup instructions for failover clustering in SQL Server 2012, see [https://technet.microsoft.com/en-us/library/hh231721.aspx](https://technet.microsoft.com/en-us/library/hh231721.aspx). For failover clustering in SQL Server 2008, see [https://technet.microsoft.com/en-us/library/ms189134(v=sql.105).aspx](https://technet.microsoft.com/en-us/library/ms189134%28v=sql.105%29.aspx).
  
When you install SQL Server, you should install SQL Server Management Studio to manage the locations for database and log file locations. SQL Server Management Studio is installed as an optional component when you install SQL Server.
  
> [!IMPORTANT]
> To install and deploy the databases on the SQL Server-based server, you must be a member of the SQL Server sysadmin group for the SQL Server-based server where you are installing the database files. If you are not a member of the SQL Server sysadmin group, you will need to request that you be added to the group until the database files are deployed. If you cannot be made a member of the sysadmin group, you should provide your SQL Server database administrator with the script to configure and deploy the databases. For details about the proper user rights and permissions that you need to accomplish the procedures, see [Deployment permissions for SQL Server in Lync Server 2013](deployment-permissions-for-sql-server.md). 
  
### To configure SQL Server clustering

1. After you have completed the installation and configuration of SQL Server clustering, you define the SQL Server store in Topology Builder by using the SQL Server instance virtual cluster name (as configured in the setup for SQL Server clustering) and the instance name of the SQL Server database. Different from a single SQL Server-based server, you will use the virtual node fully qualified domain name (FQDN) for a clustered SQL Server-based server.
    
    > [!NOTE]
    > The individual Windows Server cluster nodes do not have to be configured for Topology Builder. You will use only the virtual SQL Server cluster name. 
  
2. If you are using Topology Builder to deploy your databases, you must be a member of the SQL Server sysadmin group. If you are a member of the SQL Server sysadmin group, but you do not have privileges in the domain (for example, a SQL Server database administrator role), then you have the rights to create the databases but not to read necessary information in Lync Server. For details about the user rights and permissions necessary to deploying Lync Server, see [Deployment permissions for SQL Server in Lync Server 2013](deployment-permissions-for-sql-server.md).
    
3. Ensure that the database folder and log files folder defaults are mapped correctly to the shared disks in the SQL Server cluster by using SQL Server Management Studio. This is a required procedure if you will create databases by using Topology Builder.
    
    > [!NOTE]
    > If you did not install SQL Server Management Studio, you can install it by rerunning the SQL Server installation, and then selecting the management tool as an added feature for the existing SQL Server deployment. 
  
4. Install the databases for the SQL Server-based server by using either Topology Builder or Windows PowerShell cmdlets. To use Topology Builder, use the following procedure. To use Windows PowerShell cmdlets, see [Database installation using Lync Server Management Shell in Lync Server 2013](database-installation-using-lync-server-management-shell.md).
    
### To create databases using Topology Builder

1. Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.
    
    > [!CAUTION]
    > The following procedure assumes that you have defined and configured your topology in Topology Builder. For details about defining your topology, see[Defining and configuring the topology in Lync Server 2013](defining-and-configuring-the-topology.md). To use Topology Builder to publish the topology and configure the database, you must log on as a user with the correct user rights and group memberships. For details about the required rights and group memberships, see [Deployment permissions for SQL Server in Lync Server 2013](deployment-permissions-for-sql-server.md). 
  
2. In Topology Builder, as you publish the topology, on the **Create databases** page, click **Advanced**.
    
3. The **Select Database File Location** page has two options that determine how the database files will be deployed to the SQL Server cluster. Select one of the following: 
    
  - **Automatically determine the database file location.** This selection uses an algorithm to determine the database log and data file locations based on the drive configuration on the SQL Server-based server. The files will be distributed in such a way as to attempt to provide optimal performance. 
    
  - Use SQL Server instance defaults. Selecting this option will install the log and data files according to the SQL Server instance settings. After deployment of the database files to the SQL Server, your SQL Server database administrator may want to relocate the files to optimize performance for your particular SQL Server configuration requirements. 
    
4. Complete the publishing of the topology and confirm that there were no errors during the operation.
    

