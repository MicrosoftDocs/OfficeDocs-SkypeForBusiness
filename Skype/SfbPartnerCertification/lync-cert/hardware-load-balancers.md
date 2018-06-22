---
title: "Load balancer partner qualification for Lync"
ms.author: jambirk
author: jambirk
manager: serdars
ms.reviewer: v-thehay
ms.topic: article
ms.tgt.pltfrm: lync
ms.service: skype-for-business
ms.collection: Lync
ms.audience: Admin
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
Hhardware load balancers listed in the table that follows have been tested by the vendor and reviewed by Microsoft to meet Lync Server requirements. We recommend that you visit the vendor's web site for the latest information regarding product specifications, capacity, country support and documentation including release notes and known issues. 

### Usage

For qualification, Lync Server requires integrating hardware load balancers in three deployment configurations. Hardware load balancers load balance traffic across several servers.

- ***Enterprise pool with multiple front-end servers***&nbsp;&nbsp; In this scenario, the hardware load balancer will be the connectivity point to multiple front-end servers in an Enterprise pool in consolidated and expanded configuration. In the expanded configuration, the hardware load balancer also load balances traffic to the Web Components servers of the Enterprise pool.
- ***Array of Directors***&nbsp;&nbsp; In this scenario, the hardware load balancer serves as the connectivity point to multiple Directors in an array.
- ***Array of Edge Servers***&nbsp;&nbsp; In this scenario, if the hardware load balancer supports multiple virtual IP addresses (VIP), it will serve as the connectivity point to both the internal and external NICs for multiple Edge Servers in an array. If the hardware load balancer only supports a single VIP, then two hardware load balancers are required to load balance Edge Servers, one for the internal NICs and one for the external NICs of the Edge Server.

***Hardware load balancers for Lync Server***

