---
title: 'Lync Server 2013: Configure network adapters'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure network adapters
ms:assetid: 6519ed80-020f-47a3-851c-03dea5eac5d9
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg429707(v=OCS.15)
ms:contentKeyID: 48184320
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure network adapters in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-11-07_

You must assign one or more IP addresses to the external network adapter and at least one IP address to the internal network adapter.

In the following procedures, the server running either Forefront Threat Management Gateway (TMG) 2010 or Internet Information Server Application Request Routing has two network adapters:

  - A public, or external, network adapter, for clients that attempt to connect to your website (that is, usually over the Internet).

  - A private, or internal, network interface, for internal servers running Lync Server that are hosting Web Services.

<div>


> [!IMPORTANT]  
> Similar to the Edge Servers, you set the default gateway on the external network adapter only. The default gateway will be the IP address of the router or external facing firewall that directs traffic to the Internet. For traffic that is destined from the reverse proxy to the internal facing network adaptor, you must use persistent static routes (such as the route command in Windows Server) for all subnets containing servers referenced by the web publishing rules. Setting a persistent route does not cause the computer to become a router. If IP forwarding is not enabled, the computer is acting only to direct specific traffic destined for another network to the appropriate interface. This is essentially setting two gateways – one as the default pointing to the external networks, and one for traffic destined to the internal interface and on to a router or other network.<BR>However, creating persistent routes for all subnets may not be necessary if your network’s routers are configured to summarize routes. Create a persistent route to the network where the router is defined and use the router as the default gateway. If you are not sure how your network is configured and need guidance on what persistent routes need to be created, consult with your company’s Network Engineers.<BR>The reverse proxy must be able to resolve the DNS host (A) records for the internal Director or Front End Server and next hop pool FQDNs used in the web publishing rules. As with the Edge Servers, for security reasons, we recommend that you do not configure a reverse proxy to use a DNS server located in the internal network. This means you either need DNS servers in the perimeter, or you need HOSTS file entries on the reverse proxy that resolves each of these FQDNs to the internal IP address of the servers.



</div>

<div>

## To configure the network adapter cards on the reverse proxy computer

1.  On the Windows Server 2008, Windows Server 2008 R2, Windows Server 2012, or Windows Server 2012 R2 server running as the reverse proxy, open **Change Adapter Settings** by clicking **Start**, pointing to **Control Panel**, clicking **Network and Sharing Center**, and then clicking **Change Adapter Settings**.

2.  Right-click the external network connection that you want to use for the external interface, and then click **Properties**.

3.  On the **Properties** page, click the **Networking** tab, click **Internet Protocol Version 4 (TCP/IPv4)** in the **This connection uses the following items** list, and then click **Properties**.

4.  On the **Internet Protocol (TCP/IP) Properties** page, configure the IP addresses as appropriate for the network subnet to which the network adapter is attached.
    
    <div>
    

    > [!NOTE]  
    > If the reverse proxy is already being used by other applications that use HTTPS/TCP/443, such as for publishing Outlook Web Access, you either need to add another IP address so that you can publish the Lync Server 2013 Web Services on HTTPS/TCP/443 without interfering with the existing rules and web listeners, or you need to replace the existing certificate with one that adds the new external FQDN names to the subject alternative name.

    
    </div>

5.  Click **OK**, and then click **OK**.

6.  In **Network Connections**, right-click the internal network connection that you want to use for the internal interface, and then click **Properties**.

7.  Repeat steps 3 through 5 to configure the internal network connection.

</div>

</div>

<span> </span>

</div>

</div>

</div>

