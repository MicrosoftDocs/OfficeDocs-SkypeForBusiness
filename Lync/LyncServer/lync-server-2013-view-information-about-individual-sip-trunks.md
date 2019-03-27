---
title: 'Lync Server 2013: View information about individual SIP trunks'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: View information about individual SIP trunks
ms:assetid: adfacb74-7ea5-4c53-934e-ba7ec59879eb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721847(v=OCS.15)
ms:contentKeyID: 49733780
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# View information about individual SIP trunks in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

SIP trunks are used to connect Lync Server 2013 Voice over IP phone network with the Public Switched Telephone Network. In previous version of the product, trunks were used to route outbound calls from a Mediation Server to a PSTN gateway and each gateway was limited to a single trunk. As a result, a PSTN gateway and a SIP trunk were essentially identical. For administrators, that meant they could view information about an individual SIP trunk simply by viewing information about the associated PSTN gateway.

In Lync Server 2013, however, multiple trunks can now be assigned to a single PSTN gateway; this means that gateways and trunks are no longer one and the same. In turn, that means that administrators must use the new [Get-CsTrunk](https://docs.microsoft.com/powershell/module/skype/Get-CsTrunk) cmdlet in order to view information about an individual SIP trunk.

The Get-CsTrunk cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To view information for all your SIP trunks

  - The following command returns information about all the SIP trunks in use in your organization:
    
        Get-CsTrunk

</div>

<div>

## To view information for a specific SIP trunk

  - This command returns information only for the SIP trunk with the Identity PstnGateway:192.168.0.240:
    
        Get-CsTrunk -Identity "PstnGateway:192.168.0.240"

</div>

<div>

## Viewing Information for All the SIP Trunks Assigned to a Pool

  - In this example, information is returned for all the SIP trunks assigned to the pool atl-cs-001.litwareinc.com:
    
        Get-CsTrunk -PoolFqdn "atl-cs-001.litwareinc.com"

</div>

</div>

<span> </span>

</div>

</div>

</div>

