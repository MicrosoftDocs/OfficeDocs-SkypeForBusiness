---
title: "Data collection in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e40b03e5-455d-4bbc-831a-c61b1380db53
description: "In Microsoft Lync Server 2013 communications software, you can run the Microsoft Lync Server 2013, Planning Tool without documenting your existing and proposed IP addresses and Edge Server fully qualified domain names (FQDNs), but it is significantly harder to do so without causing configuration errors. For example, if coexistence is required for a period of time, a common mistake is to reuse FQDNs from an existing Edge deployment for your Lync Server 2013 Edge deployment. By having the existing and proposed IP addresses and FQDNs written down in a spreadsheet, table, or other visual form, you help prevent setup problems during installation."
---

# Data collection in Lync Server 2013
[]
In Microsoft Lync Server 2013 communications software, you can run the Microsoft Lync Server 2013, Planning Tool without documenting your existing and proposed IP addresses and Edge Server fully qualified domain names (FQDNs), but it is significantly harder to do so without causing configuration errors. For example, if coexistence is required for a period of time, a common mistake is to reuse FQDNs from an existing Edge deployment for your Lync Server 2013 Edge deployment. By having the existing and proposed IP addresses and FQDNs written down in a spreadsheet, table, or other visual form, you help prevent setup problems during installation.
  
> [!CAUTION]
> If you have used previous versions of the Planning Tool, you may have used the tool to create your topology and the exported the topology document for use in Topology Builder to publish your topology. The ability to export the topology was removed from Planning Tool. Using a previous version of the Planning Tool to create a topology document for Lync Server 2013 is strongly discouraged, and will produce unexpected results. 
  
Therefore, the recommended approach is to use the following data collection template, which corresponds to your Edge topology, to gather the various FQDN and IP addresses that you will need to enter into the Planning Tool. By documenting the current and proposed configuration, you can put the values in the proper context for your production environment. And, you are forced to think about how you will configure coexistence and features such as simple URLs, file shares, and load balancing.
  
To successfully deploy Microsoft Lync Server 2013, you need to understand the interaction of and reliance on the individual components. By collecting data from your existing network and server infrastructure, and applying the planning guidance in these sections, you can integrate Lync Server 2013 Edge Server components into your infrastructure.
  
Introduced in [Choosing a topology in Lync Server 2013](choosing-a-topology.md), there are three main architectures with two variations, for a total of five possible deployment scenarios. One of these scenarios will be the starting point for your data collection. The IP addresses, server names, and domain names are examples that coincide with the matching certificate, firewall, and DNS diagrams that detail the information required for a complete planning solution. The diagrams and filling in your required certificate, DNS and firewall values is especially important in cross-team communications where the management of the certification authority, firewall configuration and DNS is managed by teams other than the team that plans the deployment. The diagrams provide information on required components that can be used to communicate these requirements for cross-team collaboration.
  
The provided diagrams are intentionally generic, but allow for the collection of all pertinent data that would be necessary for communication of requirements in a cross team scenario where networking, firewall, certificate creation and management, server deployment, and server management are handled by different groups. Having the required details for configuration of networking, firewalls, ports and protocols, certificates, and servers is invaluable when the deployment of Lync Server is underway.
  
 **Edge Server and Edge pool**
  
![Edge Server and Edge Pool](media/Plan_DataCollection_Edge_Server_and_Edge_pool.jpg)
  
 **Reverse Proxy**
  
![Reverse Proxy](media/Plan_DataCollection_Reverse_Proxy.jpg)
  
 **Director or Director pool**
  
![Director and Director Pool](media/Plan_DataCollection_Director_and_Director_pool.jpg)
  

