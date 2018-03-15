---
title: "Port summary - Scaled Director pool, hardware load balancer in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6ae2f4ac-5b64-4e45-8253-133308f5812d
description: "Firewall port requirements for a Director pool consist of the ports that are used to establish communication with the Director from the internal interface of the Edge Server or internal-facing interface of the reverse proxy. Microsoft Lync Server 2013 by default expects ports HTTP/TCP 8080 and HTTPS/TCP 4443 to be open from the reverse proxy to the Director, as well as the Front End pool and Front End Server. Additionally, there must be session initiation protocol (SIP) communication from the Edge Server internal interface to the Director and to the Front End pool and Front End Server. The SIP protocol uses SIP/MTLS/TCP 5061 from the Edge Server to the Front End pool and Front End Server. A rule that allows SIP/MTLS/TCP 5061 communication from the Director, Front End pool and Front End Server to the Edge Server internal interface must be created as well."
---

# Port summary - Scaled Director pool, hardware load balancer in Lync Server 2013
[]
Firewall port requirements for a Director pool consist of the ports that are used to establish communication with the Director from the internal interface of the Edge Server or internal-facing interface of the reverse proxy. Microsoft Lync Server 2013 by default expects ports HTTP/TCP 8080 and HTTPS/TCP 4443 to be open from the reverse proxy to the Director, as well as the Front End pool and Front End Server. Additionally, there must be session initiation protocol (SIP) communication from the Edge Server internal interface to the Director and to the Front End pool and Front End Server. The SIP protocol uses SIP/MTLS/TCP 5061 from the Edge Server to the Front End pool and Front End Server. A rule that allows SIP/MTLS/TCP 5061 communication from the Director, Front End pool and Front End Server to the Edge Server internal interface must be created as well.
  
**Director Ports and Protocols for Firewall Definitions**

|**Role/Protocol/TCP or UDP/Port**|**Source IP address**|**Destination IP address**|**Notes**|
|:-----|:-----|:-----|:-----|
|HTTP/TCP 8080  <br/> |Reverse proxy internal interface  <br/> |Director Hardware Load Balancer VIP  <br/> |Initially received by the external side of the reverse proxy, the communication is sent on to the Director HLB VIP and Front End Servers web services  <br/> |
|HTTPS/TCP 4443  <br/> |Reverse proxy internal interface  <br/> |Director Hardware Load Balancer VIP  <br/> |Initially received by the external side of the reverse proxy, the communication is sent on to the Director HLB VIP and Front End Servers web services  <br/> |
|HTTPS/TCP 444  <br/> |Director  <br/> |Front End Server or Front End pool  <br/> |Inter-server communication between the Director HLB VIP and the Front End Servers  <br/> |
|HTTP/TCP 80  <br/> |Internal Clients  <br/> |Director Hardware Load Balancer VIP  <br/> |The Director provides web services to internal as well as external clients.  <br/> |
|HTTPS/TCP 443  <br/> |Internal Clients  <br/> |Director Hardware Load Balancer VIP  <br/> |The Director provides web services to internal as well as external clients.  <br/> |
|SIP/MTLS/TCP 5061  <br/> |Edge Server internal interface  <br/> |Director Hardware Load Balancer VIP  <br/> |SIP communication from the Edge Server to the Director, and Front End Servers.  <br/> |
|MTLS/TCP/50001  <br/> |Any  <br/> |Director  <br/> |Centralized Logging Service controller (ClsController.exe) or agent (ClsAgent.exe)commands and log collection  <br/> |
|MTLS/TCP/50002  <br/> |Any  <br/> |Director  <br/> |Centralized Logging Service controller (ClsController.exe) or agent (ClsAgent.exe)commands and log collection  <br/> |
|MTLS/TCP/50003  <br/> |Any  <br/> |Director  <br/> |Centralized Logging Service controller (ClsController.exe) or agent (ClsAgent.exe)commands and log collection  <br/> |
   

