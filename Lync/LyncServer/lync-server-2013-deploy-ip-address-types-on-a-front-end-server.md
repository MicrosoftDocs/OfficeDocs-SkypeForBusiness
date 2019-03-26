---
title: 'Lync Server 2013: Deploy IP address types on a Front End Server'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Deploy IP address types on a Front End Server
ms:assetid: b6c8e0f9-ec8e-4a4e-a525-756f9cd6b9d0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205191(v=OCS.15)
ms:contentKeyID: 48185193
ms.date: 07/28/2016
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deploy IP address types on a Front End Server for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-07-28_

Using Topology Builder, perform the steps in the following procedure to deploy IP address types on a Front End Server.

<div>

## To deploy IP address types on a Front End Server

1.  Under **Enterprise Edition Front End pools**, right-click the server within a pool, and then select **Edit Properties**. (Alternatively, select the server, and then click **Edit Properties** from the **Action** menu.)

2.  In the **Edit Properties** dialog box, select the IP address type that you want to configure. For a dual-stack configuration, select **Enable IPv4** and **Enable IPv6**, as shown in the following figure.
    
    **Edit Properties dialog box for the Front End Server pool**
    
    ![Front End Server Edit Properties dialog box](images/JJ205191.737a9d71-c0bc-4a54-9608-9e028dacc814(OCS.15).png "Front End Server Edit Properties dialog box")
    
      - **Use all configured IP addresses**. Select this option if you want to allow any IP address defined on the computer to be used.
        
        <div>
        

        > [!NOTE]  
        > This is the recommended option for IP version 6 (IPv6) configurations.

        
        </div>
    
      - **Limit service usage to selected IP addresses**. Select this option to specify a specific address to use on the new server. If you select this option, you must enter a value for **Primary IP address**.
    
      - **Primary IP address**. Enter an IP address that the server will use for all communications except public switched telephone network (PSTN). The IP address entered must match the format of the select address type.
    
      - **PSTN IP address**. The installation of additional network interface cards (NIC)s to support the PSTN IP address configuration for Lync Server 2013 is not supported on collocated Mediation Server roles. For more information about supported NIC configurations for Lync Server 2013, see [Server hardware platforms for Lync Server 2013](lync-server-2013-server-hardware-platforms.md).

</div>

</div>

<span> </span>

</div>

</div>

</div>