<table border="1" cellpadding="5" cellspacing="" class="grid" style="border-collapse:collapse;background-color:white;" width="100%" xmlns="http://www.w3.org/1999/xhtml">
	<tr bgcolor="#DEDEDE">
		<td width="13%"><strong>Vendor</strong></td>
		<td width="28%"><strong>Qualified Product</strong></td>
		<td width="16%"><strong>Software Version Tested</strong></td>
		<td width="43%"><strong>Vendor's Lync Page</strong></td>
	</tr>
	<tr align="left" valign="top">
		<td rowspan="2"><a href="http://www.a10networks.com/solutions/application_solutions_microsoft.php">A10Networks</a></td>
		<td>AX Series 1000, 2200, 3200</td>
		<td rowspan="2">2.4.3</td>
		<td rowspan="2"><a href="http://www.a10networks.com/solutions/application_solutions_microsoft.php">AX Series for Lync 2010 Overview and Deployment Guide</a></td>
	</tr>
	<tr>
		<td>64-bit AX Series 2500, 2600, 3000, 5100, 5200</td>
	</tr>
	<tr align="left" bgcolor="#F8F8F8" valign="top">
		<td><a href="http://www.arraynetworks.com/">Array Networks</a></td>
		<td>APV Series</td>
		<td>ArrayOS TM 8.x or later</td>
		<td><a href="http://www.arraynetworks.com/libraries/DG-APV-Lync2010-Dec-2011-Rev-III.PDF">Deployment Guide for Array Networks APV Application Delivery Controllers and Microsoft Lync Server 2010</a></td>
	</tr>
	<tr align="left" valign="top">
		<td>AVANU</td>
		<td>Webmux 481SD, 591SGQ, 690PG</td>
		<td>V8.x and up</td>
		<td><a href="http://avanu.com/webmuxuc/">WebMux and Microsoft Lync 2010</a></td>
	</tr>
	<tr align="left" bgcolor="#F8F8F8" valign="top">
		<td><a href="https://www.barracuda.com/products">BarracudaNetworks</a></td>
		<td>Barracuda Load Balancer ADC Model 340, 440 or 640</td>
		<td>3.3.1.005, 3.5.0.008</td>
		<td><a href="https://techlib.barracuda.com/ADC/MSLyncDeployOverview">Barracuda Load Balancer Deployment Guide</a></td>
	</tr>
	<tr align="left" valign="top">
		<td rowspan="2">Brocade</td>
		<td>ServerIron XL,4G,GTC,GTE,350,450 &amp; 850</td>
		<td>SI V10.0.0a </td>
		<td rowspan="2"><a href="http://www.brocade.com/partnerships/technology-alliance-partners/partner-details/microsoft/microsoft-office-communications-server/index.page">Brocade Communications' Microsoft Unified Communications Solutions</a></td>
	</tr>
	<tr align="left" valign="top">
		<td>ServerIron ADX 1000, 4000, 10000</td>
		<td>V12.1, V12.2</td>
	</tr>
	<tr align="left" bgcolor="#F8F8F8" valign="top">
		<td><a href="http://www.citrix.com/global-partners/microsoft/netscaler.html">CitrixSystems</a></td>
		<td>Netscaler</td>
		<td>8.1, 9.x, 10.5</td>
		<td><a href="https://www.citrix.com/community.html">Netscaler Developer Network</a></td>
	</tr>
	<tr align="left"valign="top">
		<td><a href="http://www.f5.com/products/technology/microsoft/lync-server/">F5</a></td>
		<td>BIG-IP Local Traffic Manager</td>
		<td>11.x</td>
		<td><a href="https://f5.com/partners/product-technology-alliances/microsoft">F5 Lync Server Solutions</a></td>
	</tr>
	<tr align="left"  bgcolor="#F8F8F8" valign="top">
		<td><a href="http://www.fortinet.com/">Fortinet</a></td>
		<td>FortiADC-1500D</td>
		<td>4.2.3</td>
		<td><a href="http://docs.fortinet.com/d/fortiadc-load-balancing-lync">Fortinet ADC Deployment Guide for Lync Server 2013</a></td>
	</tr>
	<tr align="left" valign="top">
		<td><a href="http://www.haproxy.com/solutions/load-balancing-for-microsoft-products/">HAProxy Technologies</a></td>
		<td>ALOHA Load Balancer</td>
		<td>5.5</td>
		<td><a href="http://www.haproxy.com/static/media/uploads/eng/resources/aloha_load_balancer_appnotes_0061_lync_2010_deployment_guide_en.pdf">Aloha Deployment Guide for Lync 2010</a></td>
	</tr>
	<tr align="left"  bgcolor="#F8F8F8" valign="top">
		<td rowspan="2"><a href="http://www.jetnexus.com/support/applications/microsoft-lync/">jetNEXUS</a></td>
		<td>Accelerating Load Balancer (ALB)</td>
		<td>ALB 2.0</td>
		<td rowspan="2"><a href="http://www.jetnexus.com/support/applications/microsoft-lync/">Advanced Load Balancing for Microsoft Lync 2010</a></td>
	</tr>
	<tr>
		<td>Accelerating Load Balancer Extreme (ALB-X)</td>
		<td>3.42.1 (Build 1475)</td>
	</tr>
	<tr align="left" valign="top">
		<td><a href="http://www.kemptechnologies.com/">KEMP Technologies</a></td>
		<td>LoadMaster</td>
		<td>7.1-18b</td>
		<td><a href="http://kemptechnologies.com/microsoft-load-balancing/load-balancing-microsoft-lync/">LoadMaster Deployment Guide</a></td>
	</tr>
	<tr align="left" bgcolor="#F8F8F8" valign="top">
		<td><a href="http://loadbalancer.org/">Loadbalancer.org</a></td>
		<td>Enterprise, Enterprise MAX, Enterprise 10G</td>
		<td>v6.18, v7.4.1</td>
		<td><a href="http://pdfs.loadbalancer.org/Microsoft_Lync_2010_Deployment_Guide.pdf">Microsoft Lync 2010 Deployment Guide</a></td>
	</tr>
	<tr align="left" valign="top">
		<td rowspan="2"><a href="http://www.radware.com/">Radware</a></td>
		<td>AppDirector</td>
		<td>v.2.14.03</td>
		<td><a href="http://www.radware.com/Partners/TechnologyPartners/Microsoft/">Radware AppDirector optimizing the delivery of Microsoft Lync 2010</a></td>
	</tr>
	<tr bgcolor="#F8F8F8">
		<td>Alteon</td>
		<td>v.28.1.0</td>
		<td><a href="http://www.radware.com/Partners/TechnologyPartners/Microsoft/">Alteon Application Switch (AAS) optimizing the delivery of Microsoft Lync 2010</a></td>
	</tr>
</table>

Note that these devices are backwards compatible with Office Communications Server 2007 R2. 

Please contact the vendor for more information on these products.

Load balancer vendors interested in qualification of their load balancer solutions with Office Communications Server should contact <a href="mailto:msucoip@microsoft.com">msucoip@microsoft.com</a>.

## Software load balancers for Lync Server

