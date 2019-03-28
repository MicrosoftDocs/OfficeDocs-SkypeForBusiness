---
title: 'Lync Server 2013: Hardening and protecting databases'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Hardening and protecting the databases of Lync Server 2013
ms:assetid: 6953e721-3511-4235-b848-51bab093dc89
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn518330(v=OCS.15)
ms:contentKeyID: 62625490
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Hardening and protecting the databases of Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-12-05_

Microsoft Lync Server 2013 also depends on SQL Server databases for storing user information, conference state, archiving data, and Call Detail Records (CDRs). You can maximize the availability of Lync Server 2013 data on Lync Server back-end databases, by partitioning the application data in a way that improves fault tolerance and simplifies troubleshooting. To achieve these goals, partition the application data by:

  - **Using server partitioning best practices**   Separate your operating system, application, and program files from your data files.

  - **Storing transaction log files and database files**   Store these files separately to increase fault tolerance and optimize recovery, and store them on an encrypted disk or volume.

  - **Using server clustering**   Cluster the back-end servers to optimize Lync Server 2013 system availability.

  - **Ensure that all data backups are encrypted and properly handled**   Lost, discarded, or misplaced backup media can pose a significant threat to data security for Lync Server 2013 deployments

On any Lync Server 2013 server except Standard Edition server, the SQL Server Express instance (RTCLOCAL instance) is not remotely accessible, and no local firewall exceptions are created, except for SQL Server Express on a Standard Edition server. On a Standard Edition server, both the back-end database and the Central Management store (CMS) are set up to be remotely accessible. To harden SQL Server databases, you can do the following:

  - Customize the SQL Server Express firewall on Standard Edition servers, limiting the scope of servers that can remotely access the database. By default, any IP address can remotely access the database.

  - Use SQL Server Configuration Manager to specify the protocols, IP addresses, and ports for SQL Server remote access:
    
      - Lync Server 2013 uses the TCP/IP protocol. It supports IP version 4 (IPv4), but not IP version 6 (IPv6).
        
        <div>
        

        > [!NOTE]  
        > Lync Server 2013 can function in a network with dual IP stack enabled.

        
        </div>
    
      - Lync Server 2013 supports multiple IP address (multi-homed network address cards). You can specify that SQL Server listen only to specific IP addresses (individual address or by subnet) and only use specific protocols.
    
      - Lync Server 2013 supports static and dynamic SQL Server ports.

  - Run SQL Server on a static (non-default) port, and do not run SQL Server Browser (so it cannot report the listening port to the client). This requires a custom configuration on each SQL Server client, including Front End Servers, Monitoring Server, Archiving Server, and administrative consoles (running Lync Server Management Shell, Lync Server Control Panel, or Topology Builder), and all other servers running Lync Server databases).

<div>


> [!NOTE]  
> Access to databases must be limited to trusted database administrators. A malicious database administrator could insert or modify data into the databases to acquire privileges over the Lync Server 2013 servers or obtain sensitive information from the services, even if the database administrator has not been granted direct access or control of the Lync Server 2013 servers.



</div>

For details about custom configurations and hardening SQL Server databases, see the NextHop blog article, "Using Lync Server 2010 with a Custom SQL Server Network Configuration," at [http://go.microsoft.com/fwlink/p/?LinkId=214008](http://go.microsoft.com/fwlink/p/?linkid=214008).

<div>


> [!NOTE]  
> You can also harden operating systems and applications servers, and you can use Group Policy to implement security lockdowns in your Lync Server deployment. For details, see <A href="lync-server-2013-hardening-and-protecting-servers-and-applications.md">Hardening and protecting servers and applications for Lync Server 2013</A>.



</div>

</div>

<span> </span>

</div>

</div>

</div>

