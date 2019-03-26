---
title: 'Lync Server 2013: Technical requirements for mobility'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Technical requirements for mobility
ms:assetid: 831be681-4de0-4e42-b04f-8879ca4dcd23
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh690030(v=OCS.15)
ms:contentKeyID: 48184679
ms.date: 07/24/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Technical requirements for mobility in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-07-24_

    Some information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.

Mobile users encounter various mobile application scenarios that require special planning. For example, someone might start using a mobile application while away from work by connecting through the 3G network, then switch to the corporate Wi-Fi network when arriving at work, and then switch back to 3G when leaving the building. You need to plan your environment to support such network transitions and guarantee a consistent user experience. This section describes the infrastructure requirements that you must have in order to support mobile applications and automatic discovery of mobility resources.

<div>


> [!NOTE]  
> Although mobile applications can also connect to other Lync Server 2013 services, the requirement to send all mobile application web requests to the same external web fully qualified domain name (FQDN) applies only to the Lync Server 2013 Mobility Service. Other mobility services do not require this configuration.



</div>

The requirement for cookie affinity in hardware load balancers is dramatically reduced, and you substitute Transmission Control Protocol (TCP) affinity if you are using the Lync Mobile delivered with Lync Server 2013. Cookie affinity can still be used, but the web services no longer require it.

<div>


> [!IMPORTANT]  
> All Mobility Service traffic goes through the reverse proxy, regardless of where the origination point is—internal or external. In the case of a single reverse proxy or a farm of reverse proxies, or a device that is providing the reverse proxy function, an issue can arise when the internal traffic is egressing through an interface and attempting to immediately ingress on the same interface. This often leads to a Security rule violation known as TCP packet spoofing or just spoofing. <EM>Hair pinning</EM> (the egress and immediate ingress of a packet or series of packets) must be allowed in order for mobility to function. One way to resolve this issue is to use a reverse proxy that is separate from the firewall (the spoofing prevention rule should always be enforced at the firewall, for security purposes). The hairpin can occur at the external interface of the reverse proxy instead of the firewall external interface. You detect the spoofing at the firewall, and relax the rule at the reverse proxy, thereby allowing the hairpin that mobility requires.<BR>Use the Domain Name System (DNS) host or CNAME records to define the reverse proxy for the hairpin behavior (not the firewall), if at all possible.



</div>

Lync Server 2013 supports mobility services for Lync 2010 Mobile and Lync 2013 mobile clients. Both clients use the Lync Server 2013 Autodiscover Service to find its mobility entry point, but differ on which mobility service they use. Lync 2010 Mobile uses the Mobility Service known as *Mcx*, introduced with the Cumulative Update for Lync Server 2010: November 2011. Lync 2013 mobile clients use the Unified Communications Web API, or *UCWA*, as their mobility service provider.

<div>

## Internal and External DNS Configuration

The Mobility Services Mcx (introduced with the Cumulative Update for Lync Server 2010: November 2011) and UCWA (introduced in the Cumulative Updates for Lync Server 2013: February 2013) use DNS in the same way.

When you use Automatic Discovery, mobile devices use DNS to locate resources. During the DNS lookup, a connection is first attempted to the FQDN that is associated with the internal DNS record (lyncdiscoverinternal.\<internal domain name\>). If a connection cannot be made by using the internal DNS record, a connection is attempted by using the external DNS record (lyncdiscover.\<sipdomain\>). A mobile device that is internal to the network connects to the internal Autodiscover Service URL, and a mobile device that is external to the network connects to the external Autodiscover Service URL. External Autodiscover requests go through the reverse proxy. The Lync Server 2013 Autodiscover Service returns all Web Services URLs for the user's home pool, including the Mobility Service (Mcx and UCWA) URLs. However, both the internal Mobility Service URL and the external Mobility Service URL are associated with the external Web Services FQDN. Therefore, regardless of whether a mobile device is internal or external to the network, the device always connects to the Lync Server 2013 Mobility Service externally through the reverse proxy.

<div>


