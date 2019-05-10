---
title: 'Lync Server 2013: Scenarios for reverse proxy'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Scenarios for reverse proxy
ms:assetid: 13108f59-a660-4ff1-8404-079d1cb646f2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204691(v=OCS.15)
ms:contentKeyID: 48183468
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Scenarios for reverse proxy in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-01-21_

Reverse proxies are required in Lync Server 2013 for providing access to services and resources such as the meeting and dial-in Simple URLs, address book, meeting content, distribution list expansion, mobility services, and others. The typical reverse proxy scenario in Lync Server 2013 is to allow external clients (for example, the desktop client or Lync Web App client) access to the Director or Front End Server external Web Services.

**Reverse proxy and external web services**

![13142405-d5c9-45b7-a8b7-a8c89f09c97c](images/JJ204932.13142405-d5c9-45b7-a8b7-a8c89f09c97c(OCS.15).jpg "13142405-d5c9-45b7-a8b7-a8c89f09c97c")

During the planning phase, you define the requirements for the reverse proxy in a Lync Server 2013 deployment. The reverse proxy enables access to features for the following external clients:

  - Microsoft Lync 2013 desktop client

  - Microsoft Lync Web App

  - Microsoft Lync Mobile

  - Lync Windows Store app

When planning your Lync Server 2013 deployment, you map the actual requirements for Lync Server 2013 to the reverse proxy features.

1.  External clients will connect to the reverse proxy on port TCP 443 and will use secure socket layer (SSL) or transport layer security (TLS). Microsoft Lync Mobile clients can connect on port TCP 80, but only when performing the initial connection to the Lync discover services and the administrator has configured the proper domain name system (DNS) CNAME (or alias) records, and accepts that this communication will not be encrypted.

2.  Lync Server 2013 external web services (deployed on the Front End Server and/or the Director) expect a connection from a reverse proxy on port TCP 4443, and it expects that the connection will be SSL/TLS.
    
    <div>
    

    > [!IMPORTANT]  
    > The suggested default listening ports for the external web services are TCP 8080 for HTTP traffic, and TCP 4443 for HTTPS traffic. Topology Builder provides an opportunity to override the defaults and define your own listening ports for the external web services. It’s important to note that the reverse proxy communicates with the external web services, and the external clients communicate with the reverse proxy. The external client communicates with the reverse proxy on port TCP 443, but you can redefine what port the reverse proxy communicates with the external web services on. The options in Topology Builder to override the default listening ports for the web services allows you to resolve listening port conflicts that may arise in your infrastructure.

    
    </div>

3.  Lync Server 2013 external web services expect an unmodified Host Header from the client to identify what service and web server directory the client is attempting to use. Requests should appear as if they came from the reverse proxy

4.  The external web services use defined web server virtual directories (vDir) that provide the services offered to clients. Specific externally identifiable web services are:
    
      - The “Meet” vDir for web conference meetings
    
      - The “Dialin” vDir for phone access and phone conferencing
    
      - The “Autodiscover” vDir for Lync Windows Store app, Lync Mobile, and the desktop client Lync 2013. Autodiscover in Lync Server 2013 is known by the DNS name “lyncdiscover”
    
      - Services not defined are accessed by the external client by direct calls to the external web services. For example, distribution group expansion (DLX) and the address book service (ABS) are accessed by direct calls to the external web services and associated vDirs. The client knows the actual path to the vDir and constructs a uniform record locator (URL) based on this information. The client would access the address book service using a URL similar to `https://externalweb.contoso.com/abs/handler`
    
      - The Office Web Apps Server when conferencing is defined and configured as part of the Lync Server topology
        
        <div>
        

        > [!NOTE]  
        > The Office Web Apps Server is a separate role server and is not configured as part of the external web services. This server is separately published for client access.

        
        </div>

5.  Define SSL bridging for each service. The external port TCP 443 is mapped to the external web services port of TCP 4443. For unencrypted HTTP, port TCP 80 is mapped to the external web services port TCP 8080

6.  Plan for reverse proxy listeners to publish web server resources

7.  Request and configure the certificate for the reverse proxy based on the services that will be offered. If configured with the correct subject alternative names, this certificate can be shared by all configured listeners on the reverse proxy server

Resources available for planning your reverse proxy deployment:

  - [Data collection in Lync Server 2013](lync-server-2013-data-collection.md)

  - [Certificate summary - Reverse proxy in Lync Server 2013](lync-server-2013-certificate-summary-reverse-proxy.md)

  - [Port summary - Reverse proxy in Lync Server 2013](lync-server-2013-port-summary-reverse-proxy.md)

  - [DNS summary - Reverse proxy in Lync Server 2013](lync-server-2013-dns-summary-reverse-proxy.md)

</div>

<span> </span>

</div>

</div>

</div>

