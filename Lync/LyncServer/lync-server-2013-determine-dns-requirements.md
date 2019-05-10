---
title: 'Lync Server 2013: Determine DNS requirements'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Determine DNS requirements
ms:assetid: 95777017-6282-44c0-a685-f246af0501b4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398758(v=OCS.15)
ms:contentKeyID: 48184839
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Determine DNS requirements for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Use the following flow chart to determine Domain Name System (DNS) requirements. Changes for the Cumulative Updates for Lync Server 2013: February 2013 are noted where they apply.

<div>


> [!IMPORTANT]  
> Microsoft Lync Server 2013 supports the use of IPv6 addressing. To use IPv6 addresses, you must also provide support for IPv6 DNS and configure DNS host AAAA (known as “quad-A”) records. In deployments where both IPv4 and IPv6 are being used, it is best to configure and maintain both host A records for IPv4 and host AAAA for IPv6. Even if your deployment has transitioned fully to IPv6, IPv4 DNS host records may still be required when external users are still using IPv4.



</div>

**Determining DNS Requirements Flow Chart**

![175782ac-363e-408a-912f-8991bf152970](images/Gg398758.175782ac-363e-408a-912f-8991bf152970(OCS.15).jpg "175782ac-363e-408a-912f-8991bf152970")

<div>


> [!IMPORTANT]  
> By default the computer name of a computer that is not joined to a domain is a host name, not a fully qualified domain name (FQDN). Topology Builder uses FQDNs, not host names. So, you must configure a DNS suffix on the name of the computer to be deployed as an Edge Server that is not joined to a domain. <STRONG>Use only standard characters</STRONG> (including A–Z, a–z, 0–9, and hyphens) when assigning FQDNs of your Lync Servers, Edge Servers, and pools. Do not use Unicode characters or underscores. Nonstandard characters in an FQDN are often not supported by external DNS and public CAs (that is, when the FQDN must be assigned to the SN in the certificate). For additional details, see <A href="lync-server-2013-configure-dns-host-records.md">Configure DNS Host records for Lync Server 2013</A>



</div>

<div>

## How Lync Clients Locate Services

Microsoft Lync 2010, Lync 2013, and Lync Mobile are similar in how the client finds and accesses services in Lync Server 2013. The notable exception is the Lync Windows Store app that uses a different service location process. This section details two scenarios of how the clients locate services, first the traditional method using a series of SRV and A host records, second using only the Autodiscover service records. Cumulative updates to the desktop clients change the DNS location process from Lync Server 2010 For all clients, the DNS query process continues until a successful query is returned, or the list of possible DNS records is exhausted, and the final error is returned to the client.

For all clients **except** for the Lync Windows Store app During DNS lookup, SRV records are queried and returned to the client in the following order:

1.  lyncdiscoverinternal.\<domain\>   A (host) record for the Autodiscover service on the internal Web services

2.  lyncdiscover.\<domain\>   A (host) record for the Autodiscover service on the external Web services

3.  \_sipinternaltls.\_tcp.\<domain\>   SRV (service locator) record for internal TLS connections

4.  \_sipinternal.\_tcp.\<domain\>   SRV (service locator) record for internal TCP connections (performed only if TCP is allowed)

5.  \_sip.\_tls.\<domain\>   SRV (service locator) record for external TLS connections

6.  sipinternal.\<domain\>   A (host) record for the Front End pool or Director, resolvable only on the internal network

7.  sip.\<domain\>   A (host) record for the Front End pool or Director on the internal network, or the Access Edge service when the client is external

8.  sipexternal.\<domain\>   A (host) record for the Access Edge service when the client is external

The Lync Windows Store app changes the process completely because it uses two records:

1.  lyncdiscoverinternal.\<domain\>   A (host) record for the Autodiscover service on the internal Web services

2.  lyncdiscover.\<domain\>   A (host) record for the Autodiscover service on the external Web services

There is no fallback to the other record types.

