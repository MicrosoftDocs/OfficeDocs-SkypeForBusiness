---
title: 'Lync Server 2013: Add Persistent Chat Server to the topology'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Add Persistent Chat Server to the topology
ms:assetid: 8389b307-8c17-4e45-b3b5-5dc9fcfc2ffb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205049(v=OCS.15)
ms:contentKeyID: 48184682
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Add Persistent Chat Server to the topology in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-06_

You must incorporate Lync Server 2013, Persistent Chat Server support in your topology before you can configure your deployment to support Persistent Chat Server. The information in this topic describes how to use Topology Builder to add Persistent Chat Server support to your existing topology.

<div>

## To add Persistent Chat Server to a topology

Perform the following steps for installing a single Persistent Chat Server pool without a disaster recovery configuration. For configuring a stretched Persistent Chat Server pool for high availability and disaster recovery, see [Configuring Persistent Chat Server for high availability and disaster recovery in Lync Server 2013](lync-server-2013-configuring-persistent-chat-server-for-high-availability-and-disaster-recovery.md) in the Deployment documentation.

To deploy multiple Persistent Chat Server pools, repeat the same process for each pool.

1.  On a computer that is running Lync Server 2013 or on which the Lync Server administrative tools are installed, log on using an account that is a member of the local Users group (or an account with equivalent user rights).
    
    <div>
    

    > [!NOTE]  
    > You can define a topology by using an account that is a member of the local Users group, but to publish a topology, which is required to install a Lync Server 2013 server, you must use an account that is a member of the <STRONG>Domain Admins</STRONG> group and the <STRONG>RTCUniversalServerAdmins</STRONG> group, and that has full control permissions (that is, read, write, and modify) on the file store that you are going to use for the Persistent Chat Server file store (that is, so that Topology Builder can configure the required DACLs), or an account with equivalent rights.

    
    </div>

2.  Start Topology Builder.

3.  In the console tree, navigate to the **Persistent Chat Pools** node and expand it to select a Persistent Chat Server pool, or right-click the node and select **New Persistent Chat Pool**. You must define the pool’s fully qualified domain name (FQDN), and indicate whether the pool will be a single-server pool or multiple-server pool deployment.
    
    You can choose a **Multiple Computer Pool** or a **Single Computer Pool**. Choose the former if you are planning to have more than one Persistent Chat Server Front End Server in your Persistent Chat Server pool. Make this choice now, or at a later point, because after you create a single computer pool, you cannot add additional servers to it later. If you choose a multiple computer pool, enter the names of the individual Persistent Chat Server Front End Servers that comprise the pool.
    
    <div>
    

    > [!IMPORTANT]  
    > If the Persistent Chat Server role is being installed on a Lync Server 2013&nbsp;Standard Edition server, the FQDN needs to match the FQDN of the Standard Edition server.

    
    </div>

4.  Define a simple **Display Name** for the Persistent Chat Server pool. The display name can be used by custom clients, particularly when there are multiple Persistent Chat Server pools, to differentiate rooms.

5.  Define the port used by the Persistent Chat Server to communicate with Lync Server Front End Servers. The default port is 5041.

6.  If your organization requires compliance support, select the **Enable compliance** check box. If chosen, the Persistent Chat Server Compliance service is installed on the same computer as the Persistent Chat Server Front End Server. You are prompted to select a SQL Server Back End Server for Persistent Chat Server Compliance later.

7.  Assign site affinity for the Persistent Chat Server pool. Select the **Use this pool as default for site \<SiteName\>** check box or **Use this pool as default for all sites** to designate this Persistent Chat Server pool as the default pool for the current site or all sites. When the Lync 2013 client is used to create and manage rooms, the default pool associated with the user’s site is used by the room creation and management experience so that it can route room creation and management operations to that pool. This only applies when you have multiple Persistent Chat Server pools deployed, and want to use the room creation and management features of Persistent Chat Server.
    
    <div>
    

    > [!IMPORTANT]  
    > You can customize the room creation and management features using the Persistent Chat Server Software Development Kit (SDK).<BR>For details about how to configure SQL Server backup databases for disaster recovery, see <A href="lync-server-2013-configuring-persistent-chat-server-for-high-availability-and-disaster-recovery.md">Configuring Persistent Chat Server for high availability and disaster recovery in Lync Server 2013</A> in the Deployment documentation.

    
    </div>

8.  Define the **SQL store for the Persistent Chat Server Back End (where chat room content is stored)** by doing one of the following:
    
      - To use an existing SQL Server database, in the drop-down list, click the name of the SQL Server database that you want to use.
    
      - To specify a new SQL Server database, click **New**, and in **Define New SQL Store**, perform the following:
    
    <!-- end list -->
    
      - In **SQL Server FQDN**, specify the FQDN of the SQL Server on which you want to create the new SQL Server database.
    
      - Either select **Default Instance** to use the default instance or, to specify a different instance, select **Named Instance**, and specify the instance that you want to use.

9.  Define the SQL Server compliance database if you enabled Compliance.
    
    <div>
    

    > [!IMPORTANT]  
    > For details about how to configure SQL Server mirrors for high availability for the Persistent Chat Server database and the Persistent Chat Server compliance database, see <A href="lync-server-2013-configuring-persistent-chat-server-for-high-availability-and-disaster-recovery.md">Configuring Persistent Chat Server for high availability and disaster recovery in Lync Server 2013</A> in the Deployment documentation.

    
    </div>

10. Define the file store. A file store is a folder where a copy of any file uploaded to the file repository is stored (for example, storing file attachments posted to a chat room). In the case of a multiple-server Persistent Chat Server topology, this must be a Universal Naming Convention (UNC) path; and for a single-server Persistent Chat Server topology, it can be a local file path.
    
    To use an existing file store, perform the following steps:
    
      - In **File Server FQDN**, specify the FQDN of the file store on which you want to create the new file store.
    
      - In **File Share**, specify the file store that you want to use.
    
    <div>
    

    > [!IMPORTANT]  
    > You can define the file store in Topology Builder before you create the file store, but you must create the file store in the defined location you define before you publish the topology.

    
    </div>

11. Select the Front End Server pool to be used as a next hop for this Persistent Chat Server pool. This is the Front End Server pool that will be able to route Persistent Chat Server requests to this pool.

12. To save the configuration, click **Finish**. The Persistent Chat Server pool appears in Topology Builder accompanied by your specific pool settings.
    
    To now publish your updated topology to which you’ve Persistent Chat Server, see [Publish the updated topology in Lync Server 2013](lync-server-2013-publish-the-updated-topology.md) in the Deployment documentation.
    
    <div>
    

    > [!NOTE]  
    > With Topology Builder already open, you can proceed to step 3 in <A href="lync-server-2013-publish-the-updated-topology.md">Publish the updated topology in Lync Server 2013</A> to begin publishing your updated topology.

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

