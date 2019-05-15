---
title: 'Lync Server 2013: Configure call admission control'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure call admission control
ms:assetid: ce3e6e71-1e33-4cff-849a-c0468e61fef6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398870(v=OCS.15)
ms:contentKeyID: 48185464
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure call admission control in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-21_

Call admission control (CAC) is a solution that determines whether a real-time session can be established based on the available bandwidth to help prevent poor audio/video quality for users on congested networks. CAC controls real-time traffic only for audio and video, and does not affect data traffic. CAC may route the call through an Internet path when the default WAN path does not have the required bandwidth. For details, see [Planning for call admission control in Lync Server 2013](lync-server-2013-planning-for-call-admission-control.md) in the Planning documentation.

This section provides a set of example procedures that illustrate how to deploy and manage CAC in your network.

<div>


> [!IMPORTANT]  
> Before you deploy CAC, you must gather all of the required information for your enterprise network topology, as described in <A href="lync-server-2013-example-of-gathering-your-requirements-for-call-admission-control.md">Example: Gathering your requirements for call admission control in Lync Server 2013</A> in the Planning documentation. Also be sure that CAC components have been installed and activated, as described in <A href="lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server.md">Define and configure a Front End pool or Standard Edition server in Lync Server 2013</A> in the Deployment documentation.



</div>

<div>


> [!NOTE]  
> All CAC deployment and management examples in this section are performed by using the Lync Server Management Shell. As an alternative, you can also use the <STRONG>Network Configuration</STRONG> section of Lync Server Control Panel to manage CAC.



</div>

<div>

## In This Section

  - [Configure network regions for CAC in Lync Server 2013](lync-server-2013-configure-network-regions-for-cac.md)

  - [Create bandwidth policy profiles in Lync Server 2013](lync-server-2013-create-bandwidth-policy-profiles.md)

  - [Configure network sites for CAC in Lync Server 2013](lync-server-2013-configure-network-sites-for-cac.md)

  - [Associate subnets with network sites for CAC in Lync Server 2013](lync-server-2013-associate-subnets-with-network-sites-for-cac.md)

  - [Create network region links in Lync Server 2013](lync-server-2013-create-network-region-links.md)

  - [Create network interregion routes in Lync Server 2013](lync-server-2013;-create-network-interregion-routes.md)

  - [Create network intersite policies in Lync Server 2013](lync-server-2013-create-network-intersite-policies.md)

  - [Enable call admission control in Lync Server 2013](lync-server-2013-enable-call-admission-control.md)

  - [Call admission control deployment checklist for Lync Server 2013](lync-server-2013-call-admission-control-deployment-checklist.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

