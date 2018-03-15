---
title: "Certificate summary - DNS and HLB load balanced in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8318a1a4-b423-47b7-95e6-9541adfad391
description: "Certificate requirements for a Director with DNS load balancing and a hardware load balancer will use a default certificate that has a subject name and subject alternative names for services that the Director can receive. A certificate is requested for each Director in the pool. It is important to remember that the hardware load balancer is load balancing only the traffic from the reverse proxy. Additionally, there is an OAuth Token certificate for server to server authentication purposes that is installed on each server."
---

# Certificate summary - DNS and HLB load balanced in Lync Server 2013
[]
Certificate requirements for a Director with DNS load balancing and a hardware load balancer will use a default certificate that has a subject name and subject alternative names for services that the Director can receive. A certificate is requested for each Director in the pool. It is important to remember that the hardware load balancer is load balancing only the traffic from the reverse proxy. Additionally, there is an OAuth Token certificate for server to server authentication purposes that is installed on each server.
  
**Certificates for Director**

|**Component**|**Subject name (SN)**|**Subject alternative names (SAN)**|**Comments**|
|:-----|:-----|:-----|:-----|
|Default  <br/> |dirpool01.contoso.net  <br/> |dirpool01.contoso.net  <br/> dir01.contoso.net  <br/> dialin.contoso.com  <br/> meet.contoso.com  <br/> lyncdiscoverinternal.contoso.com  <br/> lyncdiscover.contoso.com  <br/> (Optionally) \*.contoso.com  <br/> |Director certificates can be requested from either an internally managed certification authority (CA) or from a public CA.  <br/> The Director responds to requests from the reverse proxy in the perimeter or from the Edge Server. Internal clients will not use the Director.  <br/> Or, a wildcard entry for the simple URLs  <br/> |
|OAuthTokenIssuer  <br/> |dir01.contoso.net  <br/> |No Entry  <br/> |
> [!IMPORTANT]
> Note that the minimum key length is 1024, but you may receive a warning that the minimum recommended key length is 2048 bits. 
  
The OAuthTokenIssuer certificate is a single-purpose certificate for the purpose of authenticating servers in a large-scale environment, and can be requested from an internal CA or from a public CA. The certificate is required.  <br/> |
   

