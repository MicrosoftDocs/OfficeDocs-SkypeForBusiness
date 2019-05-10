---
title: 'Lync Server 2013: Define optional Director topologies in your topology'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Define optional Director topologies in your topology
ms:assetid: 8e9a659d-23b0-401d-b296-59c7df414d49
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398717(v=OCS.15)
ms:contentKeyID: 48184808
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Define optional Director topologies in your topology for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-08_

Lync Server 2013 Directors can be single-instance servers or they can be installed as a load-balanced pool of multiple Directors for higher availability and capacity. Both hardware load balancing and Domain Name System (DNS) load balancing are supported. This topic explains how to configure DNS load balancing for Director pools.

To successfully publish, enable, or disable a topology when you add or remove a server role, you should be logged on as a user who is a member of the **RTCUniversalServerAdmins** and **Domain Admins** groups. You can also delegate the proper administrator rights and permissions for adding server roles. For details, see [Delegate setup permissions in Lync Server 2013](lync-server-2013-delegate-setup-permissions.md) in the Standard Edition server or Enterprise Edition server Deployment documentation. For other configuration changes, only membership in the **RTCUniversalServerAdmins** group is required.

This topic describes the steps to define and publish the topology for the two Director topologies:

  - To define the Director (single instance)

  - To define the Director (multiple Director pool)

<div>

## To define the Director (single instance)

1.  Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.

2.  On the welcome page, click **Download Topology from Existing Deployment**.

3.  In the **Save Topology As** dialog box, type the name and location of the local copy of the existing topology, and then click **Save**.

4.  Expand the site in which you plan to add the Director, right-click **Director pools**, and then click **New Director Pool**.

5.  In the **Define the Director pool FQDN** dialog box, do the following:
    
      - In **Pool FQDN**, type the FQDN for the Director pool.
    
      - Click **Single computer pool**, and then click **Next**.

6.  In the **Define the file share** dialog box, do one of the following:
    
    1.  To use an existing file share, click **Use a previously defined file share**, select a file share from the list, and then click **Next**.
    
    2.  To create a new file share, click **Define a new file share**, type the FQDN for the location of the file share in **File Server FQDN**, type the name of the share in **File Share**, and then click **Next**.
    
    <div>
    

    > [!IMPORTANT]  
    > The file share that you specify or create in this step must exist or be created prior to publishing the topology.<BR>The file share assigned to a Director is not actually used, so you can assign the file share of any pool in the organization.

    
    </div>

7.  In the **Specify the Web Services URL** dialog box, in **External Base URL**, specify the FQDN for the Directors, and then click **Finish**.
    
    <div>
    

    > [!IMPORTANT]  
    > The name must be resolvable from Internet DNS servers and point to the public IP address of the reverse proxy, which listens for HTTP/HTTPS requests to that URL and proxies them to the external Web Services virtual directory on that Director.

    
    </div>
    
    <div>
    

    > [!WARNING]  
    > If you have more than one Front End pool or Front End Server the external Web services FQDN must be unique. For example, if you define the external Web services FQDN of a Front End Server as <STRONG>pool01.contoso.com</STRONG>, you cannot use <STRONG>pool01.contoso.com</STRONG> for another Front End pool or Front End Server. If you are also deploying Directors, the external Web services FQDN defined for any Director or Director pool must be unique from any other Director or Director pool as well as any Front End pool or Front End Server. If decide to override the Internal web services with a self-defined FQDN, each FQDN must be unique from any other Front End pool, Director or a Director pool.

    
    </div>

8.  Publish the topology.

</div>

<div>

## To define the Director (multiple Director pool)

1.  Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.

2.  On the welcome page, click **Download Topology from Existing Deployment**.

3.  In the **Save Topology As** dialog box, type the name and location of the local copy of the existing topology, and then click **Save**.

4.  Expand the site in which you plan to add the Director, right-click **Director pools**, and then click **New Director Pool**.

5.  In the **Define the Director pool FQDN** dialog box, do the following:
    
      - In **Pool FQDN**, type the FQDN for the Director pool.
    
      - Click **Multiple computer pool**, and then click **Next**.

6.  In the **Define the computers in this pool** dialog box, do the following:
    
      - Specify the computer FQDN of the first pool member, and then click **Add**.
    
      - Repeat the previous step for each computer that you want to add. When you are finished, click **Next**.

7.  In the **Define the file share** dialog box, do one of the following:
    
      - To use an existing file share, click **Use a previously defined file share**, select a file share from the list, and then click **Next**.
    
      - To create a new file share, click **Define a new file share**, type the FQDN for the location of the file share in **File Server FQDN**, type the name of the share in **File Share**, and then click **Next**.
    
    <div>
    

    > [!IMPORTANT]  
    > The file share that you specify or create in this step must exist or be created prior to publishing the topology.<BR>The file share assigned to a Director is not actually used, so you can assign the file share of any pool in the organization.

    
    </div>

8.  In the **Specify the Web Services URL** dialog box, in **External Base URL**, specify the FQDN for the Directors, and then click **Finish**.
    
    <div>
    

    > [!IMPORTANT]  
    > The name must be resolvable from Internet DNS servers and point to the public IP address of the reverse proxy, which listens for HTTP/HTTPS requests sent to that URL and proxies them to the external Web Services virtual directory on that Director pool.

    
    </div>
    
    <div>
    

    > [!WARNING]  
    > If you have more than one Front End pool or Front End Server the external Web services FQDN must be unique. For example, if you define the external Web services FQDN of a Front End Server as <STRONG>pool01.contoso.com</STRONG>, you cannot use <STRONG>pool01.contoso.com</STRONG> for another Front End pool or Front End Server. If you are also deploying Directors, the external Web services FQDN defined for any Director or Director pool must be unique from any other Director or Director pool as well as any Front End pool or Front End Server. If decide to override the Internal web services with a self-defined FQDN, each FQDN must be unique from any other Front End pool, Director or a Director pool.

    
    </div>

9.  Publish the topology.

</div>

</div>

<span> </span>

</div>

</div>

</div>

