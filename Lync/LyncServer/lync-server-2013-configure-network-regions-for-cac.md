---
title: 'Lync Server 2013: Configure network regions for CAC'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure network regions for CAC
ms:assetid: ea3ff988-dd5a-4bc4-bec5-39a0fb09793a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg399051(v=OCS.15)
ms:contentKeyID: 48185906
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure network regions for CAC in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-21_

<div>


> [!IMPORTANT]  
> If you have already created network regions for E9-1-1 or media bypass, you can modify the existing network regions by adding settings specific to call admission control (CAC) by using the <STRONG>Set-CsNetworkRegion</STRONG> cmdlet. For an example of how to modify a network region, see <A href="lync-server-2013-create-or-modify-a-network-region.md">Create or modify a network region in Lync Server 2013</A>.



</div>

*Network regions* are the network hubs or backbones that are used in configuring CAC, E9-1-1, and media bypass. Use the following procedure to create network regions that align to network regions in the example network topology for CAC. To view the example network topology, see [Example: Gathering your requirements for call admission control in Lync Server 2013](lync-server-2013-example-of-gathering-your-requirements-for-call-admission-control.md) in the Planning documentation.

The example network topology for CAC has three regions: North America, EMEA, and APAC. Each region has a specified central site. For the North America region, the designated central site is named CHICAGO. The following procedure shows an example of how you can use the **New-CsNetworkRegion** cmdlet to create the North America region.

<div>


> [!NOTE]  
> In the following procedure, Lync Server Management Shell is used to create a network region. For details about using Lync Server Control Panel to create a network region, see <A href="lync-server-2013-create-or-modify-a-network-region.md">Create or modify a network region in Lync Server 2013</A>.



</div>

<div>

## To create a network region for call admission control

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  For each region that you need to create, run the **New-CsNetworkRegion** cmdlet. For example, to create the North America region, run:
    
        New-CsNetworkRegion -Identity NorthAmerica -CentralSite CHICAGO -Description "All North America Locations"

3.  Repeat step 2 to create the network regions, EMEA and APAC.

</div>

</div>

<span> </span>

</div>

</div>

</div>

