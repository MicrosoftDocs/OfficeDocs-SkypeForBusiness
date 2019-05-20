---
title: "Edge Machine Settings Expander for Lync Server 2010"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 11/17/2018
audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.EdgeMachineSettingsExpander2010
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: fb72a5b5-70f4-44af-8dfd-c5d32e563882
description: "To edit the properties for Edge Server computers as an single Edge Server or as member computers in an Edge pool, you configure Server name and IP address configuration settings:"
---

# Edge Machine Settings Expander for Lync Server 2010
 
To edit the properties for Edge Server computers as an single Edge Server or as member computers in an Edge pool, you configure **Server name and IP address configuration** settings:
  
- **Internal name or FQDN**: Type the name of the computer as it is referenced in the domain name system (DNS). 
    
- **Internal IPv4 address**: Type the IPv4 address of the internal network interface card (NIC) for this computer.
    
- You configure the **Access Edge service** **External IPv4 address** associated with this computer
    
    > [!IMPORTANT]
    > If you selected to use a single IP address for the Edge Server configuration, you will only be able to edit the external IPv4 address for the Access Edge service. The other Edge services will share the same IPv4 address as the Access Edge service. 
  
- If available to edit, you configure the **Web Conferencing service** **External IPv4 address** associated with this computer
    
- If available to edit, you configure the **A/V Edge service** **External IPv4 address** associated with this computer
    
- If available to edit, you configure the **NAT-enabled public IPv4 address** associated with this computer.
    
    > [!IMPORTANT]
    > The configuration property for **NAT-enabled public IPv4 address** will only be available to edit if you chose to provide network address translation (NAT) for the A/V Edge service
  
  **OK** Accepts and commits changes to the dialog.
  
  **Cancel** Discards changes and closes the dialog.
  
  **Help** Displays this help screen.
  