The difference between the methods used for newer clients as compared to older clients is that the Autodiscover service is becoming the preferred method to locate all services.

When a connection is successful, the Autodiscover Service returns all the Web Services URLs for the user's home pool, including the Mobility Service (known as Mcx by the virtual directory created for the service in IIS), Microsoft Lync Web App and Web scheduler URLs. However, both the internal Mobility Service URL and the external Mobility Service URL is associated with the external Web Services FQDN. Therefore, regardless of whether a mobile device is internal or external to the network, the device always connects to the Mobility Service externally through the reverse proxy.

If the Cumulative Updates for Lync Server 2013: February 2013 has been installed, the Autodiscover Service also returns references to Internal/UCWA, External/UCWA and UCWA. These entries refer to the Unified Communications Web API (UCWA) web component. Currently, only the entry UCWA is used and provides a reference to a URL for the web component. UCWA is used by Lync 2013 Mobile clients instead of the Mcx Mobility Service used by the Lync 2010 Mobile clients.

<div>


> [!NOTE]  
> When creating SRV records, it is important to remember that they must point to a DNS A and AAAA (if you are using IPv6 addressing) record in the same domain in which the DNS SRV record is created. For example, if the SRV record is in contoso.com, the A and AAAA (if you are using IPv6 addressing) record it points to cannot be in fabrikam.com.



</div>

<div>


> [!TIP]  
> The default configuration is to direct all mobile client traffic through the external site. You can modify settings to return only the internal URL, if this is more preferable for your requirements. With this configuration, users can use Lync mobile applications on their mobile devices only when they are inside the corporate network. To define this configuration, you use the <STRONG>Set-CsMcxConfiguration</STRONG> cmdlet.



</div>

<div>


> [!NOTE]  
> Although mobile applications can also connect to other Lync Server 2013 services, such as Address Book Service, internal mobile application web requests go to the external web FQDN only for the Mobility Service. Other service requests, such as Address Book requests, do not require this configuration.



</div>

Mobile devices support manual discovery of services. In this case, each user must configure the mobile device settings with the full internal and external Autodiscover Service URIs, including the protocol and path, as follows:

  - https://\<ExtPoolFQDN\>/Autodiscover/autodiscoverservice.svc/Root for external access

  - https://\<IntPoolFQDN\>/AutoDiscover/AutoDiscover.svc/Root for internal access

We recommend that you use automatic discovery, rather than manual discovery. However, manual settings can be useful for troubleshooting mobile device connectivity issues.

</div>

<div>

## Configuring Split-Brain DNS with Lync Server

Split-brain DNS is known by a number of names, for example, split DNS or split-horizon DNS. Simply, it describes a DNS configuration where there are two DNS zones with the same namespace – but one DNS zone services internal-only requests, and the other DNS zone services external-only requests. However, many of the DNS SRV and A records contained in the internal DNS will not be contained in the external DNS, and the reverse is also true. In cases where the same DNS record exists in both the internal and external DNS (for example, www.contoso.com), the IP address returned will be different based on where (internal or external) the query was initiated.

<div>


> [!IMPORTANT]  
> Currently, Split-Brain DNS is not supported for the mobility, or more specifically, the LyncDiscover and LyncDiscoverInternal DNS records. LyncDiscover must be defined on an external DNS server and LyncDiscoverInternal must be defined on an internal DNS server.



</div>

For the purposes of these topics, the term split-brain DNS will be used.

If you are configuring split-brain DNS, the following internal and external zone contain a summary of the types of DNS records required in each zone. For details, see [Scenarios for external user access in Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md).

