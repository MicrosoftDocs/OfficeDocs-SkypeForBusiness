---
title: Configure DNS records for pilot pool deployment
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure DNS records for pilot pool deployment
ms:assetid: 5c7a6e10-e1e9-4479-9bf9-d4a3e2e09ff0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688072(v=OCS.15)
ms:contentKeyID: 49733666
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure DNS records for pilot pool deployment

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-24_

Prior to deploying the Lync Server 2013 pilot pool, you must update the DNS Host A entries for the pilot pool. To successfully complete this procedure, you should be logged on to the server or domain at minimum as a member of the Domain Admins group or a member of the DnsAdmins group.

**To configure DNS Host A records**

1.  On the Domain Name System (DNS) server, click **Start**, click **Administrative Tools**, and then click **DNS**.

2.  In the console tree for your domain, expand **Forward Lookup Zones**, and then right-click the domain in which Lync Server 2013 will be installed.

3.  Click **New Host (A or AAAA)**.

4.  Click **Name**, type the host name for the pool (the domain name is assumed from the zone that the record is defined in and does not need to be entered as part of the A record).

5.  Click **IP Address**, type the IP address for the Front End pool.

6.  Click **Add Host**, and then click **OK**.

7.  When you are finished, click **Done**.

</div>

<span> </span>

</div>

</div>

</div>

