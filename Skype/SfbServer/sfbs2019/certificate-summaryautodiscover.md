---
title: "Certificate summary - Autodiscover in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 16ac96bb-882a-4141-b75c-9530637548d9
description: "The Lync Server 2013 Autodiscover Service runs on the Director and Front End pool servers, and when published in DNS, can be used by Lync clients to locate server and user services. If you are upgrading from Lync Server 2010 and did not deploy Mobility, before clients can use automatic discovery, you must modify certificate subject alternative name lists on any Director and Front End Server running the Autodiscover Service. In addition, it may be necessary to modify the subject alternative name lists on certificates used for external web service publishing rules on reverse proxies."
---

# Certificate summary - Autodiscover in Lync Server 2013
[]
The Lync Server 2013 Autodiscover Service runs on the Director and Front End pool servers, and when published in DNS, can be used by Lync clients to locate server and user services. If you are upgrading from Lync Server 2010 and did not deploy Mobility, before clients can use automatic discovery, you must modify certificate subject alternative name lists on any Director and Front End Server running the Autodiscover Service. In addition, it may be necessary to modify the subject alternative name lists on certificates used for external web service publishing rules on reverse proxies.
  
The decision about whether to use subject alternative name lists on reverse proxies is based on whether you publish the Autodiscover Service on port 80 or on port 443:
  
- **Published on port 80** No certificate changes are required if the initial query to the Autodiscover Service occurs over port 80. This is because mobile devices running Lync will access the reverse proxy on port 80 externally and then be bridged to a Director or Front End Server on port 8080 internally. For details, see the "Initial Autodiscover Process Using Port 80" section [Technical requirements for mobility in Lync Server 2013](technical-requirements-for-mobility.md).
    
- **Published on port 443** The subject alternative name list on certificates used by the external web services publishing rule must contain a lyncdiscover.\<sipdomain\> entry for each SIP domain within your organization. 
    
    > [!IMPORTANT]
    > We highly recommend using HTTPS over HTTP. HTTPS uses certificates to encrypt traffic. HTTP does not provide for encryption, and any data sent will be plain text. 
  
Reissuing certificates by using an internal certificate authority is typically a simple process. But for public certificates used on the web service publishing rule, adding multiple subject alternative name entries can become expensive. To work around this issue, we support the initial automatic discovery connection over port 80, which is then redirected to port 8080 on the Director or Front End Server. 
  
> [!NOTE]
> If your Lync Server 2013 infrastructure uses internal certificates that are issued from an internal certification authority (CA) and you plan to support mobile devices connecting wirelessly, either the root certificate chain from the internal CA must be installed on the mobile devices or you must change to a public certificate on your Lync Server 2013 infrastructure. 
  
This topic describes the added subject alternative names required for the Director, Front End Server and reverse proxy. Only the added subject alternative names (SAN) are referenced. Refer to the planning sections for guidance on the other entries on certificates. For details, see [Scenarios for the Director in Lync Server 2013](scenarios-for-the-director.md), [Scenarios for external user access in Lync Server 2013](scenarios-for-external-user-access.md), and [Scenarios for reverse proxy in Lync Server 2013](scenarios-for-reverse-proxy.md).
  
The following tables define the Autodiscover SAN entries for the Director pool, the Front End pool, and the reverse proxy:
  
**Director Pool Certificate Requirements**

|**Description**|**Subject alternative name entry**|
|:-----|:-----|
|Internal Autodiscover Service URL  <br/> |SAN=lyncdiscoverinternal. _\<internal domain name\>_ <br/> |
|External Autodiscover Service URL  <br/> |SAN=lyncdiscover. _\<sipdomain\>_ <br/> |
   
> [!NOTE]
> You assign the newly updated certificate with the new SAN entry to the Default certificate. Alternatively, you can use SAN=*. _\<sipdomain\>_. 
  
**Front End Pool Certificate Requirements**

|**Description**|**Subject alternative name entry**|
|:-----|:-----|
|Internal Autodiscover Service URL  <br/> |SAN=lyncdiscoverinternal. _\<internal domain name\>_ <br/> |
|External Autodiscover Service URL  <br/> |SAN=lyncdiscover. _\<sipdomain\>_ <br/> |
   
> [!NOTE]
> You assign the newly updated certificate with the new SAN entry to the Default certificate. Alternatively, you can use SAN=\*. _\<sipdomain\>_
  
**Reverse Proxy (Public CA) Certificate Requirements**

|**Description**|**Subject alternative name entry**|
|:-----|:-----|
|External Autodiscover Service URL  <br/> |SAN=lyncdiscover. _\<sipdomain\>_ <br/> |
   
> [!NOTE]
> You assign the newly updated certificate with the new SAN entry to the SSL Listener on the reverse proxy. 
  

