---
title: 'Lync Server 2013: Planning for public instant messaging connectivity'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Planning for public instant messaging connectivity
ms:assetid: e75e8884-05c7-414a-8014-bc9aa8126fb7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205349(v=OCS.15)
ms:contentKeyID: 48185698
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Planning for public instant messaging connectivity in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-10-07_

Public Instant Messaging Connectivity is a class of federation, and is configured to allow your internal and external Lync Server 2013 users to add contacts from any of the following:

  - Messenger contacts

  - Yahoo\! contacts

  - America Online (AOL) contacts

<div>


> [!IMPORTANT]  
> <UL>
> <LI>
> <P>As of September 1st, 2012, the Microsoft Lync Public IM Connectivity User Subscription License (PIC USL) is no longer available for the purchase for new or renewing agreements. Customers with active licenses will be able to continue to federate with Yahoo! Messenger until the service shutdown date. An end of life date of June 2014 for AOL and Yahoo! has been announced. For details, see <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Support for public instant messenger connectivity in Lync Server 2013</A>.</P>
> <LI>
> <P>The PIC USL is a per-user, per-month subscription license that is required for Lync Server or Office Communications Server to federate with Yahoo! Messenger. Microsoft’s ability to provide this service has been contingent upon support from Yahoo!, the underlying agreement for which will not be renewed.</P>
> <LI>
> <P>More than ever, Lync is a powerful tool for connecting across organizations and with individuals around the world. Federation with Windows Live Messenger requires no additional user/device licenses beyond the Lync Standard CAL. Skype federation will be added to this list, enabling Lync users to reach hundreds of millions of people through IM and voice.</P></LI></UL>



</div>

This class of federation requires the following planning considerations:

  - Windows Live Messenger users can have peer-to-peer audio/visual communication with Lync Server 2013 users, in addition to instant messaging. Your Edge Servers must meet specific port and protocol requirements. For details, see [Determine external A/V firewall and port requirements for Lync Server 2013](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md).

  - Yahoo instant messaging has no unique requirements, other than those typically used in the planning and deployment of the typical Edge Server that is providing federation.

  - America Online requires that your Edge Server certificate assigned to the Access Edge service has a client enhanced key usage (EKU).

<div>

## In This Section

  - [Certificate summary - Public instant messaging connectivity in Lync Server 2013](lync-server-2013-certificate-summary-public-instant-messaging-connectivity.md)

  - [Port summary - Public instant messaging connectivity in Lync Server 2013](lync-server-2013-port-summary-public-instant-messaging-connectivity.md)

  - [DNS summary - Public instant messaging connectivity in Lync Server 2013](https://technet.microsoft.com/en-us/library/jj618375\(v=ocs.15\))

</div>

</div>

<span> </span>

</div>

</div>

</div>