> [!NOTE]  
> It is important to understand that your deployment can consist of multiple distinct namespaces for internal and external use. Your SIP domain name may be different than the internal deployment domain name. For example, your SIP domain may be <STRONG>contoso.com</STRONG>, while your internal deployment may be <STRONG>contoso.net</STRONG>. Users who log in to Lync Server will use the SIP domain name, such as <STRONG>john@contoso.com</STRONG>. When addressing the external web services (defined in Topology Builder as <STRONG>External web services</STRONG>), the domain name and the SIP domain name will be consistent, as defined in DNS. When addressing the internal Web services (defined in Topology Builder as <STRONG>Internal web services</STRONG>), the default name of the internal web services will be the FQDN of the Front End Server, Front End pool, Director, or Director pool. You have the option to override the internal web services name. You should use the internal domain name (and not the SIP domain name) for internal web services and define the DNS host A (or, for IPv6, AAAA) record to reflect the overridden name. For example, the default internal web services FQDN may be <STRONG>pool01.contoso.net</STRONG>. An overridden internal web services FQDN may be <STRONG>webpool.contoso.net</STRONG>. Defining the web services in this way helps to ensure that the internal and external locality of the services—and not the locality of the user who is using them—is observed.<BR>However, because the web services are defined in Topology Builder and the internal web services name can be overridden, as long as the resulting web services name, the certificate that validates it, and the DNS records that define it, are consistent, you can define the internal web services with any domain name—including the SIP domain name—that you want. Ultimately, the resolution for the name to the IP address is determined by DNS host records and a consistent namespace.<BR>For the purposes of this topic and the examples, the internal domain name is used to illustrate the topology and the DNS definitions.



</div>

The following diagram illustrates the flow of mobile application web requests for the Mobility Service and for the Autodiscover Service when using an internal and external DNS configuration.

**Mobility service flow using AutoDiscover**

![cdb96424-96f2-4abf-88d7-1d32d1010ffd](images/Hh690030.cdb96424-96f2-4abf-88d7-1d32d1010ffd(OCS.15).jpg "cdb96424-96f2-4abf-88d7-1d32d1010ffd")

<div>


> [!NOTE]  
> The diagram illustrates generic web services. A virtual directory named Mobility depicts the Mobility services Mcx and/or UCWA. If you have not applied the Cumulative Updates for Lync Server 2013: February 2013, you may or may not have the virtual directory Ucwa defined on your internal and external Web services. You will have a virtual directory Autodiscover, and you may have a virtual directory Mcx.<BR>Autodiscover and the discovery of services work the same way, regardless of the mobility services technology that you have deployed.



</div>

To support mobile users from both inside and outside the corporate network, your internal and external web FQDNs must meet some prerequisites. In addition, you may need to meet other requirements, depending on the features you choose to implement:

  - New DNS, CNAME or A (host, if IPv6, AAAA) records, for automatic discovery.

  - New firewall rule, if you want to support push notifications through your Wi-Fi network.

  - Subject alternative names on internal server certificates and reverse proxy certificates, for automatic discovery.

  - Front End Server hardware load balancer configuration changes source affinity.

Your topology must meet the following requirements to support the Mobility Service and the Autodiscover Service:

  - The Front End pool internal web FQDN must be distinct from the Front End pool external web FQDN.

  - The internal web FQDN must only resolve to and be accessible from inside the corporate network.

  - The external web FQDN must only resolve to and be accessible from the Internet.

  - For a user who is inside the corporate network, the Mobility Service URL must be addressed to the external web FQDN. This requirement is for the Mobility Service and applies only to this URL.

  - For a user who is outside the corporate network, the request must go to the external web FQDN of the Front End pool or Director.

If you support automatic discovery, you need to create the following DNS records for each SIP domain:

  - An internal DNS record to support mobile users who connect from within your organization's network.

  - An external, or public, DNS record to support mobile users who connect from the Internet.

The internal automatic discovery URL should not be addressable from outside your network. The external automatic discovery URL should not be addressable from within your network. However, if you cannot meet this requirement for the external URL, mobile client functionally will probably not be affected, because the internal URL is always tried first.

The DNS records can be either CNAME records or A (host, if IPv6, AAAA) records.

<div>


> [!NOTE]  
> Mobile device clients do not support multiple Secure Sockets Layer (SSL) certificates from different domains. Therefore, CNAME redirection to different domains is not supported over HTTPS. For example, a DNS CNAME record for lyncdiscover.contoso.com that redirects to an address of director.contoso.net is not supported over HTTPS. In such a topology, a mobile device client needs to use HTTP for the first request, so that the CNAME redirection is resolved over HTTP. Subsequent requests then use HTTPS. To support this scenario, you need to configure your reverse proxy with a web publishing rule for port 80 (HTTP). For details, see "To create a web publishing rule for port 80" in <A href="lync-server-2013-configuring-the-reverse-proxy-for-mobility.md">Configuring the reverse proxy for mobility in Lync Server 2013</A>.<BR>CNAME redirection to the same domain is supported over HTTPS. In this case, the destination domain's certificate covers the originating domain.



