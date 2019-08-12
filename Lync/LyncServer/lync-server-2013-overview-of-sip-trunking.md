---
title: 'Lync Server 2013: Overview of SIP trunking'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Overview of SIP trunking
ms:assetid: 204f2c21-436f-4b2d-93ea-d6db98fa2952
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398285(v=OCS.15)
ms:contentKeyID: 48183601
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Overview of SIP trunking in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-05_

Deploying SIP trunking can be a big step toward simplifying your organization’s telecommunications and preparing for up-to-date enhancements to real-time communications. One of the primary advantages of SIP trunking is that you can consolidate your organization’s connections to the public switched telephone network (PSTN) at a central site, as opposed to its predecessor, time division multiplexing (TDM) trunking, which typically requires a separate trunk from each branch site.

<div>

## SIP Trunking in Lync Server

The Lync Server 2013 SIP trunking capabilities enable the following:

  - An enterprise user, whether inside or outside the corporate firewall, can make a local call or a long-distance call that is specified by an E.164-compliant number that is terminated on the PSTN as a service of the corresponding service provider.

  - Any PSTN subscriber can contact an enterprise user inside or outside the corporate firewall by dialing a Direct Inward Dialing (DID) number that is associated with that enterprise user.

</div>

<div>

## Cost Savings

The cost savings associated with SIP trunking can be substantial:

  - Long distance calls typically cost much less through a SIP trunk.

  - You can cut manageability costs and reduce the complexity of deployment.

  - Basic rate interface (BRI) and primary rate interface (PRI) fees can be eliminated if you connect a SIP trunk directly to your ITSP at significantly lower cost. In TDM trunking, service providers charge for calls by the minute. The cost of SIP trunking may be based on bandwidth usage, which you can buy in smaller, more economical increments. (The actual cost depends on the service model of the ITSP you choose.)

<div>

## SIP Trunking vs. Hosting a PSTN Gateway or IP-PBX

Because SIP trunks connect directly to your service provider, you can eliminate your PSTN gateways and their management cost and complexity. Using a SIP trunk can lead to substantial cost savings through reduced maintenance and administration.

</div>

</div>

<div>

## Expanded VoIP Services

Voice features are often the primary motivation for deploying SIP trunking, but voice support is just the first step. With SIP trunking, you can extend VoIP capabilities and enable Lync Server 2013 to deliver a richer set of services. For example:

  - Enhanced presence detection for devices that are not running Lync Server 2013 can provide better integration with mobile phones, enabling you to see when a user is on a mobile phone call.

  - E9-1-1 emergency calling enables the authorities who answer 911 calls to determine the caller’s location from his or her telephone number.

<div>


> [!NOTE]  
> Contact your ITSP for a list of services that they support and can enable for your organization.



</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

