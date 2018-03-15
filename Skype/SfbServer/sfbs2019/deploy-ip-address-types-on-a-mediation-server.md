---
title: "Deploy IP address types on a Mediation Server for Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 7/28/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 689ebed5-96ee-4cd4-b7ae-ee2a86a1d9b3
description: "Using Topology Builder, perform the steps in the following procedure to deploy IP address types on a Mediation Server."
---

# Deploy IP address types on a Mediation Server for Lync Server 2013
[]
Using Topology Builder, perform the steps in the following procedure to deploy IP address types on a Mediation Server.
  
### To deploy IP address types on a Mediation Server

- In Topology Builder, under **Mediation pools**, right-click the server within a pool, and then select **Edit Properties**. (Alternatively, select the server, and then click **Edit Properties** from the **Action** menu.) 
    
- In the **Edit Properties** dialog box, select the IP address type that you want to configure. For a dual-stack configuration, select **Enable IPv4** and **Enable IPv6**, as shown in the following figure.
    
   **Edit Properties dialog box for the Mediation Server pool**

     ![Lync Server general properties page with FQDN](media/Deploy_LyncServer_IPv6_Mediation_EditProperties.png)
  
  - **Use all configured IP addresses**. Select this option if you want to allow any IP address defined on the computer to be used. 
    
    > [!NOTE]
    > This is the recommended option for IP version 6 (IPv6) configurations. 
  
  - **Limit service usage to selected IP addresses**. Select this option to specify a specific address to use on the new server. If you select this option, you must enter a value for Primary IP address.
    
  - **Primary IP address**. Enter an IP address that the server will use for all communications except public switched telephone network (PSTN). The IP address entered must match the format of the select address type.
    
  - **PSTN IP address**. Define a PSTN IP address when a Mediation Server is standalone. This address must match the format of the selected address type.
    
    > [!NOTE]
    > The installation of additional network interface cards (NIC)s to support the PSTN IP address configuration for Lync Server 2013 is not supported on collocated Mediation Server roles. For more information about supported NIC configurations for Lync Server 2013, see [Server hardware platforms for Lync Server 2013](server-hardware-platforms.md). 
  

