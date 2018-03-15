---
title: "Configuring support for Autodiscover in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3a266456-69a0-4539-ba99-d388b83799a8
description: "The Lync Server web services Autodiscover service first appeared in the Lync Server 2010 Cumulative Update: November 2011. This update was accompanied by the initial release of Lync Mobile clients. The autodiscover service exposed the mobility services, known as the Mcx service."
---

# Configuring support for Autodiscover in Lync Server 2013
[]
The Lync Server web services **Autodiscover service** first appeared in the Lync Server 2010 Cumulative Update: November 2011. This update was accompanied by the initial release of Lync Mobile clients. The autodiscover service exposed the mobility services, known as the Mcx service. 
  
The autodiscover service acts as a single location for all clients to request information on what services and features are available, and how to contact the sevices - either by a fully qualified domain name or a web uniform resource locator reference. Autodiscover exposes a number of features, and each client will make requests based on the features that the client can use. For example, a desktop Lync 2013 client will use autodiscvoer to determine the external web services, but will not use the mobility (Mcx) services. To properly define and enable your clients to use the features available to them, the scenarios that allow a client to effectively find and use autodiscover entries should be defined. To use autodoscover, your deployment requires that a reverse proxy publishes the Lync Server web services, that DNS records are configured to resolve DNS queries for the Lync Server autodiscover service and Lync Server web services, and that certificate services are properly configured for your specific scenario. 
  
> [!TIP]
> For technical details on what the elements within the autodiscover request/response do, see [Understanding Autodiscover in Lync Server 2013](understanding-autodiscover.md). 
  
The following information and tables define, per scenario, what configurations (if any) you need to implement to provide the full and effective use of the autodiscover service. The information in the following topics is specific to Microsoft Lync Server 2013. If you are looking for guidance on how to plan Mobility for Lync Server 2010, see [https://go.microsoft.com/fwlink/?LinkId=275113](https://go.microsoft.com/fwlink/?LinkId=275113). To deploy Mobility for Lync Server 2010, see [https://go.microsoft.com/fwlink/?LinkId=275114](https://go.microsoft.com/fwlink/?LinkId=275114)
  
## In this section

- [Configuring DNS for Autodiscover in Lync Server 2013](configuring-dns-for-autodiscover.md)
    
- [Configuring certificates for Autodiscover in Lync Server 2013](configuring-certificates-for-autodiscover.md)
    
- [Configuring a reverse proxy for Autodiscover in Lync Server 2013](configuring-a-reverse-proxy-for-autodiscover.md)
    
- [Configuring Autodiscover in Lync Server 2013 for hybrid deployments](configuring-autodiscover-for-hybrid-deployments.md)
    