</div>

For details about the DNS records required for your scenario, see [DNS summary - Autodiscover in Lync Server 2013](lync-server-2013-dns-summary-autodiscover.md).

</div>

<div>

## Port and Firewall Requirements

If you support push notifications and want Apple mobile devices to receive push notifications over your Wi-Fi network, you also need to open port 5223 on your enterprise Wi-Fi network. Port 5223 is an outbound TCP port used by the Apple Push Notification Service (APNS). The mobile device initiates the connection. For details, see [http://support.apple.com/kb/TS1629](http://support.apple.com/kb/ts1629) .

<div>


> [!WARNING]  
> An Apple device using the Lync 2013 Mobile client does not require push notifications.



</div>

Note that if a user is homed on a Survivable Branch Appliance (SBA) then the following ports are required:

  - UcwaSipExternalListeningPort requires port 5088

  - UcwaSipPrimaryListeningPort requires port 5089

For additional details and guidance on port and protocol requirements for Autodiscover, see [Port summary - Autodiscover in Lync Server 2013](lync-server-2013-port-summary-autodiscover.md).

</div>

<div>

## Certificate Requirements

If you support automatic discovery for Lync mobile clients, you need to modify the subject alternative name lists on certificates to support secure connections from the mobile clients. You need to request and assign new certificates, adding the subject alternative name entries described in this section, for each Front End Server and Director that runs the Autodiscover Service. The recommended approach is to also modify the subject alternative names lists on certificates for your reverse proxies. You need to add subject alternative name entries for every SIP domain in your organization.

Reissuing certificates by using an internal certificate authority is typically a simple process, but adding multiple subject alternative name entries to public certificates used by the reverse proxy can be expensive. If you have many SIP domains, making the addition of subject alternative names very expensive, you can configure the reverse proxy to make the initial Autodiscover Service request over port 80 using HTTP, instead of port 443 using HTTPS (the default configuration). The request is then redirected to port 8080 on the Director or Front End pool. When you publish the initial Autodiscover Service request on port 80, you do not need to change certificates for the reverse proxy, because the request uses HTTP rather than HTTPS. This approach is supported, but we do not recommend it.

</div>

<div>

## Internet Information Services (IIS) Requirements

We recommend that you use IIS 7.5, IIS 8.0, or IIS 8.5 for mobility. The Mobility Service installer sets flags in ASP.NET to improve performance. IIS 7.5 is installed by default on Windows Server 2008 R2, IIS 8.0 is installed on Windows Server 2012, and IIS 8.5 is installed on Windows Server 2012 R2. The Mobility Service installer automatically changes the ASP.NET settings.

</div>

<div>

## Hardware Load Balancer Requirements

On the hardware load balancer that is supporting the Front End pool, the external Web Services virtual IPs (VIPs) for Web Services traffic must be configured for source. Source affinity helps to ensure that multiple connections from a single client are sent to one server to maintain session state. For details about affinity requirements, see [Load balancing requirements for Lync Server 2013](lync-server-2013-load-balancing-requirements.md).

If you plan to support Lync mobile clients only over your internal Wi-Fi network, you should configure the internal Web Services VIPS for source as described for external Web Services VIPs. In this situation, you should use source\_addr (or TCP) affinity for the internal Web Services VIPs on the hardware load balancer. For details, see [Load balancing requirements for Lync Server 2013](lync-server-2013-load-balancing-requirements.md).

</div>

<div>

## Reverse Proxy Requirements

If you support automatic discovery for Lync mobile clients, you need to update the current publishing rule as follows:

  - If you decide to update the subject alternative names lists on the reverse proxy certificates and use HTTPS for the initial Autodiscover Service request, you must update the web publishing rule for lyncdiscover.\<sipdomain\>. Typically, this is combined with the publishing rule for the external Web Services URL on the Front End pool.

  - If you decide to use HTTP for the initial Autodiscover Service request so that you do not need to update the subject alternative names list on the reverse proxy certificates, you must create a new web publishing rule for port HTTP/TCP 80, if one does not already exist. If a rule for HTTP/TCP 80 does already exist, you can update that rule to include the lyncdiscover.\<sipdomain\> entry.

</div>

</div>

<span> </span>

</div>

</div>

</div>