**Internal DNS:**

  - Contains a DNS zone called contoso.com for which it is authoritative

  - The internal contoso.com zone contains:
    
      - DNS A and AAAA (if you are using IPv6 addressing) and SRV records for internal Lync Server 2013 client autoconfiguration (optional)
    
      - DNS A and AAAA (if you are using IPv6 addressing) or CNAME records for automatic discovery of Lync Server 2013 Web Services (optional)
    
      - DNS A and AAAA (if you are using IPv6 addressing) records for Front End pool name, Director or Director pool name, and all internal servers running Lync Server 2013 in the corporate network
    
      - DNS A and AAAA (if you are using IPv6 addressing) records for the Edge internal interface of each Lync Server 2013, Edge Server in the perimeter network
    
      - DNS A and AAAA (if you are using IPv6 addressing) records for the internal interface of each reverse proxy server in the perimeter network (optional for management of reverse proxy)
    
      - All Lync Server 2013  Edge Server internal edge interfaces in the perimeter network use the internal DNS zone for resolving queries to contoso.com
    
      - All servers running Lync Server 2013 and clients running Lync 2013 in the corporate network point to the internal DNS servers for resolving queries to contoso.com, or use of HOSTS file on each Edge server and list A and AAAA (if you are using IPv6 addressing) records for next hop server, specifically the Director or Director VIP, Front End pool VIP, or Standard Edition server

**External DNS:**

  - Contains a DNS zone called contoso.com for which it is authoritative

  - The external contoso.com zone contains:
    
      - DNS A and AAAA (if you are using IPv6 addressing) and SRV records for Lync Server 2013 client autoconfiguration (optional)
    
      - DNS A and AAAA (if you are using IPv6 addressing) or CNAME records for automatic discovery of Lync Server 2013 Web Services for use with mobility
    
      - DNS A and AAAA (if you are using IPv6 addressing) and SRV records for the Edge external interface of each Lync Server 2013, Edge Server or hardware load balancer virtual IP (VIP) in the perimeter network
    
      - DNS A and AAAA (if you are using IPv6 addressing) records for the external interface of the reverse proxy server or VIP for a pool of reverse proxy servers in the perimeter network

</div>

<div>

## Automatic Configuration without Split-Brain DNS

Using split-brain DNS, a Lync Server 2013 user that signs in internally can take advantage of automatic configuration if the internal DNS zone contains a \_sipinternaltls.\_tcp SRV record for each SIP domain in use. However, if you do not use split-brain DNS, internal automatic configuration of clients running Lync will not work unless one of the workarounds described in later in this section is implemented. This is because Lync Server 2013 requires the user’s SIP URI to match the domain of the Front End pool designated for automatic configuration. This was also the case with earlier versions of Communicator.

For example, if you have two SIP domains in use, the following DNS service (SRV) records would be required:

  - If a user signs in as bob@contoso.com the following SRV record will work for automatic configuration because the user’s SIP domain (contoso.com) matches the domain of automatic configuration Front End pool):
    
     \_sipinternaltls.\_tcp.contoso.com. 86400 IN SRV 0 0 5061 pool01.contoso.com

  - If a user signs in as alice@fabrikam.com the following DNS SRV record will work for automatic configuration of the second SIP domain.
    
     \_sipinternaltls.\_tcp.fabrikam.com. 86400 IN SRV 0 0 5061 pool01.fabrikam.com

For comparison, if a user signs in as tim@litwareinc.com the following DNS SRV record will not work for automatic configuration, because the client’s SIP domain (litwareinc.com) does not match the domain that the pool is in (fabrikam.com):

 \_sipinternaltls.\_tcp.litwareinc.com. 86400 IN SRV 0 0 5061 pool01.fabrikam.com

