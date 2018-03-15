---
title: "Scenarios for external user access in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 25697446-b045-4d12-9b1c-47f694b4f224
description: "Providing external user access for Lync Server 2013 requires that you deploy at least one Edge Server and one reverse proxy in your perimeter network. Optionally, you may deploy a Director or Director pool in your internal network."
---

# Scenarios for external user access in Lync Server 2013
[]
Providing external user access for Lync Server 2013 requires that you deploy at least one Edge Server and one reverse proxy in your perimeter network. Optionally, you may deploy a Director or Director pool in your internal network.
  
If you need greater capacity than a single Edge Server can provide, or if you need high availability for your Edge Server deployment, you can configure load balancing and deploy multiple Edge Servers in a load balanced pool. If your organization has multiple data centers, you can have Edge Server or Edge pool deployments at more than one location. However, only one of the Edge Server deployments can be designated as the federation route.
  
This section defines the scenarios for Edge Server deployments and maps the planning sections to the possible scenarios. For example, if your deployment requires high availability, federation with extensible messaging and presence (XMPP) contacts, and Lync mobility, you would select the matching entries in the following table that would satisfy these requirements and use the referenced planning sections to define your deployment, as illustrated in the following flowchart. 
  
**Edge Server deployment scenario selection process**

![Sample deployment flowchart](media/Lync_Planning_Choose_Edge_Scenarios.jpg)
  
By using this process, you can plan for and document the configuration of all potential features that you intend to deploy for your users. However, you can add federation and mobility services after you have deployed the Edge Server and have confirmed the correct operation before adding other features. The process of adding features to an existing Edge Server deployment is covered in the Deployment section. For details on deployment, see [Deploying external user access in Lync Server 2013](deploying-external-user-access.md) By including planning for these features during the initial planning process, you can prepare for the DNS, firewall, and certificate requirements for the added features, which enables you to acquire the certificates and configure DNS and port/protocol requirements in advance. 
  
> [!TIP]
> If you are planning to install the Edge Servers and reverse proxy and then add features later (for example, federation and mobility), determine what certificates you will require for all services after deployment. Planning for and acquiring the certificates for all features in advance, initially deployed or not, saves you from having to order new certificates to satisfy the requirements of federation (that is, on the Edge Servers) or the reverse proxy (that is, for mobility services). 
  
> [!NOTE]
> All edge services run on each Edge Server. Services cannot be split between two different Edge Servers. If you deploy an Edge pool for scalability, all edge services are deployed on each Edge Server in the pool. XMPP federation, Office Communications Server, and Lync Server federation, public IM connectivity and client mobility are additional services that can be deployed after you have deployed your first Edge Server or Edge pool. Mobility services is a feature that uses the reverse proxy. Installation of mobility services will not add features to your Edge Servers, but will require reconfiguration of your reverse proxy. The **Installation goal** column that lists these features provides planning guidance in the associated column under **Edge Server planning section or sections** for concurrently planning these features to be deployed when the Edge Servers are installed and configured. 
  
## Identifying and Mapping Your Deployment Goals

