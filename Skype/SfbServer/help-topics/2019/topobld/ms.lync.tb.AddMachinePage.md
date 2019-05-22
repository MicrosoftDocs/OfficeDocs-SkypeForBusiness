---
title: "Add Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.AddMachinePage
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 61647eac-9062-4381-9c80-3cbf70b7db33
ROBOTS: NOINDEX, NOFOLLOW
description: "To add a new server to an existing pool of servers, where the pool is one of the following:"
---

# Add Server
 
To add a new server to an existing pool of servers, where the pool is one of the following:
  
- Enterprise Edition Front End Server
    
- Director server
    
- Mediation Server
    
- Audio/Video Conferencing Server
    
- Trusted Application server
    
Each of the new pool servers has different requirements. In the following sections, locate the type of server that you are adding to the existing pool, and supply the information requested as it is defined for each server type. You provide the requested information to define the new pool server.
  
 **Enterprise Edition Front End Server**
  
- Fully qualified domain name (FQDN) of the new server as it is defined in Domain Name System (DNS).
    
- Select **Use all configured IP addresses**, which means that any IP address defined on the computer can be used. Alternatively, you can select **Limit service usage to selected IP addresses** and enter a specific address on the new server. The IP address entered is the only IP address which will respond for the hosted services.
    
- Define a **PSTN IP address** when a Mediation Server is collocated on the Front End Server.
    
- Select **Enable IPv6** to enable IPv6 for this server.
    
  **Director server**
  
- The FQDN of the new server as it is defined in DNS.
    
- Select **Use all configured IP addresses**, which means that any IP address defined on the computer will be used. Alternatively, you select **Limit service usage to selected IP addresses** and enter a specific IP address on the new server. The IP address entered is the only IP address which will respond for the hosted services.
    
  **Mediation Server**
  
- The FQDN of the new server as it is defined in DNS.
    
- Select **Use all configured IP addresses**, which means that any IP address defined on the computer can be used. Alternatively, you select **Limit service usage to selected IP addresses** and enter a specific IP address on the new server as the Primary IP address, and an enter an IP address for the public switched telephone network (PSTN) IP address. The IP addresses entered are the only IP address which will respond for the designated services.
    
    > [!NOTE]
    > For the Mediation Server, the IP address entered for the Primary IP address and the PSTN IP address is the same by default. The IP addresses can be defined separately if you are using dedicated network interfaces or separate IP addresses on the same network interface. If you have two network interfaces, one for the local network connection and one for the PSTN connection, you must assign different IP addresses. 
  
  **Audio/Video Conferencing Server**
  
- The FQDN of the new server as it is defined in DNS.
    
- Select **Use all configured IP addresses**, which means that any IP address defined on the computer can be used. Alternatively, you can select **Limit service usage to selected IP addresses** and enter a specific address on the new server. The IP address entered is the only IP address which will respond for the hosted services.
    
  **Trusted Application server**
  
- The FQDN of the new server as it is defined in DNS.
    

