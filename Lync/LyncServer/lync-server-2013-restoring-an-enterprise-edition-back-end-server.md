---
title: 'Lync Server 2013: Restoring an Enterprise Edition Back End Server'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Restoring an Enterprise Edition Back End Server
ms:assetid: 1450eb4e-3315-4d02-8f02-6e1791fb1550
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh202163(v=OCS.15)
ms:contentKeyID: 51541446
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Restoring an Enterprise Edition Back End Server in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-18_

Use the procedure described in this topic in the following two cases:

  - Both the primary and mirror databases of a mirrored Enterprise Edition Back End Server fail.

  - An Enterprise Edition Back End Server that is not mirrored fails.

If you have a mirrored Enterprise Edition Back End and only the mirror or primary database fails, see [Restoring a mirrored Enterprise Edition Back End Server in Lync Server 2013 - primary](lync-server-2013-restoring-a-mirrored-enterprise-edition-back-end-server-primary.md) for restoring the primary database, and [Restoring a mirrored Enterprise Edition Back End Server in Lync Server 2013 - mirror](lync-server-2013-restoring-a-mirrored-enterprise-edition-back-end-server-mirror.md) for restoring the mirror.

If the Central Management store fails, see [Restoring the server hosting the Central Management store in Lync Server 2013](lync-server-2013-restoring-the-server-hosting-the-central-management-store.md). If an Enterprise Edition member server that is not the Back End Server fails, see [Restoring an Enterprise Edition member server in Lync Server 2013](lync-server-2013-restoring-an-enterprise-edition-member-server.md).

<div>


> [!TIP]  
> We recommend that you take an image copy of the system before you start restoration. You can use this image as a rollback point, in case something goes wrong during restoration. You might want to take the image copy after you install the operating system and SQL Server, and restore or reenroll the certificates.



</div>

<div>

## To restore an Enterprise Edition Back End Server

1.  Start with a clean or new server that has the same fully qualified domain name (FQDN) as the failed computer, install the operating system, and then restore or reenroll the certificates.
    
    <div>
    

    > [!NOTE]  
    > Follow your organization's server deployment procedures to perform this step.

    
    </div>

2.  From a user account that is a member of the RTCUniversalServerAdmins group, log on to the server that you are restoring.

3.  Install SQL Server 2012 or SQL Server 2008 R2, keeping the instance names the same as before the failure.
    
    <div>
    

    > [!NOTE]  
    > Depending on your deployment, the Back End Server might include multiple collocated or separate databases. Follow the same procedure to install SQL Server that you used originally to deploy the server, including SQL Server permissions and logins.

    
    </div>

4.  After you install SQL Server, perform the following:
    
    1.  Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.
    
    2.  Click **Download Topology from existing deployment**, and then click **OK**.
    
    3.  Select the topology, and then click **Save**. Click **Yes** to confirm your selection.
    
    4.  Right-click the **Lync Server 2013** node, and then click **Publish Topology**.
    
    5.  Follow the **Publish the Topology** wizard. On the **Create databases** page, select the databases that you want to re-create.
        
        <div>
        

        > [!NOTE]  
        > Only stand-alone databases are displayed on the <STRONG>Create databases</STRONG> page.

        
        </div>
    
    6.  If you are restoring a Back End that was mirrored, continue to follow the rest of the wizard until the prompt **Create Mirror Database** appears. Select the database that you want to install, and complete the process.
    
    7.  Follow the rest of the wizard, and then click **Finish**.
    
    <div>
    

    > [!TIP]  
    > Instead of running Topology Builder, you can use the <STRONG>Install-CsDatabase</STRONG> cmdlet to create each database, and the <STRONG>Install-CsMirrorDatabase</STRONG> cmdlet to configure mirroring. For details, see the Lync Server Management Shell documentation.

    
    </div>

5.  Restore user data by performing the following:
    
    1.  Copy ExportedUserData.zip from $Backup\\ to a local directory.
    
    2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
    3.  Before you restore the user data, you must stop Lync services. To do so, type:
        
            Stop-CsWindowsService
    
    4.  To restore the user data, at the command line, type:
        
            Import-CsUserData -PoolFqdn <Fqdn> -FileName <String>
        
        For example:
        
            Import-CsUserData -PoolFqdn "atl0cs-001.litwareinc.com" -FileName "C:\Logs\ExportedUserDatal.zip"
    
    5.  Restart Lync Services by typing:
        
            Start-CsWindowsService

6.  If you deployed Response Group on this pool, restore the Response Group configuration data. For details, see [Restoring Response Group settings in Lync Server 2013](lync-server-2013-restoring-response-group-settings.md).

7.  If you are restoring a Back End Server that included Archiving or Monitoring databases, restore the Archiving or Monitoring data by using a SQL Server tool, such as SQL Server Management Studio. For details, see [Restoring monitoring or archiving data in Lync Server 2013](lync-server-2013-restoring-monitoring-or-archiving-data.md).

</div>

</div>

<span> </span>

</div>

</div>

</div>

