---
title: 'Lync Server 2013: Perimeter network VoIP components'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Perimeter network VoIP components
ms:assetid: 74230008-695d-436a-90b9-9cd060c70f7b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398559(v=OCS.15)
ms:contentKeyID: 48184514
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Perimeter network VoIP components for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-21_

Outside callers who use unified communications clients for individual or conference calls rely on Edge Server for voice communication with coworkers.

On an Edge Server, the Access Edge service provides SIP signaling for calls from Lync users who are outside your organization’s firewall. The A/V Edge service enables media traversal of NAT and firewalls. A caller who uses a unified communications (UC) client from outside the corporate firewall relies on the A/V Edge service for both individual and conference calls.

The A/V Authentication service is collocated with, and provides authentication services for, the A/V Edge service. Outside users who attempt to connect to the A/V Edge service require an authentication token that is provided by the A/V Authentication Service before their calls can go through.

</div>

<span> </span>

</div>

</div>

</div>

