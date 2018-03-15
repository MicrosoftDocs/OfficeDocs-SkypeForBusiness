---
title: "Editing the design in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 08f639ba-0e5f-4ae7-9191-c3d96c25b169
description: "After completing the initial interview questions, you can edit the fully qualified domain name (FQDN) and IP addresses for the site. To do this, on the Global Topology page, double-click the site that you want to edit."
---

# Editing the design in Lync Server 2013
[]
After completing the initial interview questions, you can edit the fully qualified domain name (FQDN) and IP addresses for the site. To do this, on the **Global Topology** page, double-click the site that you want to edit. 
  
The Planning Tool displays the site topology for the selected site. At the bottom of the site page are four tabs:
  
![Planning Tool Site Topology](media/Planning_Tool_Site_Topology.jpg)
  
- Site Topology - The currently displayed page with a visual overview of the topology as recommended.
    
- Edge Network Diagram - The Edge Network Diagram page is where the designer does most of the work in the Planning Tool. The diagram displays the network configuration for a recommended Lync Server 2013 topology, with editable entries for IP addresses and FQDNs for servers, pool, and both hardware and Domain Name System (DNS) load balancers.
    
- Edge Admin Report - The Edge Admin Report contains a total of four reports:
    
     ![Edge Admin Report page](media/Planning_Tool_Summary_Report.jpg)
  
  - Summary Report - A general report of settings for the Edge network configuration. If you edit the values on the **Edge Network Diagram** page to the topology TCP/IP and FQDN values of that will be used in the actual deployment, those addresses and names will be represented here. Otherwise, the default text will appear. 
    
  - Certificate Report - The certificate report will list the subject name and subject alternative names for the certificates that are required for the topology.
    
  - Firewall Report - The firewall report lists information necessary to configure perimeter firewalls in the infrastructure. This includes the IP addresses (either the default or edited values), server role, source IP and port, destination IP and port, transport protocol, application protocol, and relevant notes.
    
  - DNS Report - The DNS Report lists relevant information for the DNS entries that you must create. The record type, FQDN, IP address, and comments necessary for the proper operation are included.
    
- Site Summary - The site summary presents an overview of the selections that you made by either answering the initial interview questions or filling in the values in **Design Sites**. Capacity information is also presented. 
    
    > [!NOTE]
    > The information on the Site Summary page is customized for each design and may not contain all sections or information detailed here. 
  
## See also

#### 

[Editing the network configuration diagram in Lync Server 2013](editing-the-network-configuration-diagram.md)

