---
title: "Create DNS records for reverse proxy servers in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b3513339-e49b-4665-80f1-b5a1c81a0e2e
description: "Create external DNS A records that point to the public external interface of your Microsoft Internet Security and Acceleration (ISA) Server 2006 SP1, Forefront Threat Management Gateway 2010 Server or Internet Information Server Application Request Routing, as described in Configure DNS for edge support in Lync Server 2013. You need DNS records for the external Web Service FQDNs for each pool, the Director (or Director pool), and each simple URL."
---

# Create DNS records for reverse proxy servers in Lync Server 2013
[]
Create external DNS A records that point to the public external interface of your Microsoft Internet Security and Acceleration (ISA) Server 2006 SP1, Forefront Threat Management Gateway 2010 Server or Internet Information Server Application Request Routing, as described in [Configure DNS for edge support in Lync Server 2013](configure-dns-for-edge-support.md). You need DNS records for the external Web Service FQDNs for each pool, the Director (or Director pool), and each simple URL. 
  
The minimum DNS records for client resolution to the reverse proxy, the following records must be created:
  
- Host (A) record(s) that define the published external web services for Directors and Director pools (for example, **webdirext.contoso.com** ) 
    
- Host (A) record(s) that define the published external web services for external web services hosted on the any Front End pools and Standard Edition server roles (for example, **webext.contoso.com** ) 
    
- Host (A) records for the Simple URLs (for example, **dialin.contoso.com** and **meet.contoso.com** ) 
    
- Host (A) record for the Lync Discover External record, and also provides pointer to AutoDiscover for all Web apps, including the Lync Web App, scheduler and Mobility (for example, **lyncdiscover.contoso.com** ) 
    
- Host (A) records for the Office Web Apps Server URL (for example **officewebapp01.contoso.com**)
    
For details, see [DNS summary - Reverse proxy in Lync Server 2013](dns-summaryreverse-proxy.md).
  

