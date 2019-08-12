---
title: 'Lync Server 2013: Configure DNS for load balancing'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure DNS for load balancing
ms:assetid: 1b2e8414-8676-4872-8ecf-ea07196f74de
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398251(v=OCS.15)
ms:contentKeyID: 48183540
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure DNS for load balancing in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-01_

To successfully complete this procedure, you should be logged on to the server or domain minimally as a member of the Domain Admins group or a member of the DnsAdmins group.

Domain Name System (DNS) Load Balancing balances the network traffic that is unique to Lync Server 2013, such as SIP traffic and media traffic. DNS load balancing is supported for Front End pools, Edge pools, Director pools, and stand-alone Mediation pools. A pool that is configured to use DNS load balancing must have two fully qualified domain names (FQDNs) defined: the regular pool FQDN that is used by DNS load balancing (for example, pool1.contoso.com) and that resolves to the physical IPs of the servers in the pool, and another FQDN for the pool’s Web Services (for example, web1.contoso.net), which resolves to the virtual IP address of the pool. For details about DNS Load Balancing, see [DNS load balancing in Lync Server 2013](lync-server-2013-dns-load-balancing.md) in the Planning documentation.

<div>


> [!NOTE]  
> Hardware load balancing is still required for client to server HTTPS traffic.



</div>

Before you can use DNS load balancing, you must do the following:

1.  Override the internal Web Services pool FQDN.
    
    <div>
    

    > [!WARNING]  
    > If decide to override the Internal web services with a self-defined FQDN, each FQDN must be unique from any other Front End pool, Director or a Director pool.

    
    </div>

2.  Create DNS A host records to resolve the pool FQDN to the IP addresses of all the servers in the pool.

3.  Enable IP Address randomization or, for Windows Server DNS, enable round robin.
    
    <div>
    

    > [!NOTE]  
    > Round robin should be enabled by default.

    
    </div>

<div>

## To override internal Web services FQDN

1.  Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.

2.  From the console tree, expand the Enterprise Edition Front End pools node.

3.  Right-click the pool, click **Edit Properties**, and then click **Web Services**.

4.  Below **Internal web services**, select the **Override FQDN** check box.

5.  Type the pool FQDN that resolves to the physical IP addresses of the servers in the pool.

6.  Below **External web services**, type the external pool FQDN that resolves to the virtual IP addresses of the pool, and then click **OK**.

7.  From the console tree, click **Lync Server 2013**, and then in the **Actions** pane, click **Publish Topology**.

</div>

<div>

## To create DNS Host (A) Records for all internal pool servers

1.  Click **Start**, click **All Programs**, click **Administrative Tools**, and then click **DNS**.

2.  In **DNS Manager**, click the DNS Server that manages your records to expand it.

3.  Click **Forward Lookup Zones** to expand it.

4.  Right-click the DNS domain that you need to add records to, and then click **New Host (A or AAAA)**.

5.  In the **Name** box, type the name of the host record (the domain name will be automatically appended).

6.  In the IP Address box, type the IP address of the individual Front End Server and then select **Create associated pointer (PTR) record** or **Allow any authenticated user to update DNS records with the same owner name**, if applicable.

7.  Continue creating records for all member Front End Servers that will participate in DNS Load Balancing.
    
    For example, if you had a pool named pool1.contoso.com and three Front End Servers, you would create the following DNS entries:
    
    
    <table>
    <colgroup>
    <col style="width: 33%" />
    <col style="width: 33%" />
    <col style="width: 33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>FQDN</th>
    <th>Type</th>
    <th>Data</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Pool1.contoso.com</p></td>
    <td><p>Host (A)</p></td>
    <td><p>192.168.1.1</p></td>
    </tr>
    <tr class="even">
    <td><p>Pool1.contoso.com</p></td>
    <td><p>Host (A)</p></td>
    <td><p>192.168.1.2</p></td>
    </tr>
    <tr class="odd">
    <td><p>Pool1.contoso.com</p></td>
    <td><p>Host (A)</p></td>
    <td><p>192.168.1.3</p></td>
    </tr>
    </tbody>
    </table>
    
    For details about creating DNS Host (A) records, see [Configure DNS Host records for Lync Server 2013](lync-server-2013-configure-dns-host-records.md).

</div>

<div>

## To enable round robin for Windows Server

1.  Click **Start**, click **All Programs**, click **Administrative Tools**, and then click **DNS**.

2.  Expand **DNS**, right-click the DNS server you want to configure, and then click **Properties**.

3.  Click the **Advanced** tab, select **Enable round robin** and **Enable netmask ordering**, and then click **OK**.
    
    ![DNS Round Robin dialog box](images/Gg398251.e7bf6125-8d78-4460-8401-0a8e7e21d305(OCS.15).jpg "DNS Round Robin dialog box")

<div>


> [!NOTE]  
> This feature should be enabled by default.



</div>

</div>

<div>

## See Also


[DNS load balancing in Lync Server 2013](lync-server-2013-dns-load-balancing.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