Software load balancers listed in the table that follows  have been tested by the vendor and reviewed by Microsoft to meet Lync Server requirements. We recommend that you visit the vendor's web site for the latest information regarding product specifications, capacity, country support and documentation including release notes and known issues. Please contact the vendor for more information on these products.

***Software load balancers for Lync Server***

<table border="1" cellpadding="5" cellspacing="" class="grid" style="border-collapse:collapse;background-color:white;" width="100%" xmlns="http://www.w3.org/1999/xhtml">
	<tr bgcolor="#DEDEDE">
		<td width="13%"><strong>Vendor</strong></td>
		<td width="28%"><strong>Qualified Product</strong></td>
		<td width="16%"><strong>Software Version Tested</strong></td>
		<td width="43%"><strong>Vendor's Lync Page</strong></td>
	</tr>
	<tr align="left" valign="top">
		<td><a href="http://www.a10networks.com/solutions/application_solutions_microsoft.php">A10Networks</a></td>
		<td>64-bit AX Series: SoftAX</td>
		<td>2.6</td>
		<td><a href="http://www.a10networks.com/solutions/application_solutions_microsoft.php">AX Series for Lync 2010 Overview and Deployment Guide</a></td>
	</tr>
	<tr align="left" bgcolor="#F8F8F8" valign="top">
		<td><a href="https://www.citrix.com/community.html">Citrix Systems</a></td>
		<td>Netscaler VPX</td>
		<td>9.1.102.8</td>
		<td><a href="https://www.citrix.com/community.html">Netscaler Developer Network</a></td>
	</tr>
	<tr align="left" valign="top">
		<td><a href="https://f5.com/">F5</a></td>
		<td>BIG-IP Local Traffic Manager Virtual Edition</td>
		<td>10.x, 11.x</td>
		<td><a href="https://f5.com/partners/product-technology-alliances/microsoft">F5 Lync Server Solutions</a></td>
	</tr>
	<tr align="left" bgcolor="#F8F8F8" valign="top">
		<td><a href="http://www.haproxy.com/solutions/load-balancing-for-microsoft-products/">HAProxy Technologies</a></td>
		<td>ALOHA Load-Balancer Virtual Appliance</td>
		<td>5.5</td>
		<td><a href="http://www.haproxy.com/static/media/uploads/eng/resources/aloha_load_balancer_appnotes_0061_lync_2010_deployment_guide_en.pdf">Deployment guide</a></td>
	</tr>
	<tr align="left" valign="top">
		<td rowspan="2"><a href="http://www.jetnexus.com/support/applications/microsoft-lync/">jetNEXUS</a></td>
		<td>Accelerating Load Balancer (ALB)</td>
		<td>ALB 2.0</td>
		<td rowspan="2"><a href="http://www.jetnexus.com/support/applications/microsoft-lync/">Advanced Load Balancing for Microsoft Lync 2010</a></td>
	</tr>
	<tr>
		<td>Accelerating Load Balancer Extreme (ALB-X)</td>
		<td>3.42.1 (Build 1475)</td>
	</tr>
	<tr align="left" bgcolor="#F8F8F8" valign="top">
		<td><a href="http://www.kemptechnologies.com/">KEMP</a></td>
		<td>LoadMaster VLM-100, VLM-1000</td>
		<td>V5.1</td>
		<td><a href="http://kemptechnologies.com/files/downloads/documentation/Lync/KEMP_Lync_2010_Deployment_Guide.pdf">LoadMaster Deployment Guide for Microsoft Lync 2010</a></td>
	</tr>
	<tr align="left" valign="top">
		<td><a href="http://loadbalancer.org/">Loadbalancer.org</a></td>
		<td>Enterprise VA</td>
		<td>v6.18, v7.4.1</td>
		<td><a href="http://pdfs.loadbalancer.org/Microsoft_Lync_2010_Deployment_Guide.pdf">Microsoft Lync 2010 Deployment Guide</a></td>
	</tr>
	<tr align="left" bgcolor="#F8F8F8" valign="top">
		<td><a href="http://www.riverbed.com/">Riverbed Technology</a></td>
		<td>Stingray Traffic Manager</td>
		<td>8.x and up</td>
		<td><a href="https://splash.riverbed.com/docs/DOC-1335">Riverbed Stingray and Microsft Lync 2010: Deployment Guide</a></td>
	</tr>
</table>

Load balancer vendors interested in qualification of their load balancer solutions with Office Communications Server should contact <a href="mailto:msucoip@microsoft.com">msucoip@microsoft.com</a>.