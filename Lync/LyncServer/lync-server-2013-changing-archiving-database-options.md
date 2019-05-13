---
title: 'Lync Server 2013: Changing Archiving database options'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Changing Archiving database options
ms:assetid: 3775f09d-65b0-48bc-8a4d-d97bd0c3423c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204814(v=OCS.15)
ms:contentKeyID: 48183879
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Changing Archiving database options in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

If you deploy Archiving using SQL Server storage for archiving storage for any of your users, you can make the following database storage changes:

  - Use a different SQL Server database for archiving storage. This includes the primary Archiving database and any database you use for SQL Server mirroring.

  - Switch to Microsoft Exchange integration to store archiving data and files on Exchange 2013 servers. If all your users are homed on your Exchange 2013 servers and you want to use Microsoft Exchange storage for all users in your deployment, you should remove the SQL Server store databases from your topology.

To make either of these changes, you must run Topology Builder, make the changes, and then publish the topology again. You can use Topology Builder to do this. Do not specify **Archiving SQL Server store** or **Enable SQL Server store mirroring** information, unless you have Lync users who are not homed on Exchange 2013 servers.

<div>

## To change your archiving database option

1.  On a computer that is running Lync Server 2013, or on which the Lync Server administrative tools are installed, log on by using an account that is a member of the local Users group (or an account with equivalent user rights).
    
    <div>
    

    > [!NOTE]  
    > You can define a topology by using an account that is a member of the local Users group, but to publish a topology, which is required to add a component to the topology, you must use an account that is a member of the <STRONG>Domain Admins</STRONG> group and the <STRONG>RTCUniversalServerAdmins</STRONG> group, and that has full control permissions (that is, read, write, and modify) on the file share that you are using for the Lync Server 2013 file store (that is, so that Topology Builder can configure the required discretionary access control lists (DACLs), or an account with equivalent rights.

    
    </div>

2.  Start Topology Builder.

3.  In the console tree, navigate to the Front End pool in which you deployed Archiving, and then click the name of the Front End pool where you want to change the database options.

4.  In the **Action** menu, click **Edit Properties**.

5.  In the **Edit Properties** dialog box, click **General**.

6.  Scroll down to **Archiving**.

7.  In **Archiving**, do the following:
    
      - To change to a different existing SQL Server store, under **Archiving SQL Server store**, in the drop-down list box, do the following:
        
          - To use an existing SQL Server store, in the drop-down list box, click the name of the SQL Server store that you want to use.
        
          - To specify a new SQL Server store, click **New**, and then in the **Define New SQL Server store** dialog box, do the following:
            
              - To use an existing SQL Server store, in the drop-down list box, click the name of the SQL Server store that you want to use.
            
              - To specify a new SQL Server store, click **New**, and then in the **Define New SQL Server Store** dialog box, do the following:
                
                  - In **SQL Server FQDN**, specify the FQDN of the server on which you want to create the new SQL Server store.
                
                  - Either click **Default Instance** to use the default instance, or, to specify a different instance, click **Named instance**, and then specify the instance you want to use.
                
                  - If the specified SQL Server instance is in a mirroring relationship, select the **This SQL instance is in mirroring relation** check box, and then, in **Mirror port number**, specify the port number.
    
      - To add SQL Server store for mirroring or change to a different existing SQL Server store for SQL Server store mirroring, select **Enable SQL Server store mirroring**, and then do the following:
        
          - To use an existing SQL Server store for mirroring, in the **Archiving SQL Server store mirror** drop-down list box, click the name of the SQL Server store that you want to use for mirroring.
        
          - To specify a new SQL Server store for mirroring, click **New**, and then in the **Define New SQL Server Store** dialog box, do one of the following:
            
            1.  In **SQL Server FQDN**, specify the FQDN of the SQL Server on which you want to create the new SQL Server store.
            
            2.  Either click **Default Instance** to use the default instance, or, to specify a different instance, click **Named Instance**, and then specify the instance you want to use.
            
            3.  If the specified SQL Server instance is in a mirroring relationship, select the **This SQL instance is in mirroring relation** check box, and then, in **Mirror port number**, specify the port number.
        
          - If you enable SQL Server mirroring and want to add or change a SQL Server mirroring witness (a third, separate SQL Server instance that can detect the health of the primary SQL Server server and mirror instances), select the **Use SQL Server mirroring witness to enable automatic failover** check box, and then do one of the following:
            
            1.  In **SQL Server FQDN**, specify the FQDN of the server on which you want to create the new SQL Server mirroring witness.
            
            2.  Either click **Default Instance** to use the default instance, or, to specify a different instance, click **Named Instance**, and then specify the instance you want to use for the mirroring witness.
            
            3.  If the specified SQL Server instance is in a mirroring relationship, select the **This SQL instance is in mirroring relation** check box, and then, in **Mirror port number**, specify the port number.
    
      - To switch to Microsoft Exchange integration to store archiving data and files on Exchange 2013 servers (if all users in your deployment are homed on your Exchange 2013 servers), delete all information for Archiving databases.
    
    <div>
    

    > [!IMPORTANT]  
    > If you have any Lync users who are not homed on Exchange 2013 servers, do not delete the SQL Server store information.

    
    </div>

8.  To save the configuration, click **OK**.
    
    <div>
    

    > [!IMPORTANT]  
    > The changes you make in Topology Builder do not take effect until you publish the new topology. For details, see <A href="lync-server-2013-publishing-the-updated-topology-to-add-archiving-databases.md">Publishing the updated topology to add Archiving databases in Lync Server 2013</A> in the Deployment documentation.

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

