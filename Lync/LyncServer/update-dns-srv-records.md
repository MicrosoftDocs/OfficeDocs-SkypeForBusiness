---
title: Update DNS SRV records
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Update DNS SRV records
ms:assetid: 9542b91a-108c-4980-89ec-634905cbbf26
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688139(v=OCS.15)
ms:contentKeyID: 49733739
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Update DNS SRV records

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-29_

To successfully complete this procedure, you should be logged on to the server or domain as a member of the Domain Admins group or a member of the DnsAdmins group.

This topic describes how to update the Domain Name System (DNS) records after migrating to Lync Server 2013. After all users have been moved to Lync Server 2013, but before the legacy Lync Server 2010 pool or Director is decommissioned, you must update the DNS SRV records in your internal DNS for every SIP domain. This procedure assumes that your internal DNS has zones for your SIP user domains.

**To configure a DNS SRV record**

1.  On the DNS server, click **Start**, click **Administrative Tools**, and then click **DNS**.

2.  In the console tree for your SIP domain, expand **Forward Lookup Zones**, expand the SIP domain in which Lync Server 2013 is installed, and navigate to the **\_tcp** setting.

3.  In the right pane, right click **\_sipinternaltls** and select **Properties**.

4.  In **Host offering this service**, update the host FQDN to point to the Lync Server 2013 pool.

5.  Click **OK**.

**To verify that the FQDN of the Front End pool or Standard Edition server can be resolved**

1.  Log on to a client computer in the domain.

2.  Click **Start**, and then click **Run**.

3.  In the **Open** box, type **cmd**, and then click **OK**.

4.  At the command prompt, type **nslookup** \<FQDN of the Front End pool\> or \<FQDN of the Standard Edition server\>, and then press ENTER.

5.  Verify that you receive a reply that resolves to the appropriate IP address for the FQDN.

</div>

<span> </span>

</div>

</div>

</div>

