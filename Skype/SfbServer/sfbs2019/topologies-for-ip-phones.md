---
title: "Topologies for IP phones in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 26ebffcf-43ff-4e70-847d-0fbc90e94e57
description: "This section provides an overview of the connectivity process and explains the differences between how an IP phone connects in an internal and external network."
---

# Topologies for IP phones in Lync Server 2013
[]
This section provides an overview of the connectivity process and explains the differences between how an IP phone connects in an internal and external network.
  
> [!NOTE]
> Lync Server provides support for the following IP phones: the Aastra 6721ip common area phone, Aastra 6725ip desk phone, HP 4110 IP Phone (common area phone), HP 4120 IP Phone (desk phone), Polycom CX600 IP desk phone, Polycom CX700 IP desk phone, Polycom CX500 IP common area phone, and Polycom CX3000 IP conference phone. Of those phones, all but the Polycom CX700 can run Lync Phone Edition. 
  
The following diagram describes all the components involved in device connectivity within the corporate environment. 
  
**Internal Topology**

![Devices Inside Network](media/Ops_LyncServer_Devices_ArchInsideNtwk.jpg)
  
> [!NOTE]
> The previous figure is a logical representation, not a physical overview. For example, Active Directory Domain Services (AD DS) is rarely located on the same machine as any Lync Server components. The user store can be located on the Back End Server or on the Archiving and Monitoring Servers. The Lync Server Management Shell, web server, and update services are all part of the Front End Server role. 
  
The following diagram provides an overview of the components involved when the device is located outside the corporate network.
  
**External Topology**

![Devices Outside Network](media/Ops_LyncServer_Devices_ArchOutsideNtwk.jpg)
  
> [!NOTE]
> The Device Update Web service provides an external and internal website, but only the external one is shown here. > The location of the Registrar and the URL of the Device Update Web service for the organization must be published in DNS if external access is to be enabled. Additionally, the Edge Server must be deployed and correctly configured to allow external communications from the device to the corporate environment and back. This is omitted from the previous diagram because Edge deployment is not specific to device connectivity. 
  

