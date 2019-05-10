---
title: 'Restoring a mirrored Enterprise Edition Back End Server - primary'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Restoring a mirrored Enterprise Edition Back End Server - primary
ms:assetid: bc555b46-70c5-4eee-ae91-e195df238293
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945648(v=OCS.15)
ms:contentKeyID: 51541512
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Restoring a mirrored Enterprise Edition Back End Server in Lync Server 2013 - primary

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-17_

If you have an Enterprise Edition Back End Server in a mirrored configuration and only the primary database fails, follow the procedures in this section. If both the primary database and mirror fail, see [Restoring an Enterprise Edition Back End Server in Lync Server 2013](lync-server-2013-restoring-an-enterprise-edition-back-end-server.md). If only the mirror fails, see [Restoring a mirrored Enterprise Edition Back End Server in Lync Server 2013 - mirror](lync-server-2013-restoring-a-mirrored-enterprise-edition-back-end-server-mirror.md). If the database hosting the Central Management store fails, see [Restoring the server hosting the Central Management store in Lync Server 2013](lync-server-2013-restoring-the-server-hosting-the-central-management-store.md). If an Enterprise Edition member server that is not the Back End Server fails, see [Restoring an Enterprise Edition member server in Lync Server 2013](lync-server-2013-restoring-an-enterprise-edition-member-server.md).

We recommend that you take an image copy of the system before you start restoration. You can use this image as a rollback point, in case something goes wrong during restoration. You might want to take the image copy after you install the operating system and SQL Server, and restore or reenroll the certificates.

In this topic, the example primary database will have a fully qualified domain name (FQDN) of BE1.contoso.com, and the mirror database will have an FQDN of BE2.contoso.com.

<div>

## To restore an Enterprise Edition Back End Server Primary Database

1.  From a user account that is a member of the RTCUniversalServerAdmins group, log on to a Front End Server.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Force all of the configured databases to fail over to the Mirror. For each of the database types that you have configured on this server, type the following cmdlet:
    
        Invoke-CsDataBaseFailover -PoolFqdn <Pool FQDN> -DatabaseType <Configured Database Type> -NewPrincipal Mirror -Force -Verbose
    
    For example:
    
        Invoke-CsDataBaseFailover -PoolFqdn pool0.vdomain.com -DatabaseType User -NewPrincipal Mirror -Force -Verbose
    
    <div>
    

    > [!WARNING]
    > If you have configured your back-end database to use synchronized mirroring with a witness, failover is automatic.

    
    </div>

4.  After completing failover, perform the following:
    
      - Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.
    
      - Disable mirroring on the Back End Server: Right-click on the pool under **Enterprise Edition Front End pools** and select **Edit Properties**. On the **General** tab, under **Associations**, clear the **Enable SQL Server store mirroring** check box. Do this for Archiving and Monitoring as necessary. Then click **OK**.
    
      - Right-click the Lync Server 2013 node, click **Topology**, and then click **Publish**.
    
      - Select the still functioning backend (BE2.contoso.com) to be the new SQL store. To do this, right-click on the pool under **Enterprise Edition Front End pools** and select **Edit Properties**. On the **General** tab, under **Associations**, type the FQDN of the functioning backend in the **SQL Server store** field (in our example, BE2.contoso.com).
    
      - Right-click the Lync Server 2013 node, click **Topology**, and then click **Publish**.
    
      - Restart services so that each server can read the new topology. From a Lync Server Management Shell, run the following cmdlets on each Front End Server that belongs to this pool:
        
            Stop-CsWindowsService
            Start-CsWindowsService

5.  Uninstall mirroring. From a Lync Server Management Shell, run the following cmdlet:
    
        Uninstall-CsMirrorDatabase -DatabaseType User -SqlServerFqdn <MirrorServerFqdn> -SqlInstanceName <SQLInstance> -verbose
    
    For example:
    
        Uninstall-CsMirrorDatabase -DatabaseType User -SqlServerFqdn DB2.contoso.com -SqlInstanceName rtc -verbose
    
    Do this for all database types on this server.

6.  Create a clean or new server that has the same FQDN (in this example, DB1.contoso.com) as the failed computer, install the operating system, and then restore or reenroll the certificates. This server will function as the new mirror.

7.  From a user account that is a member of the RTCUniversalServerAdmins group, log on to the new server.

8.  Install SQL Server 2012 or SQL Server 2008 R2, keeping the instance names the same as before the failure.

9.  From a user account that is a member of the RTCUniversalServerAdmins group, log on to a Front End Server.

10. Use Topology Builder to install mirror DB. Perform the following steps:
    
      - Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.
    
      - Enable mirroring on the Back End Server. To do so, right-click on the pool under **Enterprise Edition Front End pools** and select **Edit Properties**. On the **General** tab, under **Associations**, select the **Enable SQL Server store mirroring** check box. Also do this for Archiving and Monitoring, if necessary.
        
        Then, in the **Mirroring SQL Server store** field, type the FQDN of the new server (n this example, BE1.contoso.com). Then click **OK**.
    
      - Right-click the Lync Server 2013 node, click **Topology**, and then click **Install Database**.
    
      - Follow the **Install Database** wizard. On the **Create databases** page, select the databases that you want to recreate.
    
      - Follow the wizard until you come to the prompt, **Create Mirror Database**. Select the database that you want to install, and complete this process.

</div>

</div>

<span> </span>

</div>

</div>

</div>

