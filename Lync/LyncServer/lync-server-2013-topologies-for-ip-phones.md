---
title: 'Lync Server 2013: Topologies for IP phones'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Topologies for IP phones
ms:assetid: 26ebffcf-43ff-4e70-847d-0fbc90e94e57
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425740(v=OCS.15)
ms:contentKeyID: 48183662
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Topologies for IP phones in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-21_

This section provides an overview of the connectivity process and explains the differences between how an IP phone connects in an internal and external network.

<div>


> [!NOTE]  
> Lync Server provides support for the following IP phones: the Aastra 6721ip common area phone, Aastra 6725ip desk phone, HP 4110 IP Phone (common area phone), HP 4120 IP Phone (desk phone), Polycom CX600 IP desk phone, Polycom CX700 IP desk phone, Polycom CX500 IP common area phone, and Polycom CX3000 IP conference phone. Of those phones, all but the Polycom CX700 can run Lync Phone Edition.



</div>

The following diagram describes all the components involved in device connectivity within the corporate environment.

**Internal Topology**

![3d88893e-df57-46e3-855a-a1d24589030a](images/Gg425740.3d88893e-df57-46e3-855a-a1d24589030a(OCS.15).jpg "3d88893e-df57-46e3-855a-a1d24589030a")

<div>


> [!NOTE]  
> The previous figure is a logical representation, not a physical overview. For example, Active Directory Domain Services (AD DS) is rarely located on the same machine as any Lync Server components. The user store can be located on the Back End Server or on the Archiving and Monitoring Servers. The Lync Server Management Shell, web server, and update services are all part of the Front End Server role.



</div>

The following diagram provides an overview of the components involved when the device is located outside the corporate network.

**External Topology**

![8ce6bb8e-b89c-4c4e-ac6d-41ac6c68f6f3](images/Gg425740.8ce6bb8e-b89c-4c4e-ac6d-41ac6c68f6f3(OCS.15).jpg "8ce6bb8e-b89c-4c4e-ac6d-41ac6c68f6f3")

<div>


> [!NOTE]  
> The Device Update Web service provides an external and internal website, but only the external one is shown here.<BR>The location of the Registrar and the URL of the Device Update Web service for the organization must be published in DNS if external access is to be enabled. Additionally, the Edge Server must be deployed and correctly configured to allow external communications from the device to the corporate environment and back. This is omitted from the previous diagram because Edge deployment is not specific to device connectivity.



</div>

</div>

<span> </span>

</div>

</div>

</div>

