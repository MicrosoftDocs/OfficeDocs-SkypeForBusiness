---
title: "Server Settings Expander for Lync Server 2010"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 11/17/2018
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.MachineSettingsExpander2010
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e2309ade-f9c7-4cd1-b135-45bf73b0441f
description: "To edit the properties for this computer, you do the following:"
---

# Server Settings Expander for Lync Server 2010
 
To edit the properties for this computer, you do the following:
  
- Edit the **Fully qualified domain name (FQDN)** for this computer. This entry must match the computer name as it is defined in the domain name system (DNS), and in subject alternative names (SAN) or subject name (SN) of the certificate associated with this computer.
    
- You select one of the following:
    
    **Use all configured IP addresses**: Select this to use all configured IP addresses on the computer.
    
    > [!IMPORTANT]
    > If the computer has multiple IP addresses, you must be aware that the services associated with this computer will use all IP addresses for all services. If a listening server or service is expecting communication of a specific IP address and port, the service may not make the best selection of which IP address to listen on. 
  
    **Limit service usage to selected IP addresses**: Select this option if you want to define specific IP addresses for the **Primary IP address** that this computer will listen on for communication from other computers and pools in the deployment. Define **PSTN IP address** for the specific IP address that the computer and service will listen for communications and send communications to the defined PSTN gateway or IP-PBX.
    

