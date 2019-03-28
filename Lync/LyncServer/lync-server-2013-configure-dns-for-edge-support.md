---
title: 'Lync Server 2013: Configure DNS for edge support'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure DNS for edge support
ms:assetid: 955493e6-aa29-424d-bb81-1ef87b3b15e3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398756(v=OCS.15)
ms:contentKeyID: 48184894
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure DNS for edge support in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-15_

You must configure Domain Name System (DNS) records for internal and external edge interfaces, including both Edge Server and reverse proxy interfaces. By default, Edge Servers are not joined to a domain and will not have a fully qualified domain name (fully qualified domain name). The Edge Server is only referred to by the short (machine) name, not a fully qualified domain name. However, Topology Builder uses FQDNs, not short names. The name of the Edge Server must match the FQDN used by Topology Builder. To do this, you define a DNS suffix that, when combined with the machine name, results in the expected FQDN. Use the following procedure in “To add the DNS suffix to the computer name on and Edge Server that is not joined to a domain” to add the DNS suffix to the computer name.

<div>


> [!NOTE]  
> By default, DNS uses a round robin algorithm to rotate the order of resource record data returned in query answers where multiple resource records of the same type exist for a queried DNS domain name. Lync Server 2013 DNS load balancing, depends on DNS round-robin as a part of the DNS Load Balancing mechanism. Verify that round-robin setting has not been disabled. If you are using a DNS server that is not running a Windows operating system, verify that round-robin resource record ordering is enabled.



</div>

Use the following procedures in “**To create a DNS SRV record**” to create and verify each DNS SRV record. Use the procedure in “**To create a DNS A record**” to define the DNS A records required for external user access. To confirm that the records are configured and working correctly, see “**To verify a DNS record**” in this topic. For details about each record required to support external user access, see [Determine DNS requirements for Lync Server 2013](lync-server-2013-determine-dns-requirements.md).

<div>

## To add the DNS suffix to the computer name on an Edge Server that is not joined to a domain

1.  On the computer, click **Start**, right-click **Computer**, and then click **Properties**.

2.  Under **Computer name, domain, and workgroup settings**, click **Change settings**.

3.  On the **Computer Name** tab, click **Change**.

4.  In **Computer Name/Domain Changes**, click **More**.

5.  In **DNS Suffix and NetBIOS Computer Name**, in **Primary DNS suffix of this computer**, type the name of your internal domain (for example, corp.contoso.com), and then click **OK** three times.

6.  Restart the computer.

</div>

<div>

## To create a DNS SRV record

1.  On the appropriate DNS server, click **Start**, click **Control Panel**, click **Administrative Tools**, and then click **DNS**.
    
    <div>
    

    > [!IMPORTANT]  
    > You need to configure DNS so that there are: 1) external DNS entries for external DNS lookups by remote users and federated partners; 2) entries for DNS lookups for use by the Edge Servers within the perimeter network (also known as DMZ, demilitarized zone, and screened subnet), including A records for the internal servers running Lync Server 2013; and 3) internal DNS entries for lookups by the internal clients and servers running Lync Server 2013.

    
    </div>

2.  In the console tree for your SIP domain, expand **Forward Lookup Zones**, and then right-click the domain where Lync Server 2013 is installed.

3.  Click **Other New Records**.

4.  In **Select a resource record type**, type **Service Location (SRV)**, and then click **Create Record**.

5.  Provide all required information for the DNS SRV record.

</div>

<div>

## To create a DNS A record

1.  On the DNS server, click **Start**, click **Control Panel**, click **Administrative Tools**, and then click **DNS**.

2.  In the console tree for your SIP domain, expand **Forward Lookup Zones**, and then right-click the domain in which Lync Server 2013 is installed.

3.  Click **New Host (A)**.

4.  Provide all required information for the DNS SRV record.

</div>

<div>

## To verify a DNS record

1.  Log on to a client computer in the domain.

2.  Click **Start**, and then click **Run**.

3.  At the command prompt, run the following command:
    
        nslookup <FQDN edge interface>

4.  Verify that you receive a reply that resolves to the appropriate IP address for the FQDN.

</div>

<div>

## See Also


[Create a DNS SRV record for integration with hosted Exchange UM](lync-server-2013-create-a-dns-srv-record-for-integration-with-hosted-exchange-um.md)  


[Determine DNS requirements for Lync Server 2013](lync-server-2013-determine-dns-requirements.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

