---
title: "Device hardware support in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: End User
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ba07ca91-32b4-49cf-801c-47a2d1d96e18
description: "Specific hardware configurations must be in place before you deploy IP phones and analog devices."
---

# Device hardware support in Lync Server 2013
[]
Specific hardware configurations must be in place before you deploy IP phones and analog devices.
  
IP phones running Lync Phone Edition support Link Layer Discovery Protocol-Media Endpoint Discovery (LLDP-MED) and Power over Ethernet (PoE). To take advantage of LLDP-MED, the switch must support IEEE802.1AB and ANSI/TIA-1057. To take advantage of PoE, the switch must support PoE802.3AF or 802.3at. 
  
To enable LLDP-MED, the administrator must enable LLDP by using the switch console window and set the LLDP-MED network policy with the correct voice VLAN ID.
  
In addition, if your deployment includes analog devices, you must configure the analog gateway to use Lync Server, and the gateway must be one of the following:
  
- An analog telephone adapter (ATA)
    
- A PSTN analog gateway
    
- A Survivable Branch Appliance that includes a PSTN analog gateway
    
- A Survivable Branch Appliance that includes a PSTN gateway that communicates with an ATA
    
To learn how to configure an analog gateway, see "Planning to Deploy Analog Devices" at [https://go.microsoft.com/fwlink/p/?LinkId=268537](https://go.microsoft.com/fwlink/p/?LinkId=268537) in the Lync Server 2010 TechNet Library. (Analog devices work the same way in Lync Server 2013 as they do in Lync Server 2010.) 
  
> [!IMPORTANT]
> You can configure the switch for Enhanced 9-1-1 (E9-1-1), if the switch supports this. 
  

