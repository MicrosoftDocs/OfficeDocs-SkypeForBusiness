---
title: "Load balancer partner qualification for Lync"
ms.author: jambirk
author: jambirk
manager: serdars
ms.reviewer: dougand
ms.topic: article
ms.tgt.pltfrm: lync
ms.service: skype-for-business-online
ms.collection: Lync
audience: Admin
appliesto:
- Lync
- Skype for Business 
localization_priority: Normal
f1keywords: None
ms.custom:
- Lync Certification
- dn788945
description: "Load balancer partner qualification requirements for Lync."
---

# Load balancer partner qualification requirements for Lync Server

## Hardware load balancers for Lync Server
Hardware load balancers listed in the table that follows have been tested by the vendor and reviewed by Microsoft to meet Lync Server requirements. We recommend that you visit the vendor's web site for the latest information regarding product specifications, capacity, country support and documentation including release notes and known issues. 

### Usage

For qualification, Lync Server requires integrating hardware load balancers in three deployment configurations. Hardware load balancers load balance traffic across several servers.

- ***Enterprise pool with multiple front-end servers***&nbsp;&nbsp; In this scenario, the hardware load balancer will be the connectivity point to multiple front-end servers in an Enterprise pool in consolidated and expanded configuration. In the expanded configuration, the hardware load balancer also load balances traffic to the Web Components servers of the Enterprise pool.
- ***Array of Directors***&nbsp;&nbsp; In this scenario, the hardware load balancer serves as the connectivity point to multiple Directors in an array.
- ***Array of Edge Servers***&nbsp;&nbsp; In this scenario, if the hardware load balancer supports multiple virtual IP addresses (VIP), it will serve as the connectivity point to both the internal and external NICs for multiple Edge Servers in an array. If the hardware load balancer only supports a single VIP, then two hardware load balancers are required to load balance Edge Servers, one for the internal NICs and one for the external NICs of the Edge Server.

***Hardware load balancers for Lync Server***

