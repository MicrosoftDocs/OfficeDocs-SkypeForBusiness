---
title: 'Lync Server 2013: Autodiscover service requirements'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Autodiscover service requirements
ms:assetid: 0ac5dbf7-9acd-4d25-b21a-932022b8b983
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh690012(v=OCS.15)
ms:contentKeyID: 48183368
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Autodiscover service requirements for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-25_

The Microsoft Lync Server 2013 Autodiscover Service runs on the Director and Front End pool servers, and when published in DNS, can be used by mobile devices running Lync Mobile to locate mobility services. Before mobile devices running Lync Mobile can take advantage of automatic discovery, you need to modify certificate subject alternative name lists on any Director and Front End Server running the Autodiscover Service. In addition, it may be necessary to modify the subject alternative name lists on certificates used for external web service publishing rules on reverse proxies.

For details about the subject alternative name entries that are required for Directors, Front End Servers, and reverse proxies, see [Technical requirements for mobility in Lync Server 2013](lync-server-2013-technical-requirements-for-mobility.md) in Planning for Mobility.

The decision about using subject alternative name lists on reverse proxies is based on whether you publish the Autodiscover Service on port 80 or on port 443:

  - **Published on port 80**   No certificate changes are required if the initial query to the Autodiscover Service occurs over port 80. This is because mobile devices running Lync will access the reverse proxy on port 80 externally and then be redirected to a Director or Front End Server on port 8080 internally. For details, see the “Initial Autodiscover Process Using Port 80” section later in this topic.

  - **Published on port 443**   The subject alternative name list on certificates used by the external web services publishing rule must contain a *lyncdiscover.\<sipdomain\>* entry for each SIP domain within your organization.

Reissuing certificates using an internal certificate authority is typically a simple process but for public certificates used on the web service publishing rule, adding multiple subject alternative name entries can become expensive. To work around this issue, we support the initial automatic discovery connection over port 80, which is then redirected to port 8080 on the Director or Front End Server.

For example, assume that a mobile client running Lync Mobile is configured to sign in to Lync Server 2013 using the automatic discovery feature using HTTP for the initial request.

<div>

## Initial Autodiscover Process for Mobile Devices Using Port 80

1.  Mobile device running Lync Mobile looks up lyncdiscover.contoso.com using DNS, where an A record exists.

2.  External DNS returns the IP address for the external web services to the client.

3.  Mobile device running Lync Mobile sends request http://lyncdiscover.contoso.com?sipuri=lyncUser1@contoso.com to the reverse proxy

4.  The web publishing rule will bridge the request from port 80 externally to port 8080 internally, which will then route it to either a Director or Front End Server.
    
    Since the request is HTTP and not HTTPS, no modifications are needed to the certificate on the external web service publishing rule to support the Autodiscover Service.

5.  The Autodiscover Service returns the external web service URLs (in HTTPS format).

6.  The mobile device running Lync Mobile can then reconnect to the reverse proxy on port 443 and is redirected over 4443 to the mobility service running on the user’s home pool.
    
    Since the HTTPS query is to the external web services URL vs. the Autodiscover Service URL, it succeeds because the certificate will already contain subject alternative name entries for the external web services fully qualified domain names (FQDNs).
    
    In this scenario, there are no certificate changes required to support mobility.
    
    <div>
    

    > [!NOTE]  
    > If the target web server has a certificate that does not have a matching value for lyncdiscover.contoso.com as a subject alternative name list value:<BR>a.&nbsp;&nbsp;&nbsp;Web server responds with a “Server Hello” and no certificate.<BR>b.&nbsp;&nbsp;&nbsp;Mobile device running Lync Mobile immediately terminates the session.<BR>If the target web server has a certificate that includes lyncdiscover.contoso.com as a subject alternative name list value:<BR>a.&nbsp;&nbsp;&nbsp;Web server responds with a “Server hello” and a certificate.<BR>b.&nbsp;&nbsp;&nbsp;Mobile device running Lync Mobile validates the certificate and completes the handshake.

    
    </div>

To support an initial connection to the Autodiscover Service using port 80 on your reverse proxy server, you can create an http publishing rule similar to this example for a Forefront Threat Management Gateway 2010 reverse proxy web publishing rule:

1.  Create a new web publishing rule (for example, **Lync Server Autodiscover (HTTP)**).

2.  In **Public Name**, enter lyncdiscover.contoso.com.

3.  On the **Bridging** tab, select only the option to bridge requests from Port 80 to Port 8080.

4.  On the **Authentication** tab, select **No authentication**, and **Client cannot authenticate directly**.

5.  Commit changes, and move the rule to the top of the list of Lync rules (first in processing order).

</div>

<div>

## Mobility for the Split Domain Deployment

A shared SIP address space, also known as a *split-domain*, or a *hybrid deployment* is a configuration where users are deployed across an on-premise deployment and an online environment. The desired outcome is to have a user, regardless of where their home server is located (on-premise or online), to log into the deployment and be redirected to their home server location. To accomplish this, the Autodiscover feature of Microsoft Lync Server 2013 is used to redirect the online user to the online topology. This is done by configuring the Autodiscover uniform resource locator (URL) by using the Lync Server Management Shell and the cmdlets **Get-CsHostingProvider** and **Set-CsHostingProvider**.

You will need to collect and record the following deployed attributes:

  - From the Lync Server Management Shell, type
    
        Get-CsHostingProvider

  - In the results, find the online provider with the attribute **ProxyFQDN**. For example, sipfed.online.lync.com

  - Record the value of the ProxyFQDN

  - Enable federation in the on-premise Lync Server Control Panel, allowing federation with the online provider

  - Enable federation for the online provider. By default, all online users are enabled for domain federation and can communicate with all domains

  - If you will define blocked and allowed domains, determine the domains that you will explicitly allow or explicitly block

  - For online federation, you must plan for firewall exceptions, certificates and DNS host (A or AAAA, if using IPv6) records. Additionally, you must configure federation policies. For details, see [Planning for Lync Server 2013 and Office Communications Server federation](lync-server-2013-planning-for-lync-server-and-office-communications-server-federation.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

