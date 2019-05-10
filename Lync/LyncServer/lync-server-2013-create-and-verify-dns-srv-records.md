---
title: 'Lync Server 2013: Create and verify DNS SRV records'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Create and verify DNS SRV records
ms:assetid: 86888c7e-1401-458f-9a7b-08ac726deeec
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398680(v=OCS.15)
ms:contentKeyID: 48184714
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create and verify DNS SRV records in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

To successfully complete this procedure, you should be logged on to the server or domain minimally as a member of the Domain Admins group or a member of the DnsAdmins group.

This topic describes how to configure the Domain Name System (DNS) records that you are required to create in Lync Server 2013 deployments and those required for automatic client sign in. When you create a Front End pool, Setup creates Active Directory objects and settings for the pool, including the pool fully qualified domain name (FQDN). Similar objects and settings are created for a Standard Edition server. For clients to be able to connect to the pool or Standard Edition server, the FQDN of the pool or Standard Edition server must be registered in DNS. You must create DNS SRV records in your internal DNS for every SIP domain. This procedure assumes that your internal DNS has zones for your SIP user domains.

<div>

## To configure a DNS SRV record

1.  On the DNS server, click **Start**, click **Administrative Tools**, and then click **DNS**.

2.  In the console tree for your SIP domain, expand **Forward Lookup Zones**, and then right-click the SIP domain in which Lync Server 2013 will be installed.

3.  Click **Other New Records**.

4.  In **Select a resource record type**, click **Service Location (SRV)**, and then click **Create Record**.

5.  Click **Service**, and then type **\_sipinternaltls**.

6.  Click **Protocol**, and then type **\_tcp**.

7.  Click **Port Number**, and then type **5061**.

8.  Click **Host offering this service**, and then type the FQDN of the pool or Standard Edition server.

9.  Click **OK**, and then click **Done**.

</div>

<div>

## To verify the creation of a DNS SRV record

1.  Log on to a client computer in the domain with an account that is a member of the Authenticated Users group or has equivalent permissions.

2.  Click **Start**, and then click **Run**.

3.  In the **Open** box, type **cmd**, and then click **OK**.

4.  At the command prompt, type **nslookup**, and then press ENTER.

5.  Type **set type=srv**, and then press ENTER.

6.  Type **\_sipinternaltls.\_tcp.contoso.com**, and then press ENTER. The output displayed for the Transport Layer Security (TLS) record is as follows:
    
    Server: \<dns server\>.contoso.com
    
    Address: \<IP address of DNS server\>
    
    Non-authoritative answer:
    
    \_sipinternaltls.\_tcp.contoso.com SRV service location:
    
    priority = 0
    
    weight = 0
    
    port = 5061
    
    svr hostname = poolname.contoso.com (or Standard Edition server A record)
    
    poolname.contoso.com internet address = \<virtual IP Address of the load balancer\> or \<IP address of a single Enterprise Edition server for pools with only one Enterprise Edition server\> or \<IP address of the Standard Edition server\>

7.  When you are finished, at the command prompt, type **exit**, and then press ENTER.

</div>

<div>

## To verify that the FQDN of the Front End pool or Standard Edition server can be resolved

1.  Log on to a client computer in the domain.

2.  Click **Start**, and then click **Run**.

3.  In the **Open** box, type **cmd**, and then click **OK**.

4.  At the command prompt, type **nslookup** \<FQDN of the Front End pool\> or \<FQDN of the Standard Edition server\>, and then press ENTER.

5.  Verify that you receive a reply that resolves to the appropriate IP address for the FQDN.

</div>

</div>

<span> </span>

</div>

</div>

</div>

