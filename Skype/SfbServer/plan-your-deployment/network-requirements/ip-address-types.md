---
title: "Configure IP address types in Skype for Business"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 7/22/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.custom: Strat_SB_Admin
ms.assetid: 17e756c0-6652-4cd5-b185-4b25929e3a42
description: "Summary: Review the IP Address type considerations below before implementing Skype for Business Server 2015."
---

# Configure IP address types in Skype for Business
 
**Summary:** Review the IP Address type considerations below before implementing Skype for Business Server 2015.
  
You deploy IP address types by using topology settings that you configure in Topology Builder. This section describes how to deploy IP address types on Front End Servers, Mediation Servers, and Edge Servers.
  
## Deploy IP address types on a Front End Server

Using Topology Builder, perform the steps in the following procedure to deploy IP address types on a Front End Server.
  
### To deploy IP address types on a Front End Server

1. Under **Enterprise Edition Front End pools**, right-click the server within a pool, and then select **Edit Properties**. (Alternatively, select the server, and then click **Edit Properties** from the **Action** menu.)
    
2. In the **Edit Properties** dialog box, select the IP address type that you want to configure. For a dual-stack configuration, select **Enable IPv4** and **Enable IPv6**, as shown in the following figure.
    
   **Edit Properties dialog box for the Front End Server pool**

  - **Use all configured IP addresses**. Select this option if you want to allow any IP address defined on the computer to be used. 
    
    > [!NOTE]
    > This is the recommended option for IP version 6 (IPv6) configurations. 
  
  - **Limit service usage to selected IP addresses**. Select this option to specify a specific address to use on the new server. If you select this option, you must enter a value for **Primary IP address**.
    
  - **Primary IP address**. Enter an IP address that the server will use for all communications except public switched telephone network (PSTN). The IP address entered must match the format of the select address type.
    
  - **PSTN IP address**. Define a PSTN IP address when a Mediation Server is collocated on the Front End Server. This address must match the format of the selected address type.
    
    > [!NOTE]
    > The installation of additional network interface cards (NICs) to support the PSTN IP address configuration on Front End Servers is not supported. For more information about supported NIC configurations for Skype for Business Server, see [Server hardware platforms for Lync Server 2013](http://technet.microsoft.com/library/c964c1c0-0153-472b-88ad-a38866e0df0c.aspx). 
  
## Deploy IP address types on a Mediation Server

Using Topology Builder, perform the steps in the following procedure to deploy IP address types on a Mediation Server.
  
### To deploy IP address types on a Mediation Server

- In Topology Builder, under **Mediation pools**, right-click the server within a pool, and then select **Edit Properties**. (Alternatively, select the server, and then click **Edit Properties** from the **Action** menu.)
    
- In the **Edit Properties** dialog box, select the IP address type that you want to configure. For a dual-stack configuration, select **Enable IPv4** and **Enable IPv6**, as shown in the following figure.
    
   **Edit Properties dialog box for the Mediation Server pool**

  - **Use all configured IP addresses**. Select this option if you want to allow any IP address defined on the computer to be used. 
    
    > [!NOTE]
    > This is the recommended option for IP version 6 (IPv6) configurations. 
  
  - **Limit service usage to selected IP addresses**. Select this option to specify a specific address to use on the new server. If you select this option, you must enter a value for Primary IP address.
    
  - **Primary IP address**. Enter an IP address that the server will use for all communications except public switched telephone network (PSTN). The IP address entered must match the format of the select address type.
    
  - **PSTN IP address**. Define a PSTN IP address when a Mediation Server is collocated on the Front End Server. This address must match the format of the selected address type.
    
    > [!NOTE]
    > The installation of additional NICs to support the PSTN IP address configuration on stand-alone Mediation Servers is not supported. For more information about supported NIC configurations for Skype for Business Server, see [Server hardware platforms for Lync Server 2013](http://technet.microsoft.com/library/c964c1c0-0153-472b-88ad-a38866e0df0c.aspx). 
  
## Deploy IP address types on a Edge Server

Using Topology Builder, perform the steps in the following procedure to deploy IP address types on an Edge Server.
  
### To deploy IP address types on an Edge Server

1. In Topology Builder, under **Edge pools**, right-click the server within a pool, and then select **Edit Properties**. (Alternatively, select the server, and then click **Edit Properties** from the **Action** menu.)
    
2. In the **Edit Properties** window, select the IP address configuration that you want to support. The following figures show a dual stack configuration for the internal interface and the external interface.
    
   **Dual stacked Edge Server internal interface**

   **Dual stacked Edge Server external interface**

3. For each address type that you select, you must supply appropriate internal and external addresses.
    