If automatic configuration is required for clients running Lync, select one of the following options:

  - **Group Policy Objects**   Use Group Policy objects (GPOs) to populate the correct server values.
    
    <div>
    

    > [!NOTE]  
    > This option does not enable automatic configuration, but it does automate the process of manual configuration, so if this approach is used, the SRV records associated with automatic configuration are not required.

    
    </div>

  - **Matching internal zone**   Create a zone in the internal DNS that matches the external DNS zone (for example, contoso.com) and create DNS A and AAAA (if you are using IPv6 addressing) records corresponding to the Lync Server 2013 pool used for automatic configuration. For example, if a user is homed on pool01.contoso.net but signs into Lync as bob@contoso.com, create an internal DNS zone called contoso.com and inside it, create a DNS A and AAAA (if IPv6 addressing is used) record for pool01.contoso.com.

  - **Pin-point internal zone**   If you are creating an entire zone in the internal DNS is not an option, you can create pin-point (that is, dedicated) zones that correspond to the SRV records that are required for automatic configuration, and populate those zones using dnscmd.exe. Dnscmd.exe is required because the DNS user interface does not support creation of pin-point zones. For example, if the SIP domain is contoso.com and you have a Front End pool called pool01 that contains two Front End Servers, you need the following pin-point zones and A records in your internal DNS:
    
        dnscmd . /zoneadd _sipinternaltls._tcp.contoso.com. /dsprimary
        dnscmd . /recordadd _sipinternaltls._tcp.contoso.com. @ SRV 0 0 5061 pool01.contoso.com.
        dnscmd . /zoneadd pool01.contoso.com. /dsprimary
        dnscmd . /recordadd pool01.contoso.com. @ A 192.168.10.90
        dnscmd . /recordadd pool01.contoso.com. @ AAAA <IPv6 address>
        dnscmd . /recordadd pool01.contoso.com. @ A 192.168.10.91 
        dnscmd . /recordadd pool01.contoso.com. @ AAAA <IPv6 address>
    
    If your environment contains a second SIP domain (for example, fabrikam.com), you need the following pin-point zones and A records in your internal DNS:
    
        dnscmd . /zoneadd _sipinternaltls._tcp.fabrikam.com. /dsprimary
        dnscmd . /recordadd _sipinternaltls._tcp.fabrikam.com. @ SRV 0 0 5061 pool01.fabrikam.com.
        dnscmd . /zoneadd pool01.fabrikam.com. /dsprimary
        dnscmd . /recordadd pool01.fabrikam.com. @ A 192.168.10.90
        dnscmd . /recordadd pool01.contoso.com. @ AAAA <IPv6 address>
        dnscmd . /recordadd pool01.fabrikam.com. @ A 192.168.10.91
        dnscmd . /recordadd pool01.contoso.com. @ AAAA <IPv6 address>

<div>


> [!NOTE]  
> The Front End pool FQDN appears twice, but with two different IP addresses. This is because DNS load balancing is used, but if hardware load balancing is used, there would be only a single Front End pool entry. Also, the Front End pool FQDN values change between the contoso.com example and the fabrikam.com example, but the IP addresses remain the same. This is because users signing in from either SIP domain, use the same Front End pool for automatic configuration.



</div>

