---
title: 'Lync Server 2013: Setting up reverse proxy servers'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Setting up reverse proxy servers
ms:assetid: 00bc138a-243f-4389-bfa5-9c62fcc95132
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398069(v=OCS.15)
ms:contentKeyID: 48183225
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Setting up reverse proxy servers for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-05-08_

For Microsoft Lync Server 2013 Edge Server deployments, an HTTPS reverse proxy in the perimeter network is required for external clients to access the Lync Server 2013 Web Services (called *Web Components* in Office Communications Server) on the Director and the user’s home pool. Some of the features that require external access through a reverse proxy include the following:

  - Enabling external users to download meeting content for your meetings.

  - Enabling external users to expand distribution groups.

  - Enabling remote users to download files from the Address Book service.

  - Accessing the Lync Web App client.

  - Accessing the Dial-in Conferencing Settings webpage.

  - Enabling external devices to connect to Device Update web service and obtain updates.

  - Enabling mobile applications to automatically discover and use the mobility (Mcx) URLs from the Internet.

  - Enabling the Lync 2013 client, Lync Windows Store app and Lync 2013 Mobile client to locate the Lync Discover (autodiscover) URLs and use Unified Communications Web API (UCWA).

We recommend that you configure your HTTP reverse proxy to publish all Web Services in all pools. Publishing https:// ExternalFQDN/\* publishes all IIS virtual directories for a pool. You need one publishing rule for each Standard Edition server, Front End pool, or Director or Director pool in your organization.

In addition, you need to publish the simple URLs. If the organization has a Director or Director pool, the HTTP reverse proxy listens for HTTP/HTTPS requests to the simple URLs and proxies them to the external Web Services virtual directory on the Director or Director pool. If you have not deployed a Director, you need to designate one pool to handle requests to the simple URLs. (If this is not the user’s home pool, it will redirect them onward to the Web Services on the user’s home pool). The simple URLs can be handled by a dedicated web publishing rule, or you can add it to the public names of the web publishing rule for the Director. You also need to publish the external Autodiscover Service URL.

You can use Microsoft Forefront Threat Management Gateway 2010, Microsoft Internet Security and Acceleration (ISA) Server 2006 SP1, or Internet Information Server 7.0, 7.5 or 8.0 with Application Request Routing (IIS ARR) as a reverse proxy. The detailed steps in this section describe how to configure Forefront Threat Management Gateway 2010, and the steps for configuring ISA Server 2006 are almost identical. Guidance is also provided for IIS ARR. If you are using a different reverse proxy, consult the documentation for that product and map the requirements defined here to the associated features in other reverse proxies.

<div>


> [!IMPORTANT]  
> Internet Information Server Application Request Routing (IIS ARR) is a fully tested and supported option for implementing a reverse proxy for Lync Server 2010 and Lync Server 2013. In November, 2012, Microsoft ceased license sales of ForeFront Threat Management Gateway 2010, or TMG. TMG is still a fully supported product, and is still available for sale on appliances sold by third parties. Also, many third party hardware load balancers and firewalls provide reverse proxy support. For hardware load balancers and firewalls that provide reverse proxy features, check with your vendor for specific instructions on how to configure their product to provide reverse proxy support for Lync Server. You can also view third parties that have submitted documentation for their product to Microsoft. Support is provided by the third party for their solution. To see third parties that are active in providing solutions, see <A href="http://go.microsoft.com/fwlink/?linkid=268730">Infrastructure qualified for Microsoft Lync</A>.



</div>

The following topics and procedures use Forefront Threat Management Gateway 2010 and IIS ARR as the basis for the deployment and configuration procedures.

  - [Configure web farm FQDNs for Lync Server 2013](lync-server-2013-configure-web-farm-fqdns.md)

  - [Configure network adapters in Lync Server 2013](lync-server-2013-configure-network-adapters.md)

  - [Request and configure a certificate for your reverse HTTP proxy in Lync Server 2013](lync-server-2013-request-and-configure-a-certificate-for-your-reverse-http-proxy.md)

  - [Configure web publishing rules for a single internal pool in Lync Server 2013](lync-server-2013-configure-web-publishing-rules-for-a-single-internal-pool.md)

  - [Verify or configure authentication and certification on IIS virtual directories in Lync Server 2013](lync-server-2013-verify-or-configure-authentication-and-certification-on-iis-virtual-directories.md)

  - [Create DNS records for reverse proxy servers in Lync Server 2013](lync-server-2013-create-dns-records-for-reverse-proxy-servers.md)

  - [Verify access through your reverse proxy in Lync Server 2013](lync-server-2013-verify-access-through-your-reverse-proxy.md)

<div>

## Before You Begin

To successfully deploy Forefront Threat Management Gateway 2010 as your reverse proxy, you need to setup and configure a server, using the prerequisites and hardware requirements defined in the Forefront Threat Management Gateway 2010 documentation. See the following topic set to properly configure the hardware and to install Forefront Threat Management Gateway 2010 on the server before proceeding.

  - <span></span>  
    [Forefront Threat Management Gateway (TMG) 2010](http://go.microsoft.com/fwlink/?linkid=291292)

  - <span></span>  
    [Forefront TMG 2010 hardware recommendations](http://go.microsoft.com/fwlink/?linkid=291293)

To successfully deploy IIS ARR as your reverse proxy, review the following topics to configure the hardware and the prerequisite software.

  - <span></span>  
    To install IIS on Windows Server 2008 or Windows Server 2008 R2, see [Installing IIS 7 on Windows Server 2008 or Windows Server 2008 R2](http://go.microsoft.com/fwlink/?linkid=291296)

  - <span></span>  
    To install IIS on Windows Server 2012, see [Installing IIS 8 on Windows Server 2012](http://go.microsoft.com/fwlink/?linkid=291297)

  - <span></span>  
    To install IIS on Windows Server 2012 R2, see [Installing IIS 8.5 on Windows Server 2012 R2](http://go.microsoft.com/fwlink/?linkid=330687)

  - <span></span>  
    To download the Application Request Routing extension for IIS, follow the instructions at [Application Request Routing v2.5 Download](http://go.microsoft.com/fwlink/?linkid=291298)

  - <span></span>  
    To install ARR, for the instructions at [Install Application Request Routing Version 2](http://go.microsoft.com/fwlink/?linkid=291299)
    
    <div>
    

    > [!NOTE]  
    > The instructions currently posted are for ARR 2.0. For installation of the extension, there is no difference between the two versions.

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

