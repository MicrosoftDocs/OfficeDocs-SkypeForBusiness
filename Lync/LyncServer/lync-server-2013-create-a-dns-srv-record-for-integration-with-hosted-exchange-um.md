---
title: 'Create a DNS SRV record for integration with hosted Exchange UM'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Create a DNS SRV record for integration with hosted Exchange UM
ms:assetid: 8ea590ae-58ea-4ca5-9853-e0708b3ea760
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh500728(v=OCS.15)
ms:contentKeyID: 48184770
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create a DNS SRV record for integration with hosted Exchange UM

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-20_

This topic describes how to configure the Domain Name System (DNS) SRV record that is required for a Lync Server 2013 Edge Server to route to a hosted Exchange service such as Microsoft Exchange Online.

<div>

## To create an external DNS SRV record for the hosted Exchange service

1.  Log on to the external DNS server as a member of the DnsAdmins group.

2.  Click **Start**, click **Administrative Tools**, and then click **DNS**.

3.  In the console tree for your SIP domain, expand **Forward Lookup Zones**, and select the SIP domain in which Lync Server 2013 will be installed.
    
    <div>
    

    > [!IMPORTANT]
    > You must create the DNS SRV record in the SIP domain in which Lync Server is or will be installed. When you create the SRV record, the FQDN used for the Host offering this service field must be the external FQDN of the Edge pool. For example, if the external FQDN of your Edge pool is edge01.contoso.net, enter that value. This must also be in the same domain as the DNS Hosts (A) record.

    
    </div>

4.  Right-click the selected domain, and then click **Other New Records**.

5.  In **Resource Record Type**, click **Service Location (SRV)**, and then click **Create Record**.

6.  In **New Resource Record**, click **Service**, and then type **\_sipfederationtls**.

7.  Click **Protocol**, and then type **\_tcp**.

8.  Click **Port Number**, and then type **5061**.

9.  Click **Host offering this service**, and then type the fully qualified domain name (FQDN) of the Lync Server 2013 Edge pool that provides access to your Lync Server 2013 system for trusted external clients.
    
    <div>
    

    > [!NOTE]
    > The domain must also be set up as an authoritative, accepted domain in your Exchange Online settings. For details, see Create Accepted Domains at <A href="http://go.microsoft.com/fwlink/p/?linkid=229762">http://go.microsoft.com/fwlink/p/?linkId=229762</A>.

    
    </div>

10. Click **OK**, and then click **Done**.

</div>

<div>

## To verify that the DNS SRV record was created successfully

1.  Log on to a client computer in the domain.

2.  Click **Start**, and then click **Run**.

3.  At the command prompt, run the following command:
    
        nslookup <FQDN Lync Edge Pool>

4.  Verify that you receive a reply that resolves to the appropriate IP address for the FQDN.

</div>

<div>

## See Also


[Create DNS records for reverse proxy servers in Lync Server 2013](lync-server-2013-create-dns-records-for-reverse-proxy-servers.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

