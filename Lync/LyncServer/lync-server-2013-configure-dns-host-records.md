---
title: 'Lync Server 2013: Configure DNS Host records'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure DNS Host records
ms:assetid: 78a1afcf-41c8-4da5-8740-c6570c19078c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398593(v=OCS.15)
ms:contentKeyID: 48184577
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure DNS Host records for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-01_

To successfully complete this procedure, you should be logged on to the server or domain at minimum as a member of the Domain Admins group or a member of the DnsAdmins group.

<div>

## To configure DNS Host A records

1.  On the Domain Name System (DNS) server, click **Start**, click **Administrative Tools**, and then click **DNS**.

2.  In the console tree for your domain, expand **Forward Lookup Zones**, and then right-click the domain in which Lync Server 2013 will be installed.

3.  Click **New Host (A or AAAA)**.

4.  Click **Name**, type the host name for the pool (the domain name is assumed from the zone that the record is defined in and does not need to be entered as part of the A record).

5.  Click **IP Address**, type the virtual IP (VIP) of the load balancer for the Front End pool.
    
    <div>
    

    > [!IMPORTANT]  
    > In deployments that use a Director pool, the host (A) records for the simple URLs should point to the VIP of the Director load balancer.

    
    </div>
    
    <div>
    

    > [!NOTE]  
    > If you deploy only one Enterprise Edition server or Director that is connected to the topology without a load balancer, or if you deploy a Standard Edition server, type the IP address of the Enterprise Edition server, Standard Edition server, or Director. A load balancer is required if you deploy more than one Enterprise Edition server or Director in a pool. Load balancers are not used with Standard Edition servers.

    
    </div>

6.  Click **Add Host**, and then click **OK**.

7.  To create an additional A record, repeat steps 4 and 5.

8.  When you are finished creating all the A records that you need, click **Done**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

