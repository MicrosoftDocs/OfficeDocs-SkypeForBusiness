---
title: "DNS summary - Autodiscover in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b336a2ae-0e58-4b74-b606-aedbbd411587
description: "Autodiscover is a flexible service in that it will accept communication over HTTP or HTTPS. To accomplish this, the domain name system (DNS) and the certificates used by servers that host the Autodiscover service must be configured correctly. Certificate requirements are covered in Certificate summary - Autodiscover in Lync Server 2013."
---

# DNS summary - Autodiscover in Lync Server 2013
[]
Autodiscover is a flexible service in that it will accept communication over HTTP or HTTPS. To accomplish this, the domain name system (DNS) and the certificates used by servers that host the Autodiscover service must be configured correctly. Certificate requirements are covered in [Certificate summary - Autodiscover in Lync Server 2013](certificate-summaryautodiscover.md).
  
> [!IMPORTANT]
> DNS lookup logic for the Lync Server clients uses a specific order of resolution. You should always include both the lyncdiscoverinternal.\<domain\> and the lyncdiscover.\<domain\> in your DNS. Excluding the lyncdiscoverinternal.\<domain\> record will cause internal clients to fail to connect to the intended services or receive the incorrect Autodiscover response. 
  
**Internal DNS Records**

|**Record type**|**Host name**|**Resolves to**|
|:-----|:-----|:-----|
|CNAME  <br/> |Lyncdiscoverinternal. _\<internal domain name\>_ <br/> |Internal Web Services FQDN for your Director pool, if you have one, or for your Front End pool if you do not have a Director.  <br/> |
|A (host, if IPv6, AAAA)  <br/> |lyncdiscoverinternal. _\<internal domain name\>_ <br/> |Internal Web Services IP address (virtual IP (VIP) address if you use a load balancer) of your Director pool, if you have one, or of your Front End pool if you do not have a Director.  <br/> |
   
You need to create one of the following external DNS records:
  
**External DNS Records**

|**Record type**|**Host name**|**Resolves to**|
|:-----|:-----|:-----|
|CNAME  <br/> |lyncdiscover. _\<sipdomain\>_ <br/> |External Web Services FQDN for your Director pool, if you have one, or for your Front End pool if you do not have a Director.  <br/> |
|A (host, if IPv6, AAAA)  <br/> |lyncdiscover. _\<sipdomain\>_ <br/> |External or public IP address of the reverse proxy.  <br/> |
   
> [!NOTE]
> External traffic goes through the reverse proxy. 
  
> [!NOTE]
> Mobile device clients do not support multiple Secure Sockets Layer (SSL) certificates from different domains. Therefore, CNAME redirection to different domains is not supported over HTTPS. For example, a DNS CNAME record for lyncdiscover.contoso.com that redirects to an address of director.contoso.net is not supported over HTTPS. In such a topology, a mobile device client needs to use HTTP for the first request, so that the CNAME redirection is resolved over HTTP. Subsequent requests then use HTTPS. To support this scenario, you need to configure your reverse proxy with a web publishing rule for port 80 (HTTP). For details, see "To create a web publishing rule for port 80" in [Configuring the reverse proxy for mobility in Lync Server 2013](configuring-the-reverse-proxy-for-mobility.md). CNAME redirection to the same domain is supported over HTTPS. In this case, the destination domain's certificate covers the originating domain. 
  
## See also

#### 

[Configuring the reverse proxy for mobility in Lync Server 2013](configuring-the-reverse-proxy-for-mobility.md)
#### 

[Certificate summary - Autodiscover in Lync Server 2013](certificate-summaryautodiscover.md)

