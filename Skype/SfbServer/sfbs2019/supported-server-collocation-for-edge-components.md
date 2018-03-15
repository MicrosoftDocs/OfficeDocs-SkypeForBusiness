---
title: "Supported server collocation for edge components in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 435c4dd8-36af-4b71-9b88-3ffcf0fc5c65
description: "The Access Edge service, Web Conferencing Edge service, A/V Edge service and XMPP Proxy service are collocated on the Edge Servers. The following servers provide functions needed for external user access and must be deployed as dedicated servers:"
---

# Supported server collocation for edge components in Lync Server 2013
[]
The Access Edge service, Web Conferencing Edge service, A/V Edge service and XMPP Proxy service are collocated on the Edge Servers. The following servers provide functions needed for external user access and must be deployed as dedicated servers:
  
- Edge Server
    
- Director (Optional)
    
- Reverse proxy
    
> [!IMPORTANT]
> The reverse proxy does not need to be dedicated to serving only Lync Server 2013. For example, you can provide services to publish the Lync Server Web services, and concurrently provide a published Web site for another Web site that has no bearing on Lync Server at all. If you already have a reverse proxy server in the perimeter network to support other services, you can use it for Lync Server 2013. 
  