|Vendor|Qualified Product|Software Version Tested|Vendor's Lync Page|
|:--- |:--- |:--- |:--- |
|[A10Networks](http://www.a10networks.com/solutions/application_solutions_microsoft.php)| AX Series 1000, 2200, 3200 <br/><hr> 64-bit AX Series 2500, 2600, 3000, 5100, 5200| 2.4.3 |  [AX Series for Lync 2010 Overview and Deployment Guide](http://www.a10networks.com/solutions/application_solutions_microsoft.php)|
|[Array Networks](http://www.arraynetworks.com/) | APV Series | ArrayOS TM 8.x or later |[Deployment Guide for Array Networks APV Application Delivery Controllers and Microsoft Lync Server 2010](http://www.arraynetworks.com/libraries/DG-APV-Lync2010-Dec-2011-Rev-III.PDF) |
|AVANU |Webmux 481SD, 591SGQ, 690PG| V8.x and up|[WebMux and Microsoft Lync 2010](http://avanu.com/webmuxuc/)|
|[BarracudaNetworks](https://www.barracuda.com/products)|Barracuda Load Balancer ADC Model 340, 440 or 640|3.3.1.005, 3.5.0.008| [Barracuda Load Balancer Deployment Guide](https://techlib.barracuda.com/ADC/MSLyncDeployOverview)|
|Brocade |ServerIron XL,4G,GTC,GTE,350,450 &amp; 850<br/><hr> ServerIron ADX 1000, 4000, 10000|SI V10.0.0a<br/><hr>V12.1, V12.2|[Brocade Communications' Microsoft Unified Communications Solutions](http://www.brocade.com/partnerships/technology-alliance-partners/partner-details/microsoft/microsoft-office-communications-server/index.page)|
|[CitrixSystems](http://www.citrix.com/global-partners/microsoft/netscaler.html) |Netscaler|8.1, 9.x, 10.5|[Netscaler Developer Network](https://www.citrix.com/community.html)|
|[F5](http://www.f5.com/products/technology/microsoft/lync-server/) |BIG-IP Local Traffic Manager|11.x|[F5 Lync Server Solutions](https://f5.com/partners/product-technology-alliances/microsoft)|
|[Fortinet](http://www.fortinet.com/) |FortiADC-1500D|4.2.3|[Fortinet ADC Deployment Guide for Lync Server 2013](http://docs.fortinet.com/d/fortiadc-load-balancing-lync)|
|[HAProxy Technologies](http://www.haproxy.com/solutions/load-balancing-for-microsoft-products/) |ALOHA Load Balancer|5.5|[Aloha Deployment Guide for Lync 2010](http://www.haproxy.com/static/media/uploads/eng/resources/aloha_load_balancer_appnotes_0061_lync_2010_deployment_guide_en.pdf)|
|[jetNEXUS](http://www.jetnexus.com/support/applications/microsoft-lync/) |Accelerating Load Balancer (ALB)<br/><hr>Accelerating Load Balancer Extreme (ALB-X) |ALB 2.0 <br/><hr>3.42.1 (Build 1475) |[Advanced Load Balancing for Microsoft Lync 2010](http://www.jetnexus.com/support/applications/microsoft-lync/)|
|[KEMP Technologies](http://www.kemptechnologies.com/) |LoadMaster|7.1-18b|[LoadMaster Deployment Guide](http://kemptechnologies.com/microsoft-load-balancing/load-balancing-microsoft-lync/)|
|[Loadbalancer.org](http://loadbalancer.org/) |Enterprise, Enterprise MAX, Enterprise 10G|v6.18, v7.4.1|[Microsoft Lync 2010 Deployment Guide](http://pdfs.loadbalancer.org/Microsoft_Lync_2010_Deployment_Guide.pdf)|
|[Radware](http://www.radware.com/) |  AppDirector  <br/><hr>  Alteon   |v.2.14.03<br/><hr> v.28.1.0   |[Radware AppDirector optimizing the delivery of Microsoft Lync 2010](http://www.radware.com/Partners/TechnologyPartners/Microsoft/)<br/><hr> |
| |         |         ||

Note that these devices are backwards compatible with Office Communications Server 2007 R2. 

Please contact the vendor for more information on these products.

Load balancer vendors interested in qualification of their load balancer solutions with Office Communications Server should contact <a href="mailto:msucoip@microsoft.com">msucoip@microsoft.com</a>.

## Software load balancers for Lync Server

Software load balancers listed in the table that follows  have been tested by the vendor and reviewed by Microsoft to meet Lync Server requirements. We recommend that you visit the vendor's web site for the latest information regarding product specifications, capacity, country support and documentation including release notes and known issues. Please contact the vendor for more information on these products.

***Software load balancers for Lync Server***

|Vendor|Qualified Product |Software Version Tested|Vendor's Lync Page|
|:--- |:--- |:--- |:--- |
|[A10Networks](http://www.a10networks.com/solutions/application_solutions_microsoft.php) |64-bit AX Series: SoftAX|2.6|[AX Series for Lync 2010 Overview and Deployment Guide](http://www.a10networks.com/solutions/application_solutions_microsoft.php)|
|[Citrix Systems](https://www.citrix.com/)     |Netscaler VPX|9.1.102.8|[Netscaler Developer Network](https://www.citrix.com/community.html)|
|[F5](https://f5.com/) |BIG-IP Local Traffic Manager Virtual Edition|10.x, 11.x|[F5 Lync Server Solutions](https://f5.com/partners/product-technology-alliances/microsoft)|
|[HAProxy Technologies](http://www.haproxy.com/solutions/load-balancing-for-microsoft-products/)|ALOHA Load-Balancer Virtual Appliance|5.5|[Deployment guide](http://www.haproxy.com/static/media/uploads/eng/resources/aloha_load_balancer_appnotes_0061_lync_2010_deployment_guide_en.pdf)|
|[jetNEXUS](http://www.jetnexus.com/support/applications/microsoft-lync/) |  Accelerating Load Balancer (ALB)  <br/><hr>  Accelerating Load Balancer Extreme (ALB-X)    |  ALB 2.0   <br/><hr>3.42.1 (Build 1475)|[Advanced Load Balancing for Microsoft Lync 2010](http://www.jetnexus.com/support/applications/microsoft-lync/)|
|[KEMP](http://www.kemptechnologies.com/) |LoadMaster VLM-100, VLM-1000|V5.1|[LoadMaster Deployment Guide for Microsoft Lync 2010](http://kemptechnologies.com/files/downloads/documentation/Lync/KEMP_Lync_2010_Deployment_Guide.pdf)|
|[Loadbalancer.org](http://loadbalancer.org/)|Enterprise VA|v6.18, v7.4.1|[Microsoft Lync 2010 Deployment Guide](http://pdfs.loadbalancer.org/Microsoft_Lync_2010_Deployment_Guide.pdf)|
|[Riverbed Technology](http://www.riverbed.com/) |Stingray Traffic Manager|8.x and up|[Riverbed Stingray and Microsft Lync 2010: Deployment Guide](https://splash.riverbed.com/docs/DOC-1335)|
|     |         |         | |

Load balancer vendors interested in qualification of their load balancer solutions with Office Communications Server should contact <a href="mailto:msucoip@microsoft.com">msucoip@microsoft.com</a>.