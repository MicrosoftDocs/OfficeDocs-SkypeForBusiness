---
title: Remove the SQL Server database for a Front End pool
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Remove the SQL Server database for a Front End pool
ms:assetid: 6bb932df-3ed7-49b6-ae17-61e4c6a5fe82
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688084(v=OCS.15)
ms:contentKeyID: 49733681
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove the SQL Server database for a Front End pool

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-04_

After you remove a Microsoft Lync Server 2010 Front End pool or reconfigure the pool to use a different database, you can remove the SQL Server databases that hosted the pool data. Use the following procedures to remove the definitions from Topology Builder, and then remove the database and log files from the database server.

<div>

## To remove the SQL Server database using Topology Builder

1.  From the Lync Server 2013 Front End Server, open Topology Builder and download the existing topology.

2.  In Topology Builder, navigate to **Shared Components** and then **SQL Server Stores**, right-click the SQL Server instance associated with the removed or reconfigured Front End pool, and then click **Delete**.

3.  Publish the topology, and then check the replication status.

</div>

<div>

## To remove user and application databases from the SQL Server

1.  To remove the databases on the SQL Server, you must be a member of the SQL Server sysadmins group for the SQL Server where you are removing the database files.

2.  Open Lync Server Management Shell

3.  To remove the database for the pool user store, type:
    
        Uninstall-CsDataBase -DatabaseType User -SqlServerFqdn <FQDN> [-SqlInstanceName <instance>]
    
    Where \<FQDN\> is the fully qualified domain name (FQDN) of the database server, and \<instance\> is the named database instance (that is, if one was defined).

4.  To remove the database for the pool application store, type:
    
        Uninstall-CsDataBase -DatabaseType Application -SqlServerFqdn <FQDN> [-SqlInstanceName <instance>]
    
    Where \<FQDN\> is the FQDN of the database server, and \<instance\> is the named database instance (that is, if one was defined).

5.  When the **Uninstall-CsDataBase** cmdlet prompts you to confirm actions, read the information, and then press **Y** (or press Enter) to proceed, or press **N** and then Enter if you want to stop the cmdlet (that is, in case there errors).

</div>

</div>

<span> </span>

</div>

</div>

</div>

