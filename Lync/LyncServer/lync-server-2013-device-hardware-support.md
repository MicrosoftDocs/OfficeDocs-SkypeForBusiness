---
title: Lync Server 2013 device hardware support
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Device hardware support
ms:assetid: ba07ca91-32b4-49cf-801c-47a2d1d96e18
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412908(v=OCS.15)
ms:contentKeyID: 48185222
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Device hardware support in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-12-14_

Specific hardware configurations must be in place before you deploy IP phones and analog devices.

IP phones running Lync Phone Edition support Link Layer Discovery Protocol-Media Endpoint Discovery (LLDP-MED) and Power over Ethernet (PoE). To take advantage of LLDP-MED, the switch must support IEEE802.1AB and ANSI/TIA-1057. To take advantage of PoE, the switch must support PoE802.3AF or 802.3at.

To enable LLDP-MED, the administrator must enable LLDP by using the switch console window and set the LLDP-MED network policy with the correct voice VLAN ID.

In addition, if your deployment includes analog devices, you must configure the analog gateway to use Lync Server, and the gateway must be one of the following:

  - An analog telephone adapter (ATA)

  - A PSTN analog gateway

  - A Survivable Branch Appliance that includes a PSTN analog gateway

  - A Survivable Branch Appliance that includes a PSTN gateway that communicates with an ATA

To learn how to configure an analog gateway, see "Planning to Deploy Analog Devices" at [http://go.microsoft.com/fwlink/p/?LinkId=268537](http://go.microsoft.com/fwlink/p/?linkid=268537) in the Lync Server 2010 TechNet Library. (Analog devices work the same way in Lync Server 2013 as they do in Lync Server 2010.)

<div>


> [!IMPORTANT]  
> You can configure the switch for Enhanced 9-1-1 (E9-1-1), if the switch supports this.



</div>

</div>

<span> </span>

</div>

</div>

</div>

