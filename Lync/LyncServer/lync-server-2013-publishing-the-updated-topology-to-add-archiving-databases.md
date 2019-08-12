---
title: 'Lync Server 2013: Publishing the updated topology to add Archiving databases'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Publishing the updated topology to add Archiving databases
ms:assetid: 454c68df-2ef5-4b5f-a44c-4eee02635d45
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204860(v=OCS.15)
ms:contentKeyID: 48184034
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Publishing the updated topology to add Archiving databases in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-01_

After updating your topology in Topology Builder, you must publish the topology to the Central Management store before you can configure and use Archiving. Read-only copies of the data are replicated to all servers in the topology to keep all servers in sync with topology and other configuration changes.

<div>

## To publish your updated topology

1.  On a computer that is running Lync Server 2013, or on which the Lync Server administrative tools are installed, log on using an account that is a member of the local Users group (or an account with equivalent user rights).
    
    <div>
    

    > [!NOTE]  
    > You can define a topology by using an account that is a member of the local Users group, but to publish a topology, which is required to add a server to the topology, you must use an account that is a member of the <STRONG>Domain Admins</STRONG> group and the <STRONG>RTCUniversalServerAdmins</STRONG> group, and that has full control permissions (that is, read, write, and modify) on the file share that you are using for the Lync Server 2013 file store (that is, so that Topology Builder can configure the required discretionary access control list (DACLs), or an account with equivalent rights.

    
    </div>

2.  Open the topology you created in the previous section using Topology Builder.

3.  In the console tree, right-click **Lync Server 2013**, and then click **Publish Topology**.

4.  On the **Publish the topology** page, click **Next**.

5.  On the **Create databases** page, verify that the database is selected, and then click **Next**.
    
    <div>
    

    > [!NOTE]  
    > If you do not have the appropriate permissions to create databases, you can cancel the selection of the database and someone with appropriate permissions can create the database. For details about the required administrator rights and permissions, see <A href="lync-server-2013-deployment-permissions-for-sql-server.md">Deployment permissions for SQL Server in Lync Server 2013</A> in the Deployment documentation.<BR>Only databases on dedicated SQL Server servers can be installed by using Topology Builder. Databases on SQL Server servers that are collocated with other server components must be installed by running local setup on that computer.

    
    </div>

6.  On the **Publishing wizard complete** page, verify that the topology was successfully published, and then click **Finish**.
    
    <div>
    

    > [!IMPORTANT]  
    > After publishing the topology, you must configure options and policies for Archiving before any content can be archived. For details, see <A href="lync-server-2013-configuring-support-for-archiving.md">Configuring support for Archiving in Lync Server 2013</A> in the Deployment documentation.

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