|**Installation goal**|**Edge Server planning documentation**|
|:-----|:-----|
|You have decided that a single server is sufficient for Edge services in your infrastructure. You also intend to use private IP addresses for the Edge server external interfaces with NAT to the Internet.  <br/> Use this planning section if you are deploying a single Edge Server in your perimeter. You will deploy an Edge Server with private IP addresses assigned to the Edge Server and will use NAT to provide the public IP addresses for the external users on the Internet.  <br/> |[Single consolidated edge with private IP addresses and NAT in Lync Server 2013](single-consolidated-edge-with-private-ip-addresses-and-nat.md) <br/> |
|You have decided that a single server is sufficient for Edge services in your infrastructure. You also intend to use public IP addresses for the Edge server external interfaces to the Internet.  <br/> Use this planning section if you are deploying a single Edge Server in your perimeter. You will deploy an Edge Server with public IP addresses assigned to the Edge Server. Instead of NAT, you will use routing in this scenario. The actual public IP address of the Edge Server are made available for external user connections.  <br/> |[Single consolidated edge with public IP addresses in Lync Server 2013](single-consolidated-edge-with-public-ip-addresses.md) <br/> |
|You have decided that high availability of the Edge services is important to your users and you will deploy two or more Edge Servers in this pool. You also intend to use private IP addresses for the Edge Server external interfaces with NAT to the Internet.  <br/> Use this planning section if you are deploying a pool of Edge Servers in your perimeter. You will deploy the Edge Servers with private IP addresses assigned to the Edge Server, using DNS load balancing to distribute communication across the pool. You will use NAT to provide the public IP addresses for the external users on the Internet.  <br/> |[Scaled consolidated edge, DNS load balancing with private IP addresses using NAT in Lync Server 2013](scaled-consolidated-edge-dns-load-balancing-with-private-ip-addresses-using-nat.md) <br/> |
|You have decided that high availability of the Edge services is important to your users and you will deploy two or more Edge Servers in this pool. You also intend to use public IP addresses for the Edge Server external interfaces to the Internet.  <br/> Use this planning section if you are deploying a pool of Edge Servers in your perimeter. You will deploy the Edge Servers with public IP addresses assigned to the Edge Server, using DNS load balancing to distribute communication across the pool. Instead of NAT, you will use routing to provide the public IP addresses for the external users on the Internet.  <br/> |[Scaled consolidated edge, DNS load balancing with public IP addresses in Lync Server 2013](scaled-consolidated-edge-dns-load-balancing-with-public-ip-addresses.md) <br/> |
|You have decided that high availability of the Edge services is important to your users and you will deploy two or more Edge Servers in this pool using a hardware load balancer.  <br/> Use this planning section if you are deploying a pool of Edge Servers in your perimeter. You will deploy the Edge Servers with public IP addresses assigned to the Edge Server, using hardware load balancers to distribute communication across the pool. Instead of NAT, you will use routing to provide the public IP addresses for the external users on the Internet.  <br/> |[Scaled consolidated edge with hardware load balancers in Lync Server 2013](scaled-consolidated-edge-with-hardware-load-balancers.md) <br/> |
| The federation scenarios allow you to plan for the feature that will extend the types of partners that your users can communicate with.  <br/>  Lync Server federation  <br/>  Office Communications Server federation  <br/>  Public IM connectivity  <br/>  XMPP federation  <br/> | Planning for Federation Scenarios  <br/> [Planning for Lync Server 2013 and Office Communications Server federation](planning-for-lync-server-and-office-communications-server-federation.md) <br/> [Planning for public instant messaging connectivity in Lync Server 2013](planning-for-public-instant-messaging-connectivity.md) <br/> [Planning for extensible messaging and presence protocol (XMPP) federation in Lync Server 2013](planning-for-extensible-messaging-and-presence-protocol-xmpp-federation.md) <br/> |
|Mobility services are offered through the reverse proxy. Services that enable mobility for external users are deployed on the Front End Server or Front End pool. You create or modify existing publishing rules on the reverse proxy to enable mobility services for your external users.  <br/> |[Planning for mobility in Lync Server 2013](planning-for-mobility.md) <br/> |
   
> [!TIP]
> In the following Scenarios sections are reference architectures, example DNS, port/protocol definitions, and certificate requirements. Also included are diagrams for your DNS, port/protocol definitions and certificate needs. The diagrams will provide a template for you to fill in and distribute to other teams (for example, your organization's Network Team, Public Key Infrastructure Team, and Server Deployment Team). The goal of the diagrams is to enhance communication and to ensure success when communicating the required Edge Server configuration elements to the people who will do the actual configuration work. We recommend that you use the diagrams and associated reference architectures to plan your deployment. 
  

