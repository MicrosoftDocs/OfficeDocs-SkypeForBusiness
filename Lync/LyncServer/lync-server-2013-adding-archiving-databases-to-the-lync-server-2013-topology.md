---
title: 'Lync Server 2013: Adding Archiving databases to the Lync Server 2013 topology'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Adding Archiving databases to the Lync Server 2013 topology
ms:assetid: 089ab32f-1167-4bb8-a283-fdc6c9613072
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204654(v=OCS.15)
ms:contentKeyID: 48183338
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Adding Archiving databases to the Lync Server 2013 topology

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-10_

You must incorporate archiving into your topology before you can configure your deployment to support archiving. The information in this topic explains how to use Topology Builder to add archiving to your existing topology.

<div>


> [!NOTE]  
> If you want to use Microsoft Exchange integration to store archiving data and files on Exchange 2013 servers for all your users in your deployment, do not specify <STRONG>Archiving SQL Server store</STRONG> or <STRONG>Use SQL Server Store mirroring</STRONG> information.



</div>

<div>

## To add Archiving database support to your topology

1.  On a computer that is running Lync Server 2013, or on which the Lync Server administrative tools are installed, log on by using an account that is a member of the local Users group (or an account with equivalent user rights).
    
    <div>
    

    > [!NOTE]  
    > You can define a topology by using an account that is a member of the local Users group, but to publish a topology, which is required to add a server to the topology, you must use an account that is a member of the <STRONG>Domain Admins</STRONG> group and the <STRONG>RTCUniversalServerAdmins</STRONG> group, and that has full control permissions (that is, read, write, and modify) on the file share that you are using for the Lync Server 2013 file store (that is, so that Topology Builder can configure the required discretionary access control list (DACLs), or an account with equivalent rights.

    
    </div>

2.  Start Topology Builder.

3.  In the console tree, navigate to the Front End pool in which you want to deploy Archiving, and then click the name of the Front End pool where you want to deploy Archiving.

4.  In the **Action** menu, click **Edit Properties**.

5.  In the **Edit Properties** dialog box, click **General**.

6.  Scroll down to **Archiving**.

7.  Select the **Archiving** check box.

8.  Under **Archiving SQL Server store,** do one of the following:
    
      - To use an existing SQL Server store, in the drop-down list box, click the name of the SQL Server store that you want to use. If all of your users are homed on Microsoft Exchange Server 2013 or above, you can archive Lync communications for all your users in Exchange. In this case, you don’t need to configure SQL Server Archiving store.
    
      - To specify a new SQL Server store, click **New**, and then in the **Define New SQL Server Store** dialog box, do the following:
        
          - In **SQL Server FQDN**, specify the FQDN of the server on which you want to create the new SQL Server store.
        
          - Either click **Default Instance** to use the default instance, or, to specify a different instance, click **Named instance**, and then specify the instance you want to use.
        
          - If the specified SQL Server instance is in a mirroring relationship, select the **This SQL instance is in mirroring relation** check box, and then, in **Mirror port number**, specify the port number.

9.  If you want to use SQL Server store mirroring, select **Enable SQL Server Store mirroring**, and then do the following:
    
      - To use an existing SQL Server store for mirroring, in the **Archiving SQL Server store mirror** drop-down list box, click the name of the SQL Server store that you want to use for mirroring.
    
      - To specify a new SQL Server store for mirroring, click **New**, and then in the **Define New SQL Server Store** dialog box, do one of the following:
        
        1.  In **SQL Server FQDN**, specify the FQDN of the SQL Server on which you want to create the new SQL Server store.
        
        2.  Either click **Default Instance** to use the default instance, or, to specify a different instance, click **Named Instance**, and then specify the instance you want to use.
        
        3.  If the specified SQL Server instance is in a mirroring relationship, select the **This SQL instance is in mirroring relation** check box, and then, in **Mirror port number**, specify the port number.
    
      - If you enable SQL Server mirroring and want to include a SQL Server mirroring witness (a third, separate SQL Server instance that can detect the health of the primary SQL Server server and mirror instances), select the **Use SQL Server mirroring witness to enable automatic failover** check box, and then do one of the following:
        
        1.  In **SQL Server FQDN**, specify the FQDN of the server on which you want to create the new SQL Server mirroring witness.
        
        2.  Either click **Default Instance** to use the default instance, or, to specify a different instance, click **Named Instance**, and then specify the instance you want to use for the mirroring witness.
        
        3.  If the specified SQL Server instance is in a mirroring relationship, select the **This SQL instance is in mirroring relation** check box, and then, in **Mirror port number**, specify the port number.

10. To save the configuration, click **OK**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

