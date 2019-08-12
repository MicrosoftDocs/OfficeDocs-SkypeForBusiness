---
title: 'Lync Server 2013: Certificate requirements for external user access'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Certificate requirements for external user access
ms:assetid: d45b6b10-556f-4b10-b1a7-fb0d0a64a498
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398920(v=OCS.15)
ms:contentKeyID: 48185503
ms.date: 03/29/2016
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Certificate requirements for external user access in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-03-29_

Microsoft Lync Server 2013 communications software supports the use of a single public certificate for access and web conferencing Edge external interfaces, plus the A/V Authentication service. The Edge internal interface typically uses a private certificate issued by an internal certification authority (CA), but can also use a public certificate, provided that it is from a trusted public CA. The reverse proxy in your deployment uses a public certificate and encrypts the communication from the reverse proxy to clients and the reverse proxy to internal servers by using HTTP (that is, Transport Layer Security over HTTP).

Following are the requirements for the public certificate used for access and web conferencing Edge external interfaces, and the A/V authentication service:

  - The certificate must be issued by an approved public CA that supports subject alternative name. For details, see Microsoft Knowledge Base article 929395, "Unified Communications Certificate Partners for Exchange Server and for Communications Server," at [http://go.microsoft.com/fwlink/p/?linkId=202834](http://go.microsoft.com/fwlink/p/?linkid=202834).

  - If the certificate will be used on an Edge pool, it must be created as exportable, with the same certificate used on each Edge Server in the Edge pool. The exportable private key requirement is for the purposes of the A/V Authentication service, which must use the same private key across all Edge Servers in the pool.

  - If you want to maximize the uptime for your Audio/Video services, review the certificate requirements for implementing a decoupled A/V Edge service certificate (that is, a separate A/V Edge service certificate from the other External Edge certificate purposes). For details, see [Changes in Lync Server 2013 that affect Edge Server planning](lync-server-2013-changes-in-lync-server-that-affect-edge-server-planning.md), [Plan for Edge Server certificates in Lync Server 2013](lync-server-2013-plan-for-edge-server-certificates.md) and [Staging AV and OAuth certificates in Lync Server 2013 using -Roll in Set-CsCertificate](lync-server-2013-staging-av-and-oauth-certificates-using-roll-in-https://docs.microsoft.com/powershell/module/skype/Set-CsCertificate).

  - The subject name of the certificate is the Access Edge service external interface fully qualified domain name (FQDN) or hardware load balancer VIP (for example, access.contoso.com). ). The subject name can’t have a wildcard character, it must be an explicit name.
    
    <div>
    

    > [!NOTE]  
    > For Lync Server 2013, this is no longer a requirement, but it is still recommended for compatibility with Office Communications Server.

    
    </div>

  - The subject alternative name list contains the FQDNs of the following:
    
      - The Access Edge service external interface or hardware load balancer VIP (for example, sip.contoso.com).
        
        <div>
        

        > [!NOTE]  
        > Even though the certificate subject name is equal to the access Edge FQDN, the subject alternative name must also contain the access Edge FQDN because Transport Layer Security (TLS) ignores the subject name and uses the subject alternative name entries for validation.

        
        </div>
    
      - The web conferencing Edge external interface or hardware load balancer VIP (for example, webcon.contoso.com).
    
      - If you are using client auto-configuration or federation, also include any SIP domain FQDNs used within your company (for example, sip.contoso.com, sip.fabrikam.com).
    
      - The A/V Edge service does not use the subject name or the subject alternative names entries.
    
    <div>
    

    > [!NOTE]  
    > The order of the FQDNs in the subject alternative names list does not matter.

    
    </div>

If you are deploying multiple, load-balanced Edge Servers at a site, the A/V authentication service certificate that is installed on each Edge Server must be from the same CA and must use the same private key. Note that the certificate's private key must be exportable, regardless of whether it is used on one Edge Server or many Edge Servers. It must also be exportable if you request the certificate from any computer other than the Edge Server. Because the A/V authentication service does not use the subject name or subject alternative name, you can reuse the access Edge certificate as long as the subject name and subject alternative name requirements are met for the access Edge and the web conferencing Edge and the certificate’s private key is exportable.

Requirements for the private (or public) certificate used for the Edge internal interface are as follows:

  - The certificate can be issued by an internal CA or an approved public certificate CA.

  - The subject name of the certificate is typically the Edge internal interface FQDN or hardware load balancer VIP (for example, lsedge.contoso.com). However, you can use a wildcard certificate on the Edge internal.

  - No subject alternative name list is required.

The reverse proxy in your deployment services requests for:

  - External user access to meeting content for meetings

  - External user access to expand and display members of distribution groups

  - External user access to downloadable files from the Address Book Service

  - External user access to the Lync Web App client

  - External user access to the Dial-in Conferencing Settings web page

  - External user access to the Location Information Service

  - External device access to the Device Update Service and obtain updates

The reverse proxy publishes the internal server Web Components URLs. The Web Components URLs are defined on the Director, Front End Server or Front End pool as the **External web services** in Topology Builder.

Wildcard entries are supported in the subject alternative name field of the certificate assigned to the reverse proxy. For details about how to configure the certificate request for the reverse proxy, see [Request and configure a certificate for your reverse HTTP proxy in Lync Server 2013](lync-server-2013-request-and-configure-a-certificate-for-your-reverse-http-proxy.md).

<div>

## See Also


[Wildcard certificate support in Lync Server 2013](lync-server-2013-wildcard-certificate-support.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