For details, see the DMTF blog article, "Communicator Automatic Configuration and Split-Brain DNS," at [http://go.microsoft.com/fwlink/p/?linkId=200707](http://go.microsoft.com/fwlink/p/?linkid=200707).

<div>


> [!NOTE]  
> The content of each blog and its URL are subject to change without notice.



</div>

</div>

<div>

## Configuring the domain name system (DNS) for Disaster Recovery

To configure DNS to redirect Lync Server 2013 Web traffic to your disaster recovery and failover sites, you must be using a DNS provider that supports GeoDNS. You can set up your DNS records for Web to support disaster recovery, so that features that use Web services continue even if one entire Front End pool goes down. This disaster recovery feature supports the Autodiscover (Lyncdiscover URL), Meet and Dial-In simple URLs.

You define and configure additional DNS host (A and AAAA if using IPv6) records for internal and external resolution of Web services at your GeoDNS provider. The following details assume paired pools, geographically dispersed, and GeoDNS supported by your provider with either round-robin DNS, or configured to use Pool1 as primary, and fail over to Pool2 in the event of communications loss or hardware failure.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>GeoDNS record (example)</th>
<th>Pool records (example)</th>
<th>CNAME records (example)</th>
<th>DNS settings (select one option)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Meet-int.geolb.contoso.com</p></td>
<td><p>Pool1InternalWebFQDN.contoso.com</p>
<p>Pool2InternalWebFQDN.contoso.com</p></td>
<td><p>Meet.contoso.com alias to Pool1InternalWebFQDN.contoso.com</p>
<p>Meet.contoso.com alias to Pool2InternalWebFQDN.contoso.com</p></td>
<td><p>Round Robin between pools</p>
<p>Use primary, connect to secondary if failure</p></td>
</tr>
<tr class="even">
<td><p>Meet-ext.geolb.contoso.com</p></td>
<td><p>Pool1ExternalWebFQDN.contoso.com</p>
<p>Pool2ExternalWebFQDN.contoso.com</p></td>
<td><p>Meet.contoso.com alias to Pool1ExternalWebFQDN.contoso.com</p>
<p>Meet.contoso.com alias to Pool2ExternalWebFQDN.contoso.com</p></td>
<td><p>Round Robin between pools</p>
<p>Use primary, connect to secondary if failure</p></td>
</tr>
<tr class="odd">
<td><p>Dialin-int.geolb.contoso.com</p></td>
<td><p>Pool1InternalWebFQDN.contoso.com</p>
<p>Pool2InternalWebFQDN.contoso.com</p></td>
<td><p>Dialin.contoso.com alias to Pool1InternalWebFQDN.contoso.com</p>
<p>Dialin.contoso.com alias to Pool2InternalWebFQDN.contoso.com</p></td>
<td><p>Round Robin between pools</p>
<p>Use primary, connect to secondary if failure</p></td>
</tr>
<tr class="even">
<td><p>Dialin-ext.geolb.contoso.com</p></td>
<td><p>Pool1ExternalWebFQDN.contoso.com</p>
<p>Pool2ExternalWebFQDN.contoso.com</p></td>
<td><p>Dialin.contoso.com alias to Pool1ExternalWebFQDN.contoso.com</p>
<p>Dialin.contoso.com alias to Pool2ExternalWebFQDN.contoso.com</p></td>
<td><p>Round Robin between pools</p>
<p>Use primary, connect to secondary if failure</p></td>
</tr>
<tr class="odd">
<td><p>Lyncdiscoverint-int.geolb.contoso.com</p></td>
<td><p>Pool1InternalWebFQDN.contoso.com</p>
<p>Pool2InternalWebFQDN.contoso.com</p></td>
<td><p>Lyncdiscoverinternal.contoso.com alias to Pool1InternalWebFQDN.contoso.com</p>
<p>Lyncdiscoverinternal.contoso.com alias to Pool2InternalWebFQDN.contoso.com</p></td>
<td><p>Round Robin between pools</p>
<p>Use primary, connect to secondary if failure</p></td>
</tr>
<tr class="even">
<td><p>Lyncdiscover-ext.geolb.contoso.com</p></td>
<td><p>Pool1ExternalWebFQDN.contoso.com</p>
<p>Pool2ExternalWebFQDN.contoso.com</p></td>
<td><p>Lyncdiscover.contoso.com alias to Pool1ExternalWebFQDN.contoso.com</p>
<p>Lyncdiscover.contoso.com alias to Pool2ExternalWebFQDN.contoso.com</p></td>
<td><p>Round Robin between pools</p>
<p>Use primary, connect to secondary if failure</p></td>
</tr>
<tr class="odd">
<td><p>Scheduler-int.geolb.contoso.com</p></td>
<td><p>Pool1InternalWebFQDN.contoso.com</p>
<p>Pool2InternalWebFQDN.contoso.com</p></td>
<td><p>Scheduler.contoso.com alias to Pool1InternalWebFQDN.contoso.com</p>
<p>Scheduler.contoso.com alias to Pool2InternalWebFQDN.contoso.com</p></td>
<td><p>Round Robin between pools</p>
<p>Use primary, connect to secondary if failure</p></td>
</tr>
<tr class="even">
<td><p>Scheduler-ext.geolb.contoso.com</p></td>
<td><p>Pool1ExternalWebFQDN.contoso.com</p>
<p>Pool2ExternalWebFQDN.contoso.com</p></td>
<td><p>Scheduler.contoso.com alias to Pool1ExternalWebFQDN.contoso.com</p>
<p>Scheduler.contoso.com alias to Pool2ExternalWebFQDN.contoso.com</p></td>
<td><p>Round Robin between pools</p>
<p>Use primary, connect to secondary if failure</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## DNS Load Balancing

DNS load balancing is typically implemented at the application level. The application (for example, a client running Lync), tries to connect to a server in a pool by connecting to one of the IP addresses returned from the DNS A and AAAA (if IPv6 addressing is used) record query for the pool fully qualified domain name (FQDN).

For example, if there are three front end servers in a pool named pool01.contoso.com, the following will happen:

  - Clients running Lync query DNS for pool01.contoso.com. The query returns three IP addresses and caches them as follows (not necessarily in this order):
    
    pool01.contoso.com      192.168.10.90
    
    pool01.contoso.com      192.168.10.91
    
    pool01.contoso.com      192.168.10.92

  - The client attempts to establish a Transmission Control Protocol (TCP) connection to one of the IP addresses. If that fails, the client tries the next IP address in the cache.

  - If the TCP connection succeeds, the client negotiates TLS to connect to the primary registrar on pool01.contoso.com.

  - If the client tries all cached entries without a successful connection, the user is notified that no servers running Lync Server 2013 are available at the moment.

<div>


> [!NOTE]  
> DNS-based load balancing is different from DNS round robin (DNS RR) which typically refers to load balancing by relying on DNS to provide a different order of IP addresses corresponding to the servers in a pool. Typically DNS RR only enables load distribution, but does not enable failover. For example, if the connection to the one IP address returned by the DNS A and AAAA (if you are using IPv6 addressing) query fails, the connection fails. Therefore, DNS round robin by itself is less reliable than DNS-based load balancing. You can use DNS round robin in conjunction with DNS load balancing.



</div>

DNS load balancing is used for the following:

  - Load balancing server-to-server SIP to the Edge Servers

  - Load balancing Unified Communications Application Services (UCAS) applications such as Conferencing Auto Attendant, Response Group, and Call Park

  - Preventing new connections to UCAS applications (also known as "draining")

  - Load balancing all client-to-server traffic between clients and Edge Servers

DNS load balancing cannot be used for the following:

  - Client-to-server web traffic to Director or Front End Servers

DNS load balancing and federated traffic:

If multiple DNS records are returned by a DNS SRV query, the Access Edge service always picks the DNS SRV record with the lowest numeric priority and highest numeric weight. The Internet Engineering Task Force document “A DNS RR for specifying the location of services (DNS SRV)” <http://www.ietf.org/rfc/rfc2782.txt> specifies that if there are multiple DNS SRV records defined, priority is first used, then weight. For example DNS SRV record A has a weight of 20 and a priority of 40 and DNS SRV record B has a weight of 10 and priority of 50. DNS SRV record A with priority 40 will be selected. The following rules apply to DNS SRV record selection:

  - Priority is considered first. A client MUST attempt to contact the target host defined by the DNS SRV record with the lowest numbered priority it can reach. Targets with the same priority SHOULD be tried in an order defined by the weight field.

  - The weight field specifies a relative weight for entries with the same priority. Larger weights SHOULD be given a proportionately higher probability of being selected. DNS administrators SHOULD use Weight 0 when there isn’t any server selection to do. In the presence of records containing weights greater than 0, records with weight 0 should have a very small chance of being selected.

If multiple DNS SRV records with equal priority and weight are returned, the Access Edge service will select the SRV record that was received first from the DNS server.

</div>

</div>

<span> </span>

</div>

</div>

</div>

