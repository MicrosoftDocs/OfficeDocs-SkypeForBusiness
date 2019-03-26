---
title: 'Lync Server 2013: Defining the network elements used to determine location'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Defining the network elements used to determine location
ms:assetid: 7538779d-055d-44ed-8dd7-11c45fc1b9f5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398567(v=OCS.15)
ms:contentKeyID: 48184508
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Defining the network elements used to determine location in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-29_

If you are setting up your Lync Server infrastructure to support automatic client location detection, you first need to decide which network elements you are going to use to map callers to locations. In Lync Server 2013, you can associate the following Layer 2 and Layer 3 network elements with locations:

  - Wireless access point (WAP) Basic Service Set Identification (BSSID) addresses (Layer 2)

  - LLDP switch port (Layer 2)

  - LLDP switch chassis IDs (Layer 2)

  - IP subnets (Layer 3)

  - Client MAC addresses (Layer 2)

The network elements are listed in order of precedence. If a client can be located by using more than one network element, Lync Server uses the order of precedence to determine which mechanism to use.

The following sections provide more details for using each network element.

<div>


> [!IMPORTANT]  
> When you use network elements to map callers to locations, it is of utmost importance that you keep the Location Information service database up-to-date. For example, if you add or change a network element, such as adding a WAP, you must delete the old entry and add the new entry in the location database.



</div>

<div>

## Wireless Access Point

When a client connects to the network wirelessly, the location request uses the BSSID address of the WAP to determine its location. If the client is roaming, the WAP indicated may not be the closest one, and it’s even possible to pick up a WAP that is on a different floor of the building. To indicate that the location is approximate, you can prepend the location value with a Near or Close to descriptor.

This location method assumes that the BSSID of each WAP is static. However, if your WAP vendor uses dynamically-assigned BSSIDs, the BSSID that is obtained from a WAP could change (this can happen following a WAP configuration change), and wireless clients could be left in a situation where they don’t receive a location. To prevent this possibility, you need to populate the Location Information service database with ERLs for all possible BSSID addresses used by each WAP.

</div>

<div>

## LLDP Ports and Switches

Managed Ethernet switches that support Link Layer Discovery Protocol-Media Endpoint Discover (LLDP-MED) can advertise their identity and port information to LLDP-MED compatible clients, which then can be queried against the location database to provide the location of the device. You can associate ERLs solely on the switch chassis ID, or you can map them down to the port level.

<div>


> [!NOTE]  
> Lync Server 2013 supports using LLDP-MED for determining locations only of Lync Phone Edition devices and Lync 2013 running on Windows 8. If you need to use switch-level Layer 2 data to determine the location of other wired PC-based Lync clients, you need to use the client MAC address method.



</div>

</div>

<div>

## Subnet

Layer 3 IP subnets provide a mechanism supported by all Lync Server clients that can be used to automatically detect client location. Using IP subnets is the easiest location method to configure and manage wired clients. Before you decide to use subnets, however, use the following questions to help determine if the location specificity of the subnet is sufficiently fine to accurately locate a client:

  - Do one or more client subnets cover multiple floors?

  - Do one or more subnets cover more than one building?

  - How much floor space is covered by each client subnet?

If the subnet covers too broad an area, you may need to use another mechanism to locate clients. However, if at all practical, we recommend that customers reorganize their IP subnetting to meet the ERL location specificity requirements rather than incurring the cost and complexity of third-party SNMP-based solutions.

</div>

<div>

## Client MAC Address

To use a client computer's MAC address to locate a caller, you need managed Ethernet switches, and you must deploy a third-party SNMP solution that can discover the MAC addresses of Lync clients connected to (or through) those switches. The SNMP solution continually polls the managed switches to get the current mappings of the endpoint MAC addresses connected to each port and obtains the corresponding port IDs. During a Lync client’s request to the Location Information service, the Location Information service queries the third-party application by using the client’s MAC address, and then returns any matching switch IP addresses and port IDs. The Location Information service uses this information to query its published Layer 2 wiremap for a matching record and returns the location to the client. If you use this option, make sure that the switch port identifiers are consistent between the SNMP application and the published location database records.

<div>


> [!NOTE]  
> Some third-party SNMP solutions can support unmanaged access switches; if the switch that services the Lync client is unmanaged but has an uplink to a managed distribution switch, the managed switch can report back to the SNMP application the MAC addresses of the clients connected to the access switch. This information enables the Location Information service to identify the location of the user. However, it is possible to assign only a single ERL to all ports on the unmanaged switch, so the location specificity is available only at the chassis level of the access switch, not the port level.



</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

