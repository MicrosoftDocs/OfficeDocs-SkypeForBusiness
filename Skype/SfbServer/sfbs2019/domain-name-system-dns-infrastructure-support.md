---
title: "DNS infrastructure support in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 37777c16-94ce-436d-b517-bcf53a564513
description: "Lync Server 2013 requires Domain Name System (DNS) and uses it in the following ways:"
---

# DNS infrastructure support in Lync Server 2013
[]
Lync Server 2013 requires Domain Name System (DNS) and uses it in the following ways: 
  
- To discover internal servers or pools for server-to-server communications.
    
- To enable clients to discover the Front End pool or Standard Edition server used for various SIP transactions.
    
- To associate the simple URLs for conferences with the servers hosting those conferences.
    
- To enable external servers and clients to connect to Edge Servers or the HTTP reverse proxy for instant messaging (IM) or conferencing.
    
- To enable unified communications (UC) devices that are not logged in to discover the Front End pool or Standard Edition server running Device Update Web service, obtain updates, and send logs.
    
- To enable mobile clients to automatically discover Web Services resources without requiring users to manually enter URLs in device settings.
    
- For DNS load balancing.
    
> [!NOTE]
> Lync Server 2013 does not support internationalized domain names (IDNs). 
  
> [!IMPORTANT]
> The name you specify must be identical to the computer name configured on the server. By default, the computer name of a computer that is not joined to a domain is a short name, not a fully qualified domain name (FQDN). Topology Builder uses FQDNs, not short names. So, you must configure a DNS suffix on the name of the computer to be deployed as an Edge Server that is not joined to a domain. **Use only standard characters** (including A-Z, a-z, 0-9, and hyphens) when assigning FQDNs of your Lync Servers, Edge Servers, and pools. Do not use Unicode characters or underscores. Nonstandard characters in an FQDN are often not supported by external DNS and public CAs (that is, when the FQDN must be assigned to the SN in the certificate). 
  

